# Core Paper Selection After Adding 4 New References

## Final core set

After reviewing the original 14 papers and the 4 newly added references, the scientific paper should mainly use the following **5 core papers**:

```text
1. Rubric Is All You Need
2. TA Buddy
3. StepGrade
4. JorGPT
5. CodEv
```

These five papers are enough to build the theoretical foundation for the research topic:

```text
AI-assisted source code evaluation and ranking based on dynamic rubrics in programming competitions.
```

---

## Why these 5 papers are the most suitable

| Paper | Main role | Why it is core |
|---|---|---|
| **Rubric Is All You Need** | Dynamic / question-specific rubric | Directly supports rubric-based LLM code evaluation and criterion-level assessment. |
| **TA Buddy** | Human-in-the-loop workflow | Shows how AI suggestions can be accepted or overridden by human graders. |
| **StepGrade** | Structured prompting | Gives the prompting strategy for step-by-step criterion evaluation. |
| **JorGPT** | Evaluation methodology | Provides metrics and workflow for comparing LLM grades with human grades. |
| **CodEv** | Reliability and consistency | Supports discussion on feedback quality, consistency, and future reliability checks. |

---

## Relationship between research paper and application

The Hackathon application is a full system, but the scientific paper is narrower.

| Aspect | Application project | Scientific paper |
|---|---|---|
| Scope | Full Hackathon management system | AI-assisted source code evaluation module |
| Includes | Events, teams, GitHub, submissions, judges, rankings, prizes | AI-assisted evaluation workflow, prompt design, AI-human evaluation |
| AI role | Supporting module | Main research object |
| Output | Working application | Scientific workflow and evaluation plan |

---

## What should be applied to the project now

The project does not need to implement all advanced ideas from the papers. It only needs a practical subset:

```text
Dynamic rubric
+ source code / GitHub diff
+ structured LLM prompt
+ criterion-level AI suggestions
+ evidence and feedback
+ judge accept/override
+ final score/ranking
```

---

## What should remain as future work

```text
- multi-model comparison
- ensemble evaluation
- repeated consistency tests
- large-scale dataset construction
- automatic rubric optimization
- pairwise ranking by LLM
```

---

## Final positioning statement

The research does not study the whole Hackathon system. It studies one module inside that system:

```text
AI-assisted source code evaluation using dynamic rubrics.
```

The application provides the context, database, and workflow environment. The scientific contribution is the proposed AI-assisted evaluation workflow and its evaluation plan.
