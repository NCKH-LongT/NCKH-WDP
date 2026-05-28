# AI-assisted Evaluation Integration

## 1. Research Direction

This project integrates an existing AI model/API into the source code evaluation process of a programming competition system.

The Hackathon application remains a full system, but the scientific paper focuses only on the AI-assisted source code evaluation module.

The workflow is inspired by:

| Paper | Applied Idea |
|---|---|
| Rubric Is All You Need | Dynamic / question-specific rubric and criterion-level evaluation |
| TA Buddy | AI suggested score per rubric criterion + human accept/override |
| StepGrade | Structured step-by-step evaluation for source code criteria |
| JorGPT | Evaluation metrics comparing AI-generated grades with human grades |
| CodEv | Reliability and consistency discussion for future work |

## 2. Input / Method / Output

### 2.1. Input

| Input | Source | Usage |
|---|---|---|
| Problem statement | Admin / track / round setup | Gives task context |
| Dynamic rubric | MongoDB | Defines criteria, weights, max score, AI-supported and judge-only flags |
| Source code / GitHub diff | GitHub API/Webhook or submission snapshot | Main technical evidence |
| README / setup guide | GitHub repository or submission | Documentation and setup evidence |
| Execution results | Build/lint/test pipeline if available | Deterministic technical evidence |
| Demo link / slide link | Submission | Optional context; not enough for judge-only criteria |
| Commit metadata | GitHub webhook | Progress and evidence context |

### 2.2. Method

The method includes:

1. Load problem statement and active rubric.
2. Extract source evidence from GitHub diff or final source snapshot.
3. Build a structured rubric-based prompt.
4. Evaluate each AI-supported criterion separately.
5. For judge-only criteria, do not assign a score.
6. Return JSON output with suggested score, evidence, feedback, confidence and risks.
7. Show AI suggestions in Judge UI.
8. Judge accepts or overrides each suggestion.
9. Final score and ranking are calculated from judge-confirmed scores.

### 2.3. Output

| Output | Purpose |
|---|---|
| Suggested score per criterion | Advisory score for judge review, not final score |
| Evidence from code/repository | Explain why the suggestion was made |
| Feedback | Summarize strengths and weaknesses |
| Risk warnings | Highlight issues requiring human review |
| Confidence level | Indicate uncertainty |
| Suggested judge questions | Support final Q&A or presentation review |
| needsHumanReview | Mark cases requiring careful human review |

## 3. Model Selection

The paper does not need to make a new model the main contribution. However, for experiment reproducibility, the implementation should record the selected provider/model used in the evaluation.

For the prototype, the team can select **one accessible general-purpose code-capable AI model/API** based on availability, cost, latency, and API access. The selected model should be reported in the experimental setup with:

- provider;
- model name;
- model version or access date;
- temperature and decoding configuration;
- prompt template version;
- input size limit and truncation strategy.

The research contribution remains the **AI-assisted source code evaluation workflow**, not the model itself.

## 4. Judge-controlled Final Scoring

AI output is advisory. The judge must review each suggested score and either accept or override it. Final score and ranking are calculated only from judge-confirmed scores.
