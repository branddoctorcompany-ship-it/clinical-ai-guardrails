# Contributing to Clinical AI Guardrails

Thank you for your interest in improving healthcare AI safety. This project values clinical expertise above code contributions.

## Who Should Contribute

- Physicians, nurses, pharmacists, and clinical researchers -- Your domain knowledge is the backbone of this project
- AI/ML engineers building healthcare products -- Your real-world deployment experience helps us catch gaps
- Medical students and residents -- Fresh clinical training perspective is valuable
- Patient safety professionals -- Your expertise in failure analysis directly applies here

## What We Need

### High Priority
- New red-team cases -- Real examples of dangerous LLM outputs you've observed in clinical contexts
- Specialty-specific prompts -- System prompts for specialties not yet covered (ophthalmology, orthopedics, OB/GYN, oncology, etc.)
- Guardrail improvements -- Gaps in existing safety rules, missed edge cases, outdated clinical information
- International adaptations -- Crisis hotline numbers, clinical guidelines, and drug formulary differences for non-US contexts

### Also Welcome
- Benchmark questions with clinically validated answers
- Improvements to existing prompts based on deployment experience
- Documentation and clarity improvements
- Translations of guardrails and prompts

## Submission Guidelines

### For Red-Team Cases

Follow this format:

Case: [Brief description]
Severity: Critical / Serious / Moderate / Minor

Prompt: [The input that triggered the dangerous response]

Dangerous LLM Response (observed):
[Paraphrased dangerous output -- do not quote copyrighted model outputs verbatim]

Why this is dangerous:
[Clinical explanation accessible to non-clinicians]

Correct response pattern:
[What the model should have said]

### For New Prompts

Include:
- Use case -- When and where this prompt would be used
- System prompt -- The full prompt text
- Clinical rationale -- Why the prompt is structured this way, with references to clinical standards
- Known limitations -- What the prompt does NOT cover
- Your credentials -- Helps reviewers assess clinical accuracy (e.g., "EM physician, 8 years practice")

### For Guardrail Updates

Include:
- What's missing or wrong in the current guardrail
- Proposed change with the updated text
- Clinical justification -- Evidence or guidelines supporting the change
- Test cases -- At least one scenario demonstrating why the change matters

## Review Process

1. Submit a pull request with your contribution
2. A clinical reviewer (physician) will assess medical accuracy
3. Feedback or approval within 2 weeks
4. Merged contributions are credited in the relevant file

## Code of Conduct

- Patient safety is the top priority in all discussions
- Respect clinical expertise across all disciplines
- No anecdotal medical advice in issues or discussions
- Disagreements about clinical standards should reference published guidelines

## Questions?

Open an issue with the question label, or reach out to the maintainers.
