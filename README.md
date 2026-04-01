# ð¥ Clinical AI Guardrails

**Physician-curated safety prompts, guardrails, and red-team benchmarks for healthcare LLMs.**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

Building a healthcare AI product? Your LLM needs clinical guardrails written by doctors, not just engineers.

This repository provides **ready-to-use system prompts, safety rules, and failure benchmarks** for any team shipping AI in healthcare â validated by practicing physicians.

## Why This Exists

LLMs hallucinate. In healthcare, hallucinations kill. Most AI teams lack clinical expertise to write safe medical prompts or catch dangerous edge cases. This repo bridges that gap with:

- **System prompts** organized by medical specialty, written for real clinical workflows
- **Safety guardrails** â hard rules every healthcare LLM must follow (triage escalation, drug interaction flags, scope-of-practice boundaries)
- **Red-team cases** â real-world examples where LLMs fail dangerously in clinical contexts, with severity ratings
- **Evaluation benchmarks** â clinically validated Q&A pairs for testing your model's medical reasoning

Everything here is reviewed by a physician (MBBS) and designed to be dropped directly into your LLM pipeline.

## Repository Structure

```
clinical-ai-guardrails/
âââ prompts/                    # System prompts by specialty
â   âââ primary-care/
â   âââ emergency-medicine/
â   âââ cardiology/
â   âââ dermatology/
â   âââ mental-health/
â   âââ pediatrics/
âââ guardrails/                 # Universal safety rules
â   âââ triage-escalation.md
â   âââ drug-safety.md
â   âââ scope-of-practice.md
â   âââ pediatric-safety.md
â   âââ mental-health-crisis.md
âââ red-team/                   # Dangerous failure cases
â   âââ hallucination-cases.md
â   âââ drug-interaction-failures.md
â   âââ triage-failures.md
â   âââ severity-rating-guide.md
âââ benchmarks/                 # Evaluation Q&A sets
    âââ primary-care-eval.json
    âââ emergency-eval.json
    âââ scoring-rubric.md
```

## Quick Start

### 1. Add a specialty system prompt

Copy any prompt from `prompts/` into your LLM's system message:

```python
with open("prompts/primary-care/symptom-assessment.md") as f:
    system_prompt = f.read()

response = client.messages.create(
    model="claude-sonnet-4-6",
    system=system_prompt,
    messages=[{"role": "user", "content": patient_query}]
)
```

### 2. Layer safety guardrails

Append rules from `guardrails/` to enforce hard safety boundaries:

```python
with open("guardrails/triage-escalation.md") as f:
    safety_rules = f.read()

full_system = f"{system_prompt}\n\n{safety_rules}"
```

### 3. Test with red-team cases

Run cases from `red-team/` against your model to find dangerous failures before your users do.

## Prompt Design Principles

Every prompt in this repo follows these clinical standards:

1. **Scope limitation** â The AI explicitly states what it cannot do (diagnose, prescribe, replace a doctor)
2. **Triage escalation** â Emergency symptoms trigger immediate "call 911 / go to ER" responses
3. **Drug safety** â Never suggests medications without flagging interaction risks and contraindications
4. **Uncertainty disclosure** â The AI communicates confidence levels and recommends professional consultation
5. **Pediatric caution** â Heightened safety thresholds for patients under 18
6. **Mental health protocol** â Suicide/self-harm mentions trigger crisis resource responses, not clinical advice

## Who Should Use This

- **Health AI startups** building patient-facing chatbots or clinical copilots
- **Developers** integrating LLMs into EHR systems or telehealth platforms
- **Researchers** evaluating medical LLM safety and accuracy
- **Healthcare organizations** setting AI governance standards

## Contributing

We welcome contributions from **physicians, nurses, pharmacists, and clinical researchers**. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Clinical domain expertise is valued above code contributions. If you can identify a dangerous LLM failure case or write a better safety guardrail, your PR is welcome.

## Curated By

**Dr. Siddharth Rajasekar, MBBS**
Physician and healthcare AI safety researcher. Building open-source clinical infrastructure for responsible AI deployment in medicine.

## License

MIT License â use these prompts freely in your products. Attribution appreciated but not required.

If these guardrails help keep a patient safe, that's the only credit that matters.
