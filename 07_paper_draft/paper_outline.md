# Paper Outline

## Title

An IOM-based AI-assisted Source Code Evaluation Workflow for SEAL Hackathon Management Systems

## Abstract

- Problem: manual hackathon judging is time-consuming and inconsistent.
- Gap: existing LLM grading studies focus on classroom assignments.
- Method: propose IOM workflow using GitHub source/diff, dynamic rubric and LLM output.
- Evaluation: compare AI suggested scores/ranking with human judges.
- Contribution: practical workflow without training a new model.

## 1. Introduction

- SEAL Hackathon context.
- Dynamic rubrics across seasons and rounds.
- Challenges of manual source code evaluation.
- Why AI can help but should not replace judges.
- Research questions.

## 2. Related Work

- AI-assisted source code grading: TA Buddy, AI-based grading.
- Structured prompting: StepGrade.
- Rubric LLM grading: JorGPT.
- Consistency and feedback: CodEv.
- Human-in-the-loop and rubric refinement.

## 3. Proposed IOM Workflow

- Input layer.
- Method layer.
- Output layer.
- Judge accept/override.
- Ranking support.

## 4. System Design

- MERN + React Native architecture.
- GitHub webhook.
- Dynamic rubric.
- AI Evaluation Service.
- Judge Scoring UI.

## 5. Methodology

- Dataset.
- Baselines.
- Metrics.
- Experiment procedure.

## 6. Results

To be added after evaluation.

## 7. Discussion

- Which criteria AI supports well.
- Which criteria should remain judge-only.
- Limitations of prompt-based LLM grading.
- Ethical and reliability concerns.

## 8. Conclusion and Future Work

- Summary.
- Fine-tuning/calibration as future work.
- Multi-model agreement.
- Rubric optimization.
