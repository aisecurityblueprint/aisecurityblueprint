# AI Security Blueprint v2.0

**Observable · Controlled · Contained**

A practical operational security framework for production AI systems that reason, act, and remember.

---

## Overview

Modern AI systems are no longer passive software components. They retrieve. They reason. They remember. They delegate. They execute. They interact.

This blueprint presents a comprehensive operational security architecture for securing AI systems across 12 control domains, with practical detection code, mandatory calibration protocols, and honest assessment of what is validated vs. placeholder.

**This is not a prompt engineering guide. This is control architecture for systems that think, act, and remember.**

---

## What's Inside

- **Domain 01: Input & Interface Control** (Complete)
  - 8 attack vectors documented with functional detection code
  - Context stuffing, function injection, RAG poisoning, tool response injection, and more
  - Deterministic risk evaluation rules (NIST/OWASP aligned)
  - Mandatory calibration protocol (Section 4.7.3)

- **12-Domain Architecture** (Planned)
  - 01 Input & Interface Control ✅
  - 02 Context & RAG Control (Planning)
  - 03 Reasoning Control (Planning)
  - ...and 9 more domains

- **Operational Validation**
  - Tested against 330+ adversarial payloads
  - Production calibration results from live AI systems
  - Real incident examples and remediation
  - Cross-model validation (Mixtral, Mistral, Qwen)

- **Governance & Maturity**
  - 5-level maturity model
  - Deterministic rules (not probabilistic scoring)
  - OWASP/NIST/MITRE alignment
  - Forensic audit trail (hash chain architecture)

---

## Key Principles

1. **"The model suggests. The architecture decides."**
   - Security lives at decision time, not in prompts
   - Controls operate across input, context, reasoning, execution layers

2. **Honest Validation Status**
   - Detection thresholds are calibrated placeholders requiring local adaptation
   - Openly documents what is validated vs. unvalidated
   - Provides mandatory calibration protocol, not universal guarantees

3. **Operational Not Theoretical**
   - Developed and validated in production AI systems
   - Tested against dark web monitoring feeds, threat intelligence, and OSINT
   - Real-world incident examples included

4. **Observable · Controlled · Contained**
   - Every decision logged with audit trail
   - Runtime governance with enforcement points
   - Failure containment and recovery procedures

---

## Quick Start

### For Security Architects
- Read: **[AI_Security_Assessment_Blueprint_v2.0.md](./docs/AI_Security_Assessment_Blueprint_v2.0.md)**
- Focus sections: 1.0 (Foundation), 4.2 (Reference Architecture), 4.5-4.6 (Risk & Rules)

### For Security Engineers
- Read: **Section 2 (Attack Vectors)** + **Section 3 (Controls)**
- Run: **[quick_start_validation.py](./code/quick_start_validation.py)** against your endpoint
- Implement: **Section 4.7.3 (Calibration Protocol)**

### For Red Teams
- Read: **Section 4.3 (Test Framework)**
- Use: **330+ adversarial payloads** from calibration dataset
- Validate: **Section 4.7.3 (Adversarial Validation)**

### For Organizations Planning AI Security
- Read: **Section 4.1 (Maturity Model)** → measure current state
- Read: **Section 4.5 (Risk Framework)** → map to your threats
- Plan: **6-week calibration protocol** (Section 4.7.3)

---

## Operational Validation

This framework has been operationally tested in production:

- **Time in Production:** 30+ days
- **Test Payloads:** 330+ adversarial variants
- **Models Tested:** Mixtral 8x22B, Mistral 7B, Qwen 3B, Qwen 1.5B
- **Real Threats:** Dark web monitoring, OSINT, threat intelligence feeds
- **Detection Rates:** 87-99.8% by vector (see case study)
- **False Positive Rates:** 0-2% (calibrated for production)

**See:** [Case Study: Operational Validation](./docs/case-study-operational-validation.md)

---

## Repository Structure