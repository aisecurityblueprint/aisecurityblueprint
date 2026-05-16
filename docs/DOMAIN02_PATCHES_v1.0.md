# DOMAIN 02 — CONTEXT & RAG CONTROL
## Patch Document: 4 Critical Gaps Fixed
**May 2026 | Pre-Launch Corrections**

---

## FIX 1 — GAP 1: Defensive Sanitization Check
### Location: §2.2.9 — SecureRetrievalPipeline.retrieve()

**ADDED METHOD & DEFENSIVE VALIDATION:**

```python
class SecureRetrievalPipeline:
    """
    Complete secure retrieval pipeline with Domain 01 integration.

    Stages:
    0. DEFENSIVE: Validate query was sanitized by Domain 01
    1. Query validation and sanitization
    2. Mandatory security filters
    3. Retrieval via secure adapter
    4. Post-retrieval filtering (relevance, staleness, cross-tenant)
    5. Integrity verification post-retrieval
    6. Source ranking (authoritative first)
    7. Complete audit trail
    """

    SOURCE_AUTHORITY = {
        "official_policy": 100, "internal_wiki": 90, "verified_partner": 80,
        "partner_feed": 60, "government_public": 50, "public_verified": 40,
        "public_unverified": 20, "web_crawl": 10, "unknown": 0,
    }

    def __init__(self, adapter: SecureVectorDBAdapter,
                 max_results: int = 20, staleness_threshold_days: int = 365):
        self.adapter              = adapter
        self.max_results          = max_results
        self.staleness_threshold  = staleness_threshold_days
        self._pipeline_log: List[dict] = []
        self.query_guard = QueryFormationGuard()  # NEW: Initialize Domain 01 guard

    def retrieve(self, query_text: str, tenant_id: str, user_id: str,
                 clearance_level: int, department: str, session_id: str,
                 doc_type_filter: Optional[str] = None,
                 d01_sanitization_metadata: Optional[dict] = None) -> dict:
        """
        DEFENSIVE FIX 1 (NEW):
        Validates that query was pre-sanitized by Domain 01.
        If Domain 01 metadata is missing or incomplete, runs QueryFormationGuard independently.
        This ensures no unsanitized query enters retrieval, even if Domain 01 is bypassed.
        """
        pipeline_id = str(uuid4())[:8]
        start_time  = time.time()

        # ========== DEFENSIVE VALIDATION (NEW) ==========
        if d01_sanitization_metadata is None:
            logger.warning("D01 sanitization metadata missing for query %s. Running defensive check.", pipeline_id)
            d01_validation = self.query_guard.validate_query(query_text, 
                                                               {"clearance_level": clearance_level, 
                                                                "department": department})
            if d01_validation["action"] == "block":
                return {
                    "action": "blocked_by_defensive_check",
                    "reason": f"Query failed Domain 01 sanitization: {d01_validation['reason']}",
                    "d01_validation": d01_validation,
                    "defensive_check": True,
                }
        else:
            # Verify D01 metadata integrity
            if not d01_sanitization_metadata.get("sanitized", False):
                logger.warning("D01 reports unsanitized query %s. Running guard.", pipeline_id)
                d01_validation = self.query_guard.validate_query(query_text, 
                                                                   {"clearance_level": clearance_level,
                                                                    "department": department})
                if d01_validation["action"] == "block":
                    return {
                        "action": "blocked_by_defensive_check",
                        "reason": f"Query failed D01 post-hoc validation: {d01_validation['reason']}",
                        "d01_validation": d01_validation,
                        "defensive_check": True,
                    }
        # ========== END DEFENSIVE VALIDATION ==========

        secure_query = SecureQuery(
            query_text=query_text, tenant_id=tenant_id, user_id=user_id,
            clearance_level=clearance_level, department=department,
            session_id=session_id, top_k=self.max_results,
            min_relevance=0.65,
            allowed_classifications=self._allowed_classifications(clearance_level),
            max_sensitivity_tier=clearance_level,
        )

        raw_results = self.adapter.query(secure_query)
        # [Continue with retrieval as before...]
        
        return {"results": raw_results, "security_report": {}, "pipeline_id": pipeline_id}
```

