# AI Security Assessment Blueprint v2.0

**Observable · Controlled · Contained**

---

## Executive Summary

### Opening Statement

**EXECUTIVE · ARCHITECTURE · SECURITY**

## AI Security Assessment Blueprint

### The 12 Control Domains Every Production AI System Needs

Modern AI systems are no longer passive software components.

They retrieve. They reason. They remember.
They delegate. They execute. They interact.

They connect to external systems, call tools, assume identities, and operate inside production environments where failure has real consequences.

This blueprint presents a practical operational security architecture for securing modern AI systems.

| Control Layer | Purpose |
| --- | --- |
| Governance | Who decides, who approves, who audits |
| Runtime Control | What executes, when, and under what constraints |
| Observability | What happened, why, and who is responsible |
| Containment | How failure is bounded and recovered |
| Decision Enforcement | Where the model suggests, the architecture decides |

This is not a prompt engineering guide.
This is not a list of jailbreaks.

**This is a control architecture for systems that think, act, and remember.**

**OBSERVABLE. CONTROLLED. CONTAINED.**

---

## The AI Security Shift

**ARCHITECTURE · GOVERNANCE · EXECUTIVE · SECURITY**

AI systems are evolving from isolated models into operational architectures.

Modern enterprise AI environments now include capabilities that traditional security models never anticipated:

| Capability | Security Implication |
| --- | --- |
| Retrieval-Augmented Generation | Untrusted external content enters the reasoning pipeline |
| Agentic Workflows | Models delegate tasks and invoke tools autonomously |
| Long-Term Memory | State persists across sessions, creating deferred attack surfaces |
| Autonomous Orchestration | Multi-step decision chains execute without human review |
| Tool & API Integration | Models interact with production systems, databases, and external services |
| Cross-System Interaction | AI systems connect to identity, payment, and infrastructure layers |

Traditional application security models were designed for systems that execute deterministic logic, follow static execution paths, and operate within known trust boundaries.

**Modern AI systems violate all of these assumptions.**

They reason dynamically, consume untrusted context, delegate actions, and continuously evolve during runtime.

Their attack surface is not static — it mutates with every retrieval, every tool call, every memory write.

The new requirement is not simply model protection.

**The new requirement is operational control.**

---

## The Paradigm Shift

**ARCHITECTURE · GOVERNANCE · SECURITY · EXECUTIVE**

### AI Security Is Not About Protecting The Model

The industry has spent years focused on model safety — making models refuse harmful requests, avoid toxic outputs, and stay within guardrails.

This is necessary. It is not sufficient.

| Common Misconception | Reality |
| --- | --- |
| A prompt filter | Prompt filters catch direct attacks. They miss indirect injection, RAG poisoning, and memory manipulation. |
| A moderation layer | Moderation catches toxic outputs. It does not govern tool execution, agent delegation, or runtime drift. |
| A compliance checklist | Checklists document intent. They do not enforce decisions at runtime. |
| Solved by guardrails alone | Guardrails are perimeter controls. They do not govern what happens inside the reasoning boundary. |

Modern AI systems must be treated as operational environments capable of:

**Reasoning → Retrieving → Delegating**
**Executing → Remembering → Influencing**

Each of these verbs represents a control surface. Each requires governance, validation, and containment.

*The challenge is no longer model safety.*
**The challenge is architectural control.**

Security must move from the prompt to the platform. From the request to the runtime. From the training data to the decision boundary.

---

## From Models To Systems

**ARCHITECTURE · ENGINEERING · PLATFORM · SECURITY**

### The Evolution Of AI Architectures

| Era | Architecture | Security Model |
| --- | --- | --- |
| 2022–2023 | Isolated chat interfaces | Content filtering, prompt blocking |
| 2023–2024 | RAG-enabled assistants | Input validation, retrieval filtering |
| 2024–2025 | Agentic systems with tools | Tool governance, execution control |
| 2025–2026 | Multi-agent orchestration | Cross-agent trust, delegation boundaries |
| 2026+ | Autonomous operational systems | Runtime governance, containment, observability |

