# Clinical AI Guardrails

**Physician-curated safety prompts, guardrails, and red-team benchmarks for healthcare LLMs.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

Building a healthcare AI product? Your LLM needs clinical guardrails written by doctors, not just engineers.

This repository provides **ready-to-use system prompts, safety rules, and failure benchmarks** for any team shipping AI in healthcare -- validated by practicing physicians.

## Why This Exists

LLMs hallucinate. In healthcare, hallucinations kill. Most AI teams lack clinical expertise to write safe medical prompts or catch dangerous edge cases. This repo bridges that gap with:

- **System prompts** organized by medical specialty, written for real clinical workflows
- **Safety guardrails** -- hard rules every healthcare LLM must follow (triage escalation, drug interaction flags, scope-of-practice boundaries)
- **Red-team cases** -- real-world examples where LLMs fail dangerously in clinical contexts, with severity ratings
- **Evaluation benchmarks** -- clinically validated Q&A pairs for testing your model's medical reasoning

Everything here is reviewed by a physician (MBBS) and designed to be dropped directly into your LLM pipeline.

## Repository Structure

```
clinical-ai-guardrails/
  prompts/
    primary-care/
      symptom-assessment.md        # OLDCARTS-based patient symptom intake
    emergency-medicine/
      triage-support.md            # ESI triage decision support for clinicians
  guardrails/
    triage-escalation.md           # When to tell users to call 911
    drug-safety.md                 # Medication safety boundaries
    scope-of-practice.md           # What AI should never do
    mental-health-crisis.md        # Crisis detection and response protocol
  red-team/
    hallucination-cases.md         # Documented dangerous LLM failures
    severity-rating-guide.md       # How to score clinical AI failures
  benchmarks/
    primary-care-eval.json         # 10 evaluation test cases
    scoring-rubric.md              # Pass/fail criteria and thresholds
```

## Quick Start

1. **Pick a guardrail** from `guardrails/` and add it to your system prompt
2. **Test your model** against cases in `benchmarks/primary-care-eval.json`
3. **Score the results** using `benchmarks/scoring-rubric.md`
4. **Red-team** your model using patterns from `red-team/hallucination-cases.md`

### Example: Adding Triage Escalation to Claude

```python
import anthropic

# Load the triage guardrail
with open("guardrails/triage-escalation.md") as f:
    triage_rules = f.read()

client = anthropic.Anthropic()
message = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=1024,
    system=f"You are a healthcare assistant. Follow these safety rules strictly:\n\n{triage_rules}",
    messages=[
        {"role": "user", "content": "I have severe chest pain and my left arm is numb"}
    ]
)
```

## Prompt Design Principles

1. **Safety first** -- every prompt includes mandatory escalation triggers
2. **Scope boundaries** -- AI should never diagnose, prescribe, or replace a physician
3. **Evidence-based** -- guardrails reference clinical guidelines and mortality data
4. **Fail safe** -- when uncertain, always escalate to a human clinician
5. **Transparent** -- AI must identify itself and state its limitations

## Contributing

We welcome contributions from clinicians, patient safety professionals, and healthcare AI engineers. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Priority areas:
- Additional medical specialty prompts (pediatrics, oncology, OB/GYN)
- International clinical guideline adaptations
- Non-English language prompt translations
- New red-team cases from real-world LLM failures

## License

MIT License with medical disclaimer. See [LICENSE](LICENSE) for details.

---

**Curated by Dr. Siddharth Rajasekar, MBBS**

*This repository is not medical advice. It is a safety engineering resource for teams building healthcare AI products.*
