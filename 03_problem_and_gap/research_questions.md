# Research Questions

## Main Research Question

How can an existing LLM be integrated into a hackathon management system using an Input–Output–Method workflow to support dynamic rubric-based source code evaluation?

## Sub Research Questions

| ID | Research Question | Purpose |
|---|---|---|
| RQ1 | What input components are necessary for AI-assisted source code evaluation in a hackathon context? | Identify whether source code, GitHub diff, problem statement, rubric, README, demo link, slide link and commit history are needed |
| RQ2 | What output format is most useful for judges? | Define AI output: suggested score, evidence, feedback, confidence, risks, suggested questions |
| RQ3 | How can StepGrade-style structured prompting be adapted to evaluate each rubric criterion separately? | Design prompt method for criterion-level evaluation |
| RQ4 | How close are AI-suggested criterion scores to human judge scores? | Evaluate score alignment |
| RQ5 | How often do judges accept or override AI-suggested scores? | Measure usefulness and trust |
| RQ6 | How similar is AI-supported ranking to human judge ranking? | Evaluate ranking alignment for contest context |
| RQ7 | How much grading time can be reduced when judges use AI-generated evidence and suggested scores? | Evaluate workflow efficiency |

## Scope Boundary

The project does not research model training or fine-tuning. The focus is workflow design, prompt-based LLM integration, database support, judge interaction and empirical evaluation.