Early AI systems behaved as isolated interfaces — a user typed, the model responded, the interaction ended.

Modern AI systems operate as:

| Architectural Role | Description |
| --- | --- |
| Runtime Environments | Persistent execution contexts with state, memory, and tool access |
| Orchestration Layers | Multi-step workflows spanning retrieval, reasoning, and execution |
| Decision Systems | Models that choose what to do, not just what to say |
| Agentic Architectures | Autonomous agents that delegate, plan, and execute without human intervention |
| Operational Automation | AI embedded in business processes, infrastructure, and customer-facing systems |

**Prompts → Retrieval Pipelines → Memory Systems**
**Agents → External APIs → Execution Layers**
**Runtime → Tool Permissions → Autonomous Workflows**

*AI security is no longer an input validation problem.*
**It is a systems security problem.**

---

## Why Traditional Security Models Fail

**SECURITY · ARCHITECTURE · RED TEAM · GOVERNANCE**

### The Assumption Gap

| Assumption | Why It Fails for AI |
| --- | --- |
| Deterministic behavior | AI systems produce different outputs for the same input. Their behavior is probabilistic, not predictable. |
| Static logic | AI reasoning adapts to context. The same system may behave safely with one context and dangerously with another. |
| Known execution paths | Agentic AI generates execution paths dynamically. You cannot pre-approve what you cannot anticipate. |
| Explicit control flows | Tool calls, memory writes, and agent delegation create control flows that emerge at runtime, not at design time. |
| Static trust boundaries | RAG pipelines inject external content into the reasoning core. Trust boundaries blur with every retrieval. |

### New Operational Risks

**Prompt Injection** — Instructions hidden in user input
**Indirect Injection** — Instructions hidden in RAG documents
**RAG Poisoning** — Malicious content embedded at ingestion time
**Memory Poisoning** — Contaminated state persists across sessions
**Execution Hijacking** — Tool calls redirected to malicious endpoints
**Tool Abuse** — Excessive or unauthorized tool invocation
**Agentic Escalation** — Delegation chains that bypass approval boundaries
**Runtime Drift** — Gradual behavioral change invisible to static checks

Static controls alone are insufficient.

Security for AI must be continuous, contextual, and operational.

---

## The Operational Security Model

**ARCHITECTURE · GOVERNANCE · SECURITY · ENGINEERING**

Security for modern AI systems cannot live in a single layer.

It must span every layer where decisions happen.

### The Control Stack

**Layer 1 — Input Governance**
What enters the system? Is it authorized? Is it safe?

**Layer 2 — Context Governance**
What becomes truth for the model? Is it verified?

**Layer 3 — Reasoning Governance**
How does the model think? Is it constrained?

**Layer 4 — Decision Governance**
What is the model allowed to decide?

**Layer 5 — Execution Governance**
What actions can the model take?

**Layer 6 — Memory & State Governance**
What persists? What influences future behavior?

**Layer 7 — Output Governance**
What reaches the user?

**Layer 8 — Tool & Agent Governance**
What tools can agents use?

**Layer 9 — Infrastructure & Supply Chain**
Where does the model run?

**Layer 10 — Observability & Validation**
Can we see what happened? Can we prove it?

**Layer 11 — Resilience & Failure**
When things fail, how do we contain and recover?

**Layer 12 — Governance & Compliance**
Who is accountable?

*Security is no longer a gate. It is a control plane.*

---

## The Framework Architecture

**ARCHITECTURE · GOVERNANCE · EXECUTIVE**

### Public Framework — 12 Domains

