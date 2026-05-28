# Literature Review Matrix - Updated with 4 Additional References

## Research Topic

**AI-assisted Source Code Evaluation and Ranking Based on Dynamic Rubrics in Programming Competitions**

This matrix uses an **AI-assisted evaluation workflow perspective**:

```text
Input  → problem statement, source code/GitHub diff, dynamic rubric, optional execution results
Method → structured LLM prompting, rubric-based evaluation, human-in-the-loop review
Output → suggested criterion scores, evidence, feedback, confidence, judge questions, ranking support
```

## Core and supporting matrix

| No | Paper | Domain | Input | Output | Method / Model | Evaluation | AI-assisted evaluation workflow Contribution to Our Research | Relevance |
|---:|---|---|---|---|---|---|---|---|
| 1 | **Rubric Is All You Need: Improving LLM-based Code Evaluation With Question-Specific Rubrics** | LLM-based code evaluation | Problem description, student code, model/reference solution when available, question-specific rubric | Score, feedback, logical assessment, rubric-point assessment | Complete Rubric Evaluation (CRE), Pointwise Rubric Evaluation (PRE), Ensembling Method Evaluation (EME) | Spearman correlation, Cohen's Kappa, Leniency, expert comparison | Strongest support for dynamic/question-specific rubric. PRE directly supports `AiReviewCriterion` design. | **Very High / Core** |
| 2 | **TA Buddy: Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments** | Source code grading / programming education | Problem statement, source code submission, grading rubric | Suggested ratings per rubric criterion, reasoning | AI-assisted grading with human accept/override | Time reduction, grade agreement | Core human-in-the-loop workflow: AI suggests, judge decides. | **Very High / Core** |
| 3 | **StepGrade: Grading Programming Assignments with Context-Aware LLMs** | Programming assignment grading | Assignment question, submitted code, previous evaluation context | Grade and detailed feedback for functionality, code quality, efficiency | Step-by-step structured prompting / CoT-style evaluation | Expert comparison, grading quality, interpretability | Prompt design for criterion-by-criterion evaluation with evidence. | **Very High / Core** |
| 4 | **JorGPT: Instructor-Aided Grading of Programming Assignments with LLMs** | LLM grading system | Student submissions, rubric, instructor configuration | Grades, feedback, comparison across models | Multi-LLM grading with instructor oversight | MAE, adjusted R², correlation, processing time | Evaluation metrics and human oversight justification. | **High / Core** |
| 5 | **CodEv: Automated Grading Framework Leveraging LLMs** | Automated grading / code feedback | Code, problem, criteria, compile/test information | Scores, comments, feedback | CoT-style prompting, LLM ensemble, agreement tests | Consistency, reliability, feedback quality | Reliability and feedback quality discussion; optional consistency feature. | **High / Core-supporting** |
| 6 | **The Future of Grading Programming Assignments in Education** | Programming education | Programming tasks, student code, teacher prompt/instruction | Grades and feedback | ChatGPT API repeated grading | Teacher comparison, correlation, repeatability | Empirical evidence that ChatGPT-style tools can grade code but need human verification. | High / Supporting |
| 7 | **A Survey on LLM-as-a-Judge** | LLM evaluation methodology | Evaluation target, criteria/rubric, prompt, context | Score, label, comparison, explanation | LLM-as-a-judge pipeline | Agreement, bias, robustness, consistency | Supports reliability, bias control, and human-alignment discussion. | Medium-High / Supporting |
| 8 | **Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena** | LLM-as-a-judge / human preference evaluation | Question and candidate responses | Pairwise winner, score, explanation | Pairwise comparison, single-answer grading, reference-guided grading | Human agreement, bias analysis | Useful as optional background for LLM-as-a-judge and ranking-style evaluation, but not code-specific. | Medium / Optional |
| 9 | AI-based Automated Grading of Source Code of Introductory Programming Assignments | Source code grading | Problem statement, source code, instructor rubric | Automated grade/suggested assessment | LLM for code/rubric-based grading | AI-human grading comparison | Supports feasibility of rubric-based code grading | High |
| 10 | A Comparative Study of LLMs in Programming Education | LLM comparison | Student submissions, rubric | Grades, feedback | GPT/Claude/Gemini comparison | Accuracy, efficiency, feedback quality | Model selection and comparison | Medium |
| 11 | Systematic Comparison of LLMs for Automated Assignment Assessment | Programming education | Large set of submissions | Automated assessment outputs | Multiple LLMs | Correlation, variability, ICC | Reliability and model selection | Medium |
| 12 | Hands-on Analysis of LLMs for Auto Evaluation of Programming Assignments | Programming assessment | Programming assignments | AI grades | Multi-run LLM evaluation | Consistency, accuracy | Multi-run score stability idea | Medium |
| 13 | GradeHITL / Human-in-the-loop grading work | Rubric grading | Student answers, rubric, human expert inputs | Refined scores | Human-in-the-loop rubric refinement | Accuracy improvement | Future work for dynamic rubric refinement | Medium |
| 14 | GradeOpt / guideline optimization work | Guideline optimization | Answers, grading guideline | Optimized guideline, score | Multi-agent grader-reflector-refiner | Accuracy, ablation | Future work: prompt/rubric optimization | Medium |
| 15 | TRACE | Collaborative project assessment | GitHub repository/project data | Project assessment dashboard | Repository mining, analytics, AI support | Instructor comparison, time reduction | GitHub-based project evidence workflow | Medium |
| 16 | Transparency and Explainability of AI Systems | Explainable AI | AI system decisions | Explainability requirements | Requirements analysis | Qualitative evaluation | Supports evidence/feedback/confidence output | Medium |
| 17 | Capstone Course SLR | Software engineering education | Literature on capstone projects | Taxonomy and findings | Systematic literature review | Literature synthesis | Domain background for project-based assessment | Medium |

## Detailed extraction from the 5 core papers

| Core Paper | What to extract | How it shapes our paper |
|---|---|---|
| **Rubric Is All You Need** | Question-specific rubric, PRE, CRE, EME, Leniency | Main theoretical basis for dynamic rubric and criterion-level AI review. |
| **TA Buddy** | AI-suggested criterion ratings, human accept/override, time saving, grade agreement | Main workflow reference for judge-facing AI suggestions. |
| **StepGrade** | Step-by-step evaluation of functionality, code quality, efficiency | Prompting strategy for structured evaluation. |
| **JorGPT** | Rubric in prompt, human comparison, MAE/R²/time reduction | Evaluation design and metrics. |
| **CodEv** | CoT-style prompting, ensemble, agreement testing, feedback quality | Reliability discussion and future work. |

## Final gap after adding the 4 papers

Existing studies strongly support LLM-based programming assessment, rubric-based grading, and human-in-the-loop review. However, they mainly focus on classroom programming assignments. The research gap for this project remains:

```text
How can these ideas be adapted into a programming competition / Hackathon workflow
where submissions are team-based, evidence comes from GitHub, rubrics are dynamic by round/track,
and final output must support judge decisions and ranking?
```

## Updated research positioning

The paper should not claim to build a new model. It should claim to design and evaluate a **workflow**:

```text
Problem statement + source code/GitHub diff + dynamic rubric
→ structured LLM evaluation
→ criterion-level suggested scores + evidence + feedback
→ judge accept/override
→ final score and ranking
```