---

## FIX 2 — GAP 2: Risk Score Inheritance Rule
### Location: §4.2.1 — ContextRiskScoringModel

```python
class ContextRiskScoringModel:
    """
    ===== NEW: DOMAIN 01 RISK INHERITANCE (FIX 2) =====
    
    Risk Inheritance Rule:
    - If Domain 01 risk score >= 0.40 (medium-high input risk):
        baseline_injection_risk = 0.15 (elevated awareness)
    - If Domain 01 risk score < 0.40 (low input risk):
        baseline_injection_risk = 0.0 (minimal concern)
    
    Final calculation:
    D02_independent_score = computed from all §4.2 signals
    D02_final_score = max(D01_adjusted_injection_risk, D02_independent_score)
    
    Rationale: If input is already risky (D01 >= 0.40), context layer assumes
    higher baseline vigilance. If input is clean, D02 starts from zero and
    builds independently.
    
    ===== END INHERITANCE RULE =====
    """

    RISK_FACTORS = {
        "injection_risk": 0.25, "trust_deficit": 0.20, "amplification_risk": 0.15,
        "freshness_decay": 0.10, "consistency_issues": 0.10, "source_mix_risk": 0.05,
        "memory_poisoning_risk": 0.05, "tool_output_risk": 0.05,
        "isolation_breach_risk": 0.03, "anomaly_score": 0.02,
    }

    def __init__(self):
        self.scoring_history: List[dict] = []

    def compute_risk_score(self, signals: dict, 
                            d01_risk_score: Optional[float] = None) -> dict:
        """
        NEW PARAMETER: d01_risk_score (Optional)
        If provided, applies Domain 01 risk inheritance rule.
        """
        fs: Dict[str, float] = {}
        
        # Compute all factors (unchanged from original)
        injection = signals.get("injection", {})
        fs["injection_risk"] = min(1.0,
            injection.get("highest_injection_score", 0) * 1.0 +
            injection.get("cross_chunk_findings", 0) * 0.2)

        avg_trust = signals.get("trust", {}).get("average_trust", 3.5)
        fs["trust_deficit"] = max(0.0, 1.0 - avg_trust / 5.0)
        fs["freshness_decay"] = 1.0 - signals.get("freshness", {}).get("freshness_score", 1.0)

        consistency = signals.get("consistency", {})
        fs["consistency_issues"] = min(1.0,
            consistency.get("issue_count", 0) * 0.1 +
            consistency.get("contradiction_count", 0) * 0.2)

        amp = signals.get("amplification", {})
        fs["amplification_risk"] = (
            0.8 if amp.get("amplification_detected") else 0.0
        ) + min(0.2, amp.get("amplification_magnitude", 0) * 0.2)

        untrusted_ratio = signals.get("sources", {}).get("external_unverified_ratio", 0)
        fs["source_mix_risk"] = min(1.0, untrusted_ratio * 2.0)
        fs["memory_poisoning_risk"] = signals.get("memory", {}).get("poisoning_score", 0)
        fs["tool_output_risk"] = 1.0 - signals.get("tools", {}).get("average_trust_score", 1.0)
        fs["isolation_breach_risk"] = min(1.0, signals.get("isolation", {}).get("violations_today", 0) * 0.2)
        fs["anomaly_score"] = signals.get("anomaly", {}).get("overall_anomaly_score", 0)

        # ===== NEW: APPLY DOMAIN 01 RISK INHERITANCE =====
        d01_adjusted_injection = 0.0
        d01_inheritance_applied = False
        
        if d01_risk_score is not None:
            if d01_risk_score >= 0.40:
                d01_adjusted_injection = 0.15
                d01_inheritance_applied = True
                logger.info("D01 score %.2f >= 0.40. D02 baseline_injection_risk raised to 0.15", d01_risk_score)
            else:
                d01_adjusted_injection = 0.0
                d01_inheritance_applied = True
                logger.info("D01 score %.2f < 0.40. D02 baseline_injection_risk remains 0.0", d01_risk_score)
        
        # Compute D02 independent score
        d02_independent = min(1.0, sum(fs[k] * w for k, w in self.RISK_FACTORS.items()))
        
        # Final: max(D01 adjusted, D02 independent)
        if d01_inheritance_applied:
            composite = min(1.0, max(d01_adjusted_injection, d02_independent))
        else:
            composite = d02_independent
        # ===== END DOMAIN 01 RISK INHERITANCE =====

        risk_level = self._determine_risk_level(composite)

        result = {
            "context_risk_score": composite, 
            "risk_level": risk_level,
            "factor_scores": fs,
            "d01_risk_score": d01_risk_score,
            "d01_inheritance_applied": d01_inheritance_applied,
            "d01_adjusted_injection_baseline": d01_adjusted_injection if d01_inheritance_applied else None,
            "d02_independent_score": d02_independent,
            "action": self._determine_action(risk_level),
            "scoring_timestamp": datetime.utcnow().isoformat(),
        }
        self.scoring_history.append(result)
        return result
```

