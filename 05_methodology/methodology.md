# Methodology

## 1. Research Approach

This study follows a **prototype-based empirical evaluation** approach. The goal is to evaluate how an existing AI model/API can support a hackathon source code evaluation workflow.

## 2. Method Overview

```text
Dynamic rubric
+ GitHub source code/diff
+ Problem statement
→ structured AI evaluation
→ AI suggested scores and evidence
→ Judge accept/override
→ Final score and ranking
→ Compare AI-supported results and human results
```

## 3. Step-by-step Procedure

### Step 1: Define Dynamic Rubric

A rubric is created for a selected SEAL Hackathon round. Each criterion includes:

- Name
- Description
- Weight
- Maximum score
- AI support status
- Judge-only flag if needed
- AI instruction if supported

### Step 2: Prepare Source Code Submissions

The team prepares sample source code submissions or GitHub repositories. Each submission should include:

- Source code
- README
- Optional demo link
- Optional slide link
- Commit history or diff

### Step 3: Human Judge Evaluation

Human evaluators score each submission using the same rubric. These scores are treated as reference scores for comparison.

### Step 4: AI Evaluation

The AI Evaluation Service receives problem statement, source code/diff and dynamic rubric as input. It returns suggested scores, evidence, feedback, confidence and risk warnings per criterion.

### Step 5: Judge Review

Judges review AI suggestions and either accept or override them. Override reasons are stored for analysis.

### Step 6: Analysis

The system compares:

- AI suggested score vs judge score
- AI-supported ranking vs judge ranking
- Simple prompt vs structured rubric prompt
- Manual grading time vs AI-assisted grading time
- AI acceptance vs override rate

## 4. Expected Scientific Contribution

The study contributes a practical workflow for adapting AI-assisted grading methods into a real hackathon management context with dynamic rubrics, GitHub evidence and judge-controlled final scoring.