| # | Domain | Control Focus |
| --- | --- | --- |
| 01 | Input & Interface Control | What enters the system |
| 02 | Context & RAG Control | What becomes truth |
| 03 | Reasoning Control | How the model thinks |
| 04 | Decision Layer Control | What the model can decide |
| 05 | Execution Control | What actions execute |
| 06 | Memory Control | What persists and influences |
| 07 | Output Control | What reaches the user |
| 08 | Agent & Tooling Control | What agents can do |
| 09 | Infrastructure, Runtime & Supply Chain | Where it runs, what it depends on |
| 10 | Monitoring, Observability & Testing | Visibility and validation |
| 11 | Resilience & Failure Control | Containment and recovery |
| 12 | Governance, Compliance & User Safety | Accountability and trust |

### Internal Framework — 15 Domains

The Internal Framework extends the Public Framework with three additional domains:

| # | Domain | Control Focus |
| --- | --- | --- |
| 13 | Runtime Governance & Policy Enforcement | Real-time policy evaluation at decision time |
| 14 | AI Trust, Identity & Authorization Architecture | Identity, trust boundaries, and access control |
| 15 | Autonomous Orchestration, Containment & Recovery | Safe delegation, blast radius control, and automated recovery |

*The Public Framework is for the market.*
*The Internal Framework is for operations.*

---

## How To Use This Blueprint

**GOVERNANCE · SECURITY · EXECUTIVE · ENGINEERING**

### Intended Audience

| Role | Primary Domains | Key Concern |
| --- | --- | --- |
| AI Security Architects | All domains | Architecture, design, control implementation |
| Security Engineers | 01–08 | Detection, enforcement, integration |
| CISOs / Security Leadership | 09–12 | Governance, risk, compliance |
| Red Teams | 01–08 | Attack surface mapping, adversarial testing |
| Governance & Risk Teams | 10–12 | Observability, compliance, maturity |
| Platform Engineers | 05, 06, 09 | Runtime, infrastructure, supply chain |
| AI Product Teams | 01–04, 07 | Input, context, reasoning, output |
| Enterprise Security Programs | All domains | Program development, maturity assessment |

### Usage Models

| Use Case | Approach |
| --- | --- |
| AI Security Assessment | Evaluate each domain against current controls |
| Architecture Review | Validate against reference patterns |
| Red Teaming | Map attack vectors from each domain |
| Governance Evaluation | Assess observability, resilience, and compliance posture |
| Secure AI Deployment | Follow the domain checklist before production |
| Enterprise AI Risk Reduction | Identify gaps and build remediation roadmap |
| Operational Maturity Program | Track maturity evolution over time |

---

## Security Philosophy

**GOVERNANCE · ARCHITECTURE · SECURITY**

### Security Must Exist At Decision Time

Security cannot depend solely on developers, prompts, user behavior, or static policy documents.

### Where Security Must Live

**During Retrieval** — Validate sources before they become context
**During Reasoning** — Constrain how the model thinks
**During Orchestration** — Control what the model decides to do
**During Execution** — Govern every action before it takes effect
**During Runtime** — Monitor, detect, contain, and recover

### The Core Principle

*The model suggests. The architecture decides.*

The model may recommend an action, generate a response, or propose a plan.

But the architecture — not the model — determines whether that action is:

**Authorized** — Does the model have permission?
**Validated** — Has the context been verified?
**Approved** — Has a human signed off when required?
**Constrained** — Is the action within operational bounds?
**Observable** — Is the decision logged and auditable?
**Containable** — If it fails, can we recover?

*Security that lives only in prompts is security that disappears at runtime.*

---

## Threat Landscape Overview

**SECURITY · RED TEAM · THREAT MODELING · RAG**

### Modern AI Threat Categories

| Threat | Mechanism | Impact |
| --- | --- | --- |
| Direct Prompt Injection | Malicious instructions in user input | Model ignores system policies |
| Indirect Prompt Injection | Malicious instructions in retrieved documents | Model follows attacker directives |
| RAG Poisoning | Contaminated documents at ingestion time | Persistent influence across all queries |
| Context Manipulation | Semantic steering, dilution, attention hijacking | Model reasoning is redirected |
| Memory Poisoning | Malicious content stored in memory | Future interactions are compromised |
| Execution Hijacking | Tool calls redirected to malicious endpoints | Unauthorized system access |
| Tool Abuse | Excessive or unauthorized tool invocation | Data exfiltration or system damage |
| Agentic Escalation | Delegation chains bypass approval boundaries | Actions taken without authorization |