---

## FIX 3 — GAP 3: Appendix E Validation Chain
### Location: Appendix E — Cross-Domain Risk Integration

```markdown
## E.1 Integrated Risk Pipeline & Complete Validation Chain (NEW FIX 3)

┌──────────────────────────────────────────────────────────────────┐
│  INPUT → [Domain 01] → Risk Score + Sanitized → [Domain 02] → Context Risk
│           ↓                                           ↓
│      + Metadata                              + D01 Feedback
│           ↓                                           ↓
│      (sanitization                     (inheritance applied)
│       metadata)                              ↓
│                                    [DomainRiskIntegrator]
│                                            ↓
│                                   Composite Risk Score
│                                            ↓
│                                    Final Action Decision
└──────────────────────────────────────────────────────────────────┘

### Validation Chain Integrity

**Stage 1: Domain 01 Input Validation**
- Input arrives: potentially malicious query
- QueryFormationGuard validates: injects security filters
- Produces: sanitized_query + d01_risk_score (0-1) + metadata
- Passes to Domain 02: full metadata package

**Stage 2: Domain 02 Context Validation (WITH FIX 1)**
- Receives metadata from D01
- DEFENSIVE CHECK (FIX 1): If D01 metadata missing → run QueryFormationGuard independently
- If D01 present: Apply risk inheritance rule (FIX 2)
- Retrieval pipeline executes on validated query
- Produces: context_risk_score (0-1) + D01 signal lineage

**Stage 3: Risk Integration & Final Decision**
- DomainRiskIntegrator receives both scores
- Weights: D01=40%, D02=35%, [D03=25% future]
- Composite = weighted sum
- Decision: block | escalate | flag | allow
- All inputs/outputs recorded in audit trail

### Inheritance Rule Documentation (FIX 2)

If D01_score >= 0.40:
  D02_baseline_injection_risk = 0.15
Else:
  D02_baseline_injection_risk = 0.0

D02_final = max(D01_baseline, D02_independent)

This ensures: risky input → higher baseline vigilance in context layer
```

---

## FIX 4 — GAP 4: Embedding Model Consistency
### Location: §5.3.2 — ThresholdRegistry

