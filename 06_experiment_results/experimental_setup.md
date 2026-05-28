# Experimental Setup

## Current Status

No official experiment has been conducted yet. This file defines the planned setup for the AI-assisted source code evaluation workflow.

## Planned Setup

| Item | Plan |
|---|---|
| Dataset size | 10–20 sample submissions initially |
| Human evaluators | 2–3 judges/evaluators |
| AI method | Existing AI model/API with structured rubric prompt |
| Selected model | To be decided based on accessibility and API availability |
| Baselines | Manual judging, simple prompt, structured rubric prompt |
| Rubric | Dynamic rubric adapted from one selected Hackathon round |
| AI Output | Suggested criterion score, evidence, feedback, confidence, risks, suggested judge questions |
| Final Output | Judge-confirmed score and ranking |

## Procedure

1. Prepare source code submissions or GitHub repositories.
2. Prepare one dynamic rubric.
3. Ask human evaluators to score submissions.
4. Run AI evaluation with a simple prompt.
5. Run AI evaluation with structured rubric prompt.
6. Store criterion-level AI suggestions.
7. Judges accept or override suggestions.
8. Compare AI suggestions with judge-confirmed scores.
9. Compare AI-supported ranking with judge-confirmed ranking.
10. Analyze time reduction and feedback usefulness.

## Missing

- Final dataset.
- Final AI API/model.
- Human judge participants.
- Real SEAL Hackathon submissions.

## Important Boundary

The experiment evaluates the AI-assisted source code evaluation workflow. It does not evaluate the entire Hackathon management system.
