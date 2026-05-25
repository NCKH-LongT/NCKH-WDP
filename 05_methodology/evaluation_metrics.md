# Evaluation Metrics

| Metric | Meaning | Why Used |
|---|---|---|
| MAE | Average difference between AI score and judge score | Measures score alignment |
| Pearson Correlation | Relationship between AI scores and judge scores | Measures score trend similarity |
| Spearman Rank Correlation | Similarity between AI ranking and judge ranking | Important for contest ranking |
| Kendall's Tau | Pairwise agreement between two rankings | Additional ranking reliability metric |
| Top-k Agreement | Whether AI and judges select similar top teams | Important for finalist selection |
| Human Override Rate | Percentage of AI suggestions changed by judges | Measures trust and usefulness |
| Time Reduction | Difference between manual grading time and AI-assisted grading time | Measures workflow efficiency |
| Criterion-level Error | Score difference per rubric criterion | Identifies criteria AI handles well or poorly |
| Feedback Usefulness Rating | Judge rating of AI feedback quality | Measures practical usefulness |
| Response Time | Time required for AI evaluation API | Measures system feasibility |

## Metric Formulas / Notes

### MAE

```text
MAE = average(|AI_score - Judge_score|)
```

### Human Override Rate

```text
Override Rate = Number of overridden AI suggestions / Total AI suggestions
```

### Top-k Agreement

```text
Top-k Agreement = Number of teams appearing in both AI top-k and judge top-k / k
```

## Criterion-level Analysis

The system should report which criteria are more reliable for AI:

- Code quality
- Architecture
- AI integration
- Documentation
- RAG reliability
- UX/demo/presentation

Presentation and teamwork criteria may need judge-only handling.