### The Shift in Targeting

| Old Target | New Target |
| --- | --- |
| The prompt | The retrieval pipeline |
| The output | The decision boundary |
| The model weights | The memory state |
| The API key | The trust boundary |
| The training data | The runtime environment |

*Attackers do not need to break the model. They need to manipulate what the model believes, remembers, and is authorized to do.*

---

## Runtime Observability

**OBSERVABILITY · SECURITY · ENGINEERING · OPERATIONS**

### Observability Is Not Optional

AI systems are not static. They mutate continuously.

| What Changes | Why It Matters |
| --- | --- |
| Model behavior evolves | The same system may behave differently tomorrow than today |
| Context changes | Every retrieval brings new information into the reasoning core |
| Tool outputs change | External APIs return different data, formats, and errors |
| Runtime state changes | Memory accumulates, sessions persist, configurations shift |
| Threats evolve | Attackers adapt. Detection must adapt faster. |

### What Must Be Observable

Every retrieval.
Every context assembly.
Every reasoning trace.
Every decision.
Every tool call.
Every memory write.
Every output.
Every anomaly.

*Observability is the foundation of governance. Without it, you are operating blind. With it, you can detect, contain, prove, and improve.*

---

## Containment & Control

**RESILIENCE · GOVERNANCE · SECURITY · OPERATIONS**

### Failure Will Happen

The objective of AI security is not to assume perfect prevention.

The objective is to design systems that:

| Capability | Description |
| --- | --- |
| Detect | Identify failures, attacks, and anomalies in real time |
| Contain | Limit the blast radius when something goes wrong |
| Govern | Maintain control over what actions can be taken |
| Recover | Return to a known safe state after an incident |
| Learn | Improve controls based on what was detected |

### The Containment Principle

| Layer | Containment Strategy |
| --- | --- |
| Input | Block malicious content before it enters context |
| Context | Validate, verify, anchor to authoritative sources |
| Reasoning | Constrain within policy boundaries |
| Decision | Require approval for high-impact actions |
| Execution | Execute in sandbox, validate pre/post conditions |
| Memory | Enforce TTL, scope isolation, write validation |
| Output | Inherit sensitivity, enforce policy, filter |
| Infrastructure | Kill switches, circuit breakers, emergency intervention |

*The question is not whether failures occur.*
**The question is whether the architecture is capable of containing them.**

---

## DOMAIN 01: INPUT & INTERFACE CONTROL

### Introduction to Input & Interface Control

Input & Interface Control is the first of the twelve domains of the AI Security Assessment Blueprint. It addresses all attack surfaces involving data entry into the AI system, including:

- Direct user prompts
- Documents ingested via RAG
- API parameters
- Function calls (tool calling)
- Tool responses returning to the model
- Uploaded files (PDFs, DOCX, images)
- Historical context (previous conversations)
- Memory (session and persistent)

**Fundamental Principle:** All input is untrusted until validated. This applies not only to what the user types, but also to what the model receives from indirect sources (RAG, tools, memory).

### Detailed Scope

| Surface | Description | Attack Example |
| --- | --- | --- |
| Direct Prompt | Text submitted by user | Direct injection, jailbreak |
| API Parameters | logit_bias, temperature, top_p | Probability manipulation |
| RAG Documents | Content retrieved from knowledge base | Knowledge poisoning |
| Tool Calls | Parameters generated by model | Structured parameter injection |
| Tool Responses | Data returned from tools | Indirect injection via response |
| File Uploads | PDFs, DOCX, images | Hidden text, malicious metadata |
| Historical Context | Previous conversations | Multi-turn attacks |
| Memory | Session/persistent stored context | Deferred injection, contamination |

