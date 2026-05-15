# Contributing to AI Security Blueprint

Thank you for your interest in contributing to this framework!

This is a **community-driven project**. We welcome feedback, improvements, and contributions at all levels.

---

## How to Contribute

### 1. Report a Bug or Issue

Found a detection bypass? A false positive? An error in the documentation?

**Via GitHub Issues:**
- [Create an issue](https://github.com/aisecurityblueprint/aisecurityblueprint/issues)
- Title: Clear, specific description
- Description: Steps to reproduce, expected vs. actual behavior
- Attach evidence if applicable (test payload, output logs, etc.)

**Via Email:**
- feedback@ai-security-blueprint.com
- Include: Issue description, evidence, suggested fix (if any)

---

### 2. Share Calibration Results

Implemented Section 4.7.3 and want to share your calibration results?

**We want to hear about:**
- Detection rates you achieved (by vector)
- False positive rates
- Thresholds you landed on
- Models you tested against
- Any discrepancies from v2.0 baseline

**How to submit:**
1. Create a new file in `/evidence/calibration-thresholds/` named:
   `thresholds-[your-organization]-[date].json`
2. Format (anonymized):
```json
   {
     "organization": "Acme Corp",
     "date": "2026-05-20",
     "models_tested": ["Mixtral 8x22B", "Mistral 7B"],
     "vector_results": {
       "context_stuffing": {
         "detection_rate": 0.98,
         "false_positive_rate": 0.02,
         "threshold_signal_density": 0.17
       },
       "function_injection": {
         "detection_rate": 0.998,
         "false_positive_rate": 0.001
       }
     },
     "notes": "Calibrated for fintech environment"
   }
```
3. Submit via PR or email

---

### 3. Report a Real-World Incident

Detected an actual attack using this framework?

**We want to learn:**
- Attack vector (which one matched?)
- How the detection worked
- Response time
- False positive risk assessment
- Any patterns we missed

**Submit anonymized incident report:**
1. Create file: `/evidence/production-incidents/incident-[date]-[vector].json`
2. Format:
```json
   {
     "date": "2026-05-15",
     "vector": "function_injection",
     "detection_trigger": "ssrf_metadata_aws",
     "response_time_seconds": 2.3,
     "action_taken": "block",
     "false_positive_risk": "low",
     "context": "Dark web monitoring pipeline"
   }
```

---

### 4. Propose an Improvement

Found a better detection pattern? Different threshold? New attack vector?

**Process:**
1. Create a GitHub Discussion (or issue with label `enhancement`)
2. Describe: What's the improvement? Why is it needed? Evidence?
3. We'll discuss and iterate

**Examples of contributions we value:**
- More efficient detection code
- Better handling of encoding tricks
- Cross-model validation results
- Translations to other languages
- Documentation improvements

---

### 5. Submit a Pull Request

For code changes, bug fixes, or documentation:

1. **Fork the repository**
2. **Create a branch:** `feature/your-improvement` or `fix/issue-number`
3. **Make changes** following the code style in `/code/`
4. **Test:** Run your changes against Section 4.7.3 test dataset
5. **Commit:** Clear, descriptive commit messages
6. **Push to your fork**
7. **Create PR** with description of what changed and why

**PR Guidelines:**
- Reference any related issues
- Include evidence (test results, before/after)
- Keep PRs focused (one feature/fix per PR)
- Be patient — we review thoroughly

---

## Code Style & Standards

### Python Code
- Follow PEP 8
- Use type hints where applicable
- Include docstrings for all functions
- Test against Section 4.7.3 dataset before submitting

### Documentation
- Clear, concise English
- Link to relevant sections of the blueprint
- Include examples where helpful
- Acknowledge limitations/caveats

---

## What We're Looking For

| Contribution Type | Priority | How to Submit |
|---|---|---|
| Detection bypass (real or test) | 🔴 Critical | GitHub issue + evidence |
| Calibration results | 🟠 High | JSON file in /evidence |
| Production incident report | 🟠 High | JSON file in /evidence |
| False positive examples | 🟡 Medium | Issue + logs |
| Better detection code | 🟡 Medium | PR to /code |
| Documentation improvement | 🟡 Medium | PR or issue |
| Translation | 🟢 Low | Issue first, then PR |

---

## Community Guidelines

- **Be respectful.** We're building security architecture, not starting wars.
- **Be specific.** "It doesn't work" is less helpful than "Function X returns Y when Z happens."
- **Be humble.** We're all learning. No shame in wrong assumptions.
- **Be patient.** Reviewers are volunteers. Responses may take time.

---

## Feedback Channels

- **GitHub Issues:** Bug reports, feature requests
- **GitHub Discussions:** Questions, ideas, community input
- **Email:** feedback@ai-security-blueprint.com (for sensitive findings)
- **LinkedIn:** @luis-de-santana (for announcements, feedback)

---

## Recognition

Contributors will be:
- ✅ Credited in the framework documentation
- ✅ Mentioned in release notes
- ✅ Invited to review upcoming domains (02-12)

---

## Code of Conduct

This project operates under a simple principle:

**"The model suggests. The architecture decides."**

In our community: **Ideas suggest. Evidence decides.**

- Bring evidence, not speculation
- Question assumptions, not people
- Collaborate on solutions, not blame

---

## Questions?

- Check [FAQ.md](./docs/FAQ.md) first
- Open a GitHub Discussion
- Email: feedback@ai-security-blueprint.com

---

Thank you for contributing to AI security! 🙏

**Observable · Controlled · Contained**