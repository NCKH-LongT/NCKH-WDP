# Baseline

## Baseline 1: Manual Judge Scoring

Human judges evaluate submissions manually using the rubric without AI assistance.

Purpose:

- Main reference workflow.
- Used to measure time and official score.

## Baseline 2: Simple AI model Prompt

The AI model receives source code and rubric and returns a general score without structured criterion-by-criterion reasoning.

Purpose:

- Shows limitations of unstructured AI grading.
- Used to compare with structured evaluation workflowd prompt.

## Baseline 3: Structured AI-assisted evaluation workflow Prompt

The AI model receives problem statement, source code/diff and dynamic rubric. It returns criterion-level suggested scores, evidence, feedback and confidence.

Purpose:

- Tests whether AI-assisted evaluation workflow output is more useful and explainable.

## Proposed Workflow: AI-assisted Judge Review

The structured AI output is shown to judges. Judges can accept or override AI suggestions. Final scores are determined by judges, not AI.

Purpose:

- Represents the final system workflow.
- Measures practical usefulness, override rate and time reduction.

## Comparison Plan

| Comparison | Purpose |
|---|---|
| Manual vs AI-assisted | Measure time saving and workflow efficiency |
| Simple prompt vs structured rubric prompt | Measure effect of structured evaluation |
| AI score vs Judge score | Measure score alignment |
| AI ranking vs Judge ranking | Measure ranking alignment |
