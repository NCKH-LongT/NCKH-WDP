# AI Model Integration

## 1. Research Direction

This project does not build or fine-tune a new AI model. Instead, it applies an **Input–Output–Method (IOM)** workflow to integrate existing LLMs into a hackathon evaluation system.

The workflow is inspired by:

| Paper | Applied Idea |
|---|---|
| TA Buddy | AI suggested score per rubric criterion + human accept/override |
| StepGrade | Structured step-by-step evaluation for functionality, code quality and efficiency |
| JorGPT | Rubric-prompted LLM grading, human oversight, MAE/correlation evaluation |
| CodEv | Optional consistency check and feedback-oriented evaluation |
| GradeOpt / GradeHITL | Future work for rubric/prompt refinement |

## 2. IOM Definition

### 2.1. Input

| Input | Source | Usage |
|---|---|---|
| Problem statement | Admin / track setup | Gives AI task context |
| Dynamic rubric | MongoDB | Defines criteria, weights, max score and AI instructions |
| Source code / GitHub diff | GitHub API/Webhook | Main technical evidence |
| README / setup guide | GitHub repository | Documentation evidence |
| Demo link / slide link | Submission | Optional evidence for product/demo criteria |
| Commit metadata | GitHub webhook | Progress and contribution signals |
| Previous AI reviews | Database | Used for final aggregate review |

### 2.2. Output

| Output | Purpose |
|---|---|
| Suggested score per criterion | Prefill judge scoring sheet |
| Evidence from code/repository | Explain why the score is suggested |
| Feedback | Help judge understand strengths and weaknesses |
| Risk warnings | Highlight issues requiring human review |
| Confidence level | Indicate uncertainty |
| Suggested judge questions | Support final Q&A or presentation review |
| needsHumanReview flag | Avoid blind automation |

### 2.3. Method

The method includes:

1. Rubric-based prompting.
2. StepGrade-style structured criterion evaluation.
3. TA Buddy-style human accept/override.
4. Optional consistency check.
5. Final judge decision.

## 3. AI Evaluation Workflow

```text
GitHub diff/source snapshot
+ Problem statement
+ Dynamic rubric
+ README/demo/commit metadata
→ Build IOM prompt
→ Call LLM API
→ Parse JSON output
→ Store AIReview and AIReviewCriteria
→ Show suggestions in Judge UI
→ Judge accept/override
→ Final score and ranking
```

## 4. Suggested Prompt Strategy

For each rubric criterion, the AI must:

1. Identify relevant evidence from code, diff, README or repository.
2. Explain strengths and weaknesses briefly.
3. Assign a suggested score from 0 to maxScore.
4. Provide concise feedback.
5. Mark confidence as low, medium or high.

The AI must return valid JSON only.

## 5. AI Output JSON

```json
{
  "overallSummary": "The solution implements core features but lacks robust error handling.",
  "criteriaResults": [
    {
      "criterionId": "code_quality",
      "criterionName": "Code Quality",
      "suggestedScore": 7,
      "maxScore": 10,
      "evidence": "The code is modular, but validation logic is duplicated in multiple files.",
      "feedback": "Move duplicated validation into a shared utility module.",
      "confidence": "medium"
    }
  ],
  "risks": ["Missing error handling for failed API calls"],
  "suggestedQuestionsForJudges": ["How does the system handle API failure?"],
  "needsHumanReview": true
}
```

## 6. Database Mapping

| IOM Component | Collection / Field |
|---|---|
| Source diff input | `commitdiffs.patch` |
| Dynamic rubric input | `rubrics`, `criteria` |
| AI review result | `aireviews` |
| Criterion-level AI output | `aireviewcriteria` |
| Official judge score | `scoresheets`, `scores` |
| Judge override | `scores.isOverridden`, `scores.overrideReason` |
| Ranking output | `rankings` |

## 7. Why No Fine-tuning in MVP

Fine-tuning requires a large dataset of source code, rubric, human judge scores and comments. The current project does not yet have enough official SEAL Hackathon data. Therefore, the MVP uses prompt-based LLM evaluation and stores judge override data for possible future fine-tuning or calibration.