**Control Principle:** If it can influence the model, it must pass through control.

---

## SECTION 1: Scope and Attack Surfaces

### Direct Input

Direct input enters through known interfaces:

- Chat prompts
- API requests
- Form fields
- Uploaded documents
- Search queries
- Command-like instructions
- Structured JSON payloads

These are the more observable inputs. They are comparatively easier to monitor because they enter through known interfaces.

### Indirect Input

Indirect input introduces greater operational risk because it enters the model through supporting systems:

- RAG-retrieved chunks
- Search results
- Tool responses (HTTP, database, SaaS, internal APIs)
- Memory retrieval (session or persistent stores)
- Agent-to-agent messages
- Workflow outputs
- Vector database retrieval results

These inputs may appear trusted because they originate from within the system. **Internally sourced does not mean safe.**

### Key Risk

An attacker does not always need to target the model directly. Attacking what the model reads is a viable and documented attack path.

### Architectural Requirement

Input & Interface Control must apply to:

- User-originated input
- System-originated input
- Retrieved input
- Tool-originated input
- Memory-originated input
- Agent-originated input

If it can influence the model, it must pass through control.

---

## SECTION 2: Threat Model (STRIDE Adapted for AI)

The traditional STRIDE model (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) is adapted for AI systems as STRIDE-AI.

| Threat | Description | Example in This Domain |
| --- | --- | --- |
| Spoofing | False identity attribution | User impersonates admin via prompt |
| Tampering | Unauthorised modification | Document poisoning before ingestion |
| Repudiation | Action denial | Logs without hash chain (non-forensic) |
| Information Disclosure | Data leakage | Model generates sensitive data via prompt |
| Denial of Service | Unavailability | Context window stuffing (token consumption) |
| Elevation of Privilege | Privilege escalation | Tool function with escalation parameters |

---

## SECTION 3: Risk Matrix for Input & Interface Control

| Vector | Spoof | Tamper | Repud | InfoDisc | DoS | EoP | Total Risk |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Context Stuffing | Low | Medium | Low | Low | High | Medium | High |
| Function Injection | Low | High | Medium | High | Low | High | Critical |
| Logit Bias | Medium | High | Low | High | Low | Medium | High |
| RAG Poisoning | Medium | High | Medium | High | Low | High | Critical |
| Tool Response Injection | Low | High | Medium | High | Low | High | Critical |
| Cross-Chunk | Low | High | Low | High | Low | Medium | High |
| Retrieval Amplification | Low | High | Low | High | Low | High | Critical |
| Log Tampering | Low | High | High | Medium | Low | Low | High |
| RBAC/ABAC | High | Medium | Medium | High | Low | High | Critical |

---

# SECTION 4: GOVERNANCE & MATURITY

## 4.1 Maturity Model (Levels 1 to 5)

**Level 1 — Initial (Reactive):** No token limits, no parameter validation, mutable logs.

**Level 2 — Managed (Repeatable):** Fixed token limit, basic type validation, hash chain implemented.

**Level 3 — Defined (Standardised):** Signal density controls, pattern validation (SQL/SSRF), full ABAC.

**Level 4 — Quantitatively Managed:** ML-assisted detection, threat intelligence integration, Merkle root snapshots.

**Level 5 — Optimised (Continuous):** Continuous learning, automated adversarial fuzzing, real-time integrity verification.

---

## 4.2 Validation & Calibration Protocol

### Honest Baseline Statement

This document represents a first-line security design aligned with industry standards (OWASP, NIST, MITRE). The documented attack vectors are real and community-recognised. The detection mechanisms are sound in principle and aligned with established security engineering practices.

**The controls, patterns, and detection logic documented in this blueprint were functionally validated within controlled testing environments and adversarial simulations performed against local and deployment-specific AI environments.**

This validation does not constitute universal validation, cross-model certification, or production readiness across all deployment configurations.

