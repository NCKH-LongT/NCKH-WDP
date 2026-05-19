# AI Model Integration

## Papers applied

- **TA Buddy**: AI suggested grades per criterion + human accept/override.
- **StepGrade**: CoT/structured criterion-by-criterion evaluation.
- **CodEv**: optional consistency check/agreement.
- **JorGPT**: metrics and human oversight.

## AI Input

```json
{
  "problemStatement": "...",
  "rubric": [
    {
      "criterionId": "functionality",
      "name": "Functionality",
      "description": "Solution satisfies required features",
      "maxScore": 10,
      "weight": 0.3
    }
  ],
  "sourceInput": {
    "type": "github_diff",
    "commitSha": "...",
    "changedFiles": []
  }
}
```

## AI Output

```json
{
  "criteriaResults": [
    {
      "criterionId": "functionality",
      "suggestedScore": 8,
      "evidence": "Main feature implemented but error handling incomplete.",
      "feedback": "Add validation and failed request handling.",
      "confidence": "medium"
    }
  ],
  "overallFeedback": "...",
  "needsHumanReview": true
}
```

## Prompt strategy

For each criterion:
1. Identify evidence from code/diff.
2. Explain strengths and weaknesses briefly.
3. Assign score.
4. Provide actionable feedback.

AI score is only suggestion. Judge score is official.