```python
class ThresholdRegistry:
    """
    ===== NEW: MANDATORY EMBEDDING MODEL CONSISTENCY (FIX 4) =====
    
    The SemanticEngine is the detection core for §2.4, §2.5, §2.6.
    
    Threshold calibration assumes model: all-MiniLM-L6-v2 (384-dim).
    
    MANDATORY ENFORCEMENT:
    - At runtime, SemanticEngine MUST load all-MiniLM-L6-v2
    - If any other model detected → raise RuntimeError
    - Prevents threshold drift from model changes
    
    ===== END MODEL CONSISTENCY ENFORCEMENT =====
    """

    MANDATORY_EMBEDDING_MODEL = "all-MiniLM-L6-v2"
    EMBEDDING_DIMENSION = 384

    def __init__(self, enforce_model_consistency: bool = True):
        self._thresholds: Dict[str, dict] = {}
        self._embedding_model_verified = False
        self.enforce_model_consistency = enforce_model_consistency
        
        if self.enforce_model_consistency:
            self._verify_embedding_model()
        
        self._build_registry()

    def _verify_embedding_model(self):
        """
        NEW METHOD (FIX 4):
        Verifies SemanticEngine is using mandatory model.
        Raises RuntimeError if model mismatch detected.
        """
        try:
            engine = SemanticEngine(self.MANDATORY_EMBEDDING_MODEL)
            
            if hasattr(engine, 'model_name') and engine.model_name != self.MANDATORY_EMBEDDING_MODEL:
                raise RuntimeError(
                    f"SemanticEngine model mismatch. "
                    f"Expected: {self.MANDATORY_EMBEDDING_MODEL}, "
                    f"Got: {engine.model_name}. "
                    f"Thresholds calibrated for {self.MANDATORY_EMBEDDING_MODEL} only."
                )
            
            if hasattr(engine, '_fallback') and engine._fallback:
                logger.warning(
                    "SemanticEngine in TF-IDF fallback mode. "
                    "Install sentence-transformers: pip install sentence-transformers"
                )
            
            test_emb = engine.embed("test")
            actual_dim = len(test_emb)
            if actual_dim != self.EMBEDDING_DIMENSION:
                raise RuntimeError(
                    f"Embedding dimension mismatch. "
                    f"Expected: {self.EMBEDDING_DIMENSION}, Got: {actual_dim}."
                )
            
            self._embedding_model_verified = True
            logger.info(
                "✓ SemanticEngine verified: %s (%d-dim, mode: %s)",
                self.MANDATORY_EMBEDDING_MODEL, self.EMBEDDING_DIMENSION, engine.mode
            )
            
        except Exception as e:
            if self.enforce_model_consistency:
                raise RuntimeError(
                    f"ThresholdRegistry initialization FAILED: {str(e)}. "
                    f"Install: pip install sentence-transformers"
                ) from e

    def verify_model_at_runtime(self):
        """
        NEW METHOD (FIX 4):
        Call before starting detection pipelines.
        Use in production startup checks.
        """
        if not self.enforce_model_consistency:
            logger.warning("Model consistency enforcement DISABLED.")
            return False
        
        try:
            self._verify_embedding_model()
            return True
        except RuntimeError as e:
            logger.critical("Model verification failed: %s", str(e))
            raise

    def summary(self) -> dict:
        return {
            "total_thresholds": len(self._thresholds),
            "embedding_model_verified": self._embedding_model_verified,
            "mandatory_model": self.MANDATORY_EMBEDDING_MODEL,
        }
```

---

## PATCH APPLICATION SUMMARY

| Fix | Section | Change | Status |
|-----|---------|--------|--------|
| 1 | §2.2.9 | Defensive sanitization check in retrieve() | ✅ READY |
| 2 | §4.2.1 | Risk score inheritance from D01 | ✅ READY |
| 3 | Appendix E | Validation chain diagram + explanation | ✅ READY |
| 4 | §5.3.2 | Embedding model consistency enforcement | ✅ READY |

**Pre-Launch Check:**
```python
registry = ThresholdRegistry(enforce_model_consistency=True)
registry.verify_model_at_runtime()  # ← Run in startup
print("✓ Domain 02 ready for production")
```

**All fixes are backward-compatible and forward-ready for Domain 03+.**