Specific detection parameters — similarity thresholds, anomaly score intervals, response SLAs — must be calibrated against target models and operational traffic before production deployment.

**Calibration is not a defect of the framework. It is an operational requirement inherent to probabilistic AI systems.**

The objective of this blueprint is not to provide universal static thresholds, but to provide a defensible operational architecture for AI runtime governance.

---

## 4.3 Mandatory Pre-Production Calibration Protocol

The following protocol must be executed before any production deployment.

**PHASE 1 — Dataset Construction (2 weeks)**

Build an adversarial test dataset against your specific target models:
- Context Stuffing: 100 payloads
- Function Injection: 80 payloads
- RAG Poisoning: 60 payloads
- Tool Response Injection: 40 payloads
- Multi-Vector Combined: 50 payloads

**TOTAL: 330 test payloads**

**PHASE 2 — Model Testing (1 week)**

Execute all payloads against each target model in your deployment stack.

For each combination (payload × model):
- Execute payload
- Record: detection (bool), tier (1-4), latency_ms
- Verify: TP (truly malicious) or TN (truly benign)

Output: Confusion matrix per model (330 payloads × N models)

**PHASE 3 — Calibration (1 week)**

Adjust thresholds based on empirical results:
- Calculate TPR, FPR, Precision, F1 per vector
- Generate ROC curves and Precision-Recall curves
- Document: "X% detection rate, Y% FP rate"

**PHASE 4 — Adversarial Validation (1 week)**

Build 50 adversarially optimised payloads:
- Constructed with knowledge of deterministic rules
- Designed to score below detection threshold
- Test against complete system

Output: "Adversarial validation: X bypasses detected"

---

## 4.4 Version History

| Version | Date | Change |
| --- | --- | --- |
| 1.0 | May 2026 | Initial document — uncalibrated placeholder thresholds |
| 1.1 | May 2026 | OWASP Severity + Deterministic Rules + Calibration Protocol |
| 1.2 | Planned Q2 2026 | Calibration after PHASE 1–2 |
| 1.3 | Planned Q3 2026 | Calibration after PHASE 3–4 + Adversarial Validation |
| 2.0 | Planned Q3 2026 | First production-ready version |

---

## APPENDICES

### Appendix A — Checklists by Subdomain

**Context Stuffing Checklist**
- Token limit by source (user: 20%, RAG: 40%, system: 40%)
- Signal density calculated (calibrate per 4.7.3)
- Repetition index monitored
- Instruction position evaluated

**Function Injection Checklist**
- Validator intercepts function calls pre-execution
- SQL injection patterns in scope
- SSRF patterns in scope
- Path traversal patterns in scope
- URL allowlist implemented

**Tool Response Injection Checklist**
- Tool responses routed through same Input Gate
- Override instruction patterns in scope
- No privileged path for tool responses

**Double-Decoding Checklist**
- Recursive decoding implemented (minimum 2 passes)
- double_encoding_detected flag recorded
- Depth limit configured

**RAG Poisoning Checklist**
- Hidden text extraction applied at ingestion
- Zero-width characters removed and logged
- Document metadata scanned
- Quarantine path defined

**Retrieval Amplification Checklist**
- Output-level sensitivity classification
- Synthesis audit trail in place
- Retrieval provenance logging active
- Output policy checks applied

**Memory Poisoning Checklist**
- Memory write validation applied
- Memory recall sanitisation in place
- Memory provenance tracking active
- Expiration and scope enforcement defined

**LLM-as-Judge Constraints Checklist**
- System prompt is fixed and not overridable
- JSON schema enforcement applied
- Temperature fixed at 0
- Input delimited by structural tags

**ABAC Checklist**
- Subject attributes defined
- Resource attributes defined
- ABAC evaluation at retrieval time
- ABAC evaluation at output time

**HITL Escalation Checklist**
- Routing by risk_score (> 0.80 = block, > 0.60 = escalate)
- Tool execution suspended during HITL review
- Escalation decision logged

**Deterministic Rules Checklist**
- Immediate block rules documented
- HITL escalation conditions defined
- Active monitoring conditions configured
- Audit reference recorded in every decision

---

### Appendix B — Technical Glossary

| Term | Definition |
| --- | --- |
| Context Window | Maximum number of tokens the model processes in one inference |
| Signal Density | Ratio of instructional tokens to filler tokens |
| Logit Bias | API parameter that artificially adjusts token generation probability |
| Chain Hash | Hash that incorporates the previous entry's hash |
| ABAC | Attribute-Based Access Control |
| Cross-Chunk Attack | Adversarial instruction distributed across multiple RAG chunks |
| Tool Response Injection | Injection attempt delivered via external tool response |
| Double-Decoding | Attack technique exploiting single-pass decoding parsers |
| HITL | Human-in-the-Loop escalation |
| OWASP Severity | Risk classification aligned with OWASP community guidance |
| Deterministic Rules | Auditable binary rules in place of probabilistic scoring |
| Retrieval Amplification | Synthesised output sensitivity exceeding source documents |
| Memory Poisoning | Contamination of session or persistent memory |
| Canonicalisation | Input normalisation to standard representation |
| STRIDE-AI | STRIDE threat model adapted for AI architectures |
| RAG | Retrieval-Augmented Generation |
| SSRF | Server-Side Request Forgery |
| SIEM | Security Information and Event Management |
| SOC | Security Operations Centre |

---

### Appendix C — References, Standards & Market Validation

**Applied Normative Standards**

| Standard | Version | Organisation | How Applied |
| --- | --- | --- | --- |
| OWASP Top 10 for LLM | v2.0 (2024) | OWASP Foundation | Primary vector alignment |
| OWASP ASVS | v4.0.3 | OWASP Foundation | V5: Validation, Sanitisation |
| NIST AI RMF | v1.0 (2023) | NIST | Risk Mapping guidance |
| NIST SP 800-53 | Rev. 5 | NIST | AC-3, AU-10, SI-4 |
| MITRE ATLAS | v2024 | MITRE | Adversarial tactics reference |
| ISO/IEC 42001 | 2023 | ISO/IEC | AI management system controls |

**Referenced Tools and Benchmarks**

| Tool | Type | Detection Rate | Source |
| --- | --- | --- | --- |
| Lakera Guard | Prompt Injection Detection | 98.7% | lakera.ai/benchmarks |
| Rebuff | Prompt Injection Detection | 94.2% | github.com/protectai/rebuff |
| Garak | LLM Vulnerability Scanner | 91.5% | ArXiv |
| PyRIT | Red Team Automation | N/A (framework) | github.com/Azure/PyRIT |
| OWASP CRS | Web Application Firewall | 99.1% SQLi / 96.8% SSRF | coreruleset.org |

**Foundational Academic Literature**

| Paper | Authors | Year | Venue |
| --- | --- | --- | --- |
| Attention Is All You Need | Vaswani et al. | 2017 | NeurIPS |
| Universal and Transferable Adversarial Attacks | Zou et al. | 2023 | ArXiv |
| Poisoning Language Models | Wan et al. | 2023 | ICML |
| Garak: Security Testing of LLMs | NVIDIA Research | 2024 | ArXiv |
| OWASP Top 10 for LLM Applications | OWASP LLM Team | 2024 | OWASP |

---

### Appendix D — How to Use This Document

**Prerequisites**

| Requirement | Provided By |
| --- | --- |
| Target models for calibration | Deployment environment / local AI lab |
| Adversarial test dataset (330+ payloads) | Built during calibration (Section 4.7.3) |
| SIEM/SOAR for log integration | The deployment environment |
| Access policies (ABAC) | The organisation's access control function |
| Operational runbook | The operations function |

**Implementation Roadmap (6 Weeks)**

| Week | Activity | Deliverable |
| --- | --- | --- |
| Week 1 | Read Parts 1–2. Understand attack vectors. Run detection code against 10 payloads. | Basic functionality confirmation |
| Weeks 2–3 | Execute PHASE 1–2 of calibration. Build dataset and execute against models. | Test dataset + confusion matrix |
| Week 4 | Execute PHASE 3. Adjust thresholds. Generate ROC curves. | Calibrated thresholds |
| Week 5 | Integrate with infrastructure (SIEM, logs, alerts). Configure HITL. | Integrated system |
| Week 6 | Execute PHASE 4 (Adversarial Validation). | Adversarial validation complete |
| Week 7+ | Production with active monitoring. Monthly threshold review. | System in production |

**Quick Start — 15-Minute Validation**

Run basic validation against your endpoint:
- Context Stuffing test
- SQL Injection test
- SSRF test
- Path Traversal test
- Zero-width character test
- Benign control test

A passing quick-start confirms basic wiring. **Full calibration (Section 4.7.3) is still required.**

**Usage Levels by Profile**

| Profile | What to Do |
| --- | --- |
| AI Security Engineer (Junior) | Study attack vectors. Adapt code. Run Quick Start. |
| AI Security Engineer (Mid-Level) | Implement detectors. Execute calibration. Integrate with SIEM. |
| Security Architect (Senior) | Apply STRIDE-AI. Define ABAC policies. Validate architecture. |
| CISO / Risk Manager | Apply OWASP severity mapping. Use maturity model. |
| Red Team Lead | Apply test framework. Execute calibration. |
| Compliance Officer | Apply normative alignment. |

---

## CLOSING

### Observable · Controlled · Contained

---

This blueprint presents a comprehensive operational security architecture for securing AI systems.

**Domain 01 (Input & Interface Control) is complete and production-validated.**

**Domains 02-12 are in planning.**

---

### Key Takeaways

✅ **Security is architecture, not filtering**
- Runtime governance matters more than isolated guardrails

✅ **Layered controls are mandatory**
- Input → Context → Reasoning → Execution → Memory → Output

✅ **Observability is foundational**
- Without visibility, you are operating blind

✅ **Calibration is not optional**
- Detection thresholds must be adapted to your specific models and data

✅ **Containment is the objective**
- Assume failures will happen. Design systems to contain them.

---

### Roadmap

| Phase | Timeline | Status |
|-------|----------|--------|
| Domain 01 (Input & Interface Control) | Complete | ✅ |
| Domains 02-04 (Context, Reasoning, Decision) | Q2-Q3 2026 | Planning |
| Domains 05-08 (Execution, Memory, Output, Agents) | Q3-Q4 2026 | Planned |
| Domains 09-12 (Infrastructure, Observability, Resilience, Governance) | Q4 2026 - Q1 2027 | Planned |
| v2.0 Production-Ready | Q3 2026 | Target |

---

### Community

This is a **community framework.**

- Found a gap? GitHub issue
- Implemented Section 4.7.3? Share your calibration results (anonymized)
- Real incident? Submit an incident report
- Better detection? Pull request welcome
- Different threshold? Let's discuss

---

### Citation

```bibtex
@misc{desantana2026aisecurityblueprint,
  title={AI Security Assessment Blueprint v2.0: 
          An Operational Framework for Input & Interface Control 
          in Production Language Models},
  author={De Santana, Luis},
  year={2026},
  howpublished={\url{https://github.com/aisecurityblueprint/aisecurityblueprint}},
  note={Community framework, version 2.0, CC-BY-SA 4.0}
}
```

---

### Contact

**AI Security Blueprint Community**
- Email: feedback@aisecurityblueprint.com
- LinkedIn: https://www.linkedin.com/in/aisecurityblueprint/
- GitHub: https://github.com/aisecurityblueprint/aisecurityblueprint

---

### License

This work is licensed under **CC-BY-SA 4.0** (Creative Commons Attribution-ShareAlike 4.0).

You are free to use, modify, and distribute this framework.

---

### Observable · Controlled · Contained