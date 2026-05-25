# Literature Review Matrix - IOM-oriented Update

## Research Topic

**An IOM-based AI-assisted Source Code Evaluation Workflow for SEAL Hackathon Management Systems**

The goal of this matrix is not only to summarize papers, but also to extract their **Input–Output–Method (IOM)** contribution for the proposed system.

| No | Paper | Domain | Input | Output | Method / Model | Evaluation | IOM Contribution to Our Project | Relevance |
|---:|---|---|---|---|---|---|---|---|
| 1 | TA Buddy: Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments | Programming education / source code grading | Problem statement, source code, grading rubric | Suggested grade/rating per criterion, reasoning | Code Llama-based AI-assisted grading with human accept/override | Time reduction, grade agreement | Core workflow: AI suggestion + human judge accept/override | Very High |
| 2 | StepGrade: Grading Programming Assignments with Context-Aware LLMs | Programming assignment grading | Assignment, submitted code, context from previous steps | Grade and feedback for functionality, code quality, efficiency | Chain-of-Thought / structured prompting | Human evaluation, deviation comparison | Prompt design for criterion-by-criterion evaluation | Very High |
| 3 | JorGPT: Instructor-Aided Grading of Programming Assignments with LLMs | Programming education | Code submissions, rubric, instructor configuration | Grade and feedback | Multi-LLM grading with instructor oversight | MAE, R², correlation, time/cost | Evaluation metrics and human oversight justification | High |
| 4 | CodEv: Automated Grading Framework Leveraging LLMs | Programming grading and feedback | Code, problem, criteria, compile/test info | Scores, comments, feedback | CoT, LLM ensemble, agreement tests | Consistency, feedback quality | Optional consistency check and robust feedback | High |
| 5 | AI-based Automated Grading of Source Code of Introductory Programming Assignments | Source code grading | Problem statement, source code, instructor rubric | Automated grade/suggested assessment | LLM for code / rubric-based grading | AI-human grading comparison | Supports feasibility of rubric-based code grading | Very High |
| 6 | A Comparative Study of LLMs in Programming Education | LLM comparison | Student submissions, rubric | Grades, feedback | GPT/Claude/Gemini comparison | Accuracy, efficiency, feedback quality | Model selection and comparison | High |
| 7 | Systematic Comparison of LLMs for Automated Assignment Assessment | Programming education | Large set of submissions | Automated assessment outputs | 18 LLMs from multiple vendors | Correlation, variability, ICC | Reliability and model selection | High |
| 8 | Hands-on Analysis of LLMs for Auto Evaluation of Programming Assignments | Programming assessment | Programming assignments | AI grades | Multi-run LLM evaluation | Consistency, accuracy | Multi-run score stability idea | Medium-High |
| 9 | GradeHITL: LLM-based Automated Grading with Human-in-the-Loop | Rubric grading / short answers | Student answers, rubric, human expert inputs | Refined grading and scores | Human-in-the-loop rubric refinement | Accuracy improvement | Future work for dynamic rubric refinement | Medium |
| 10 | GradeOpt: LLM-Powered Automatic Grading Framework with Guidelines Optimization | Guideline optimization | Answers, grading guideline | Optimized guideline, score | Multi-agent grader-reflector-refiner | Accuracy, ablation | Future work: prompt/rubric optimization | Medium |
| 11 | BeGrading | Programming education feedback | Programming assignments and grades | Grades, enhanced feedback | Fine-tuned LLM | Feedback and grading evaluation | Future work after enough judge-score data | Medium |
| 12 | TRACE | Collaborative project assessment | GitHub repository/project data | Project assessment dashboard | Repository mining, analytics, AI support | Instructor comparison, time reduction | GitHub-based project evidence workflow | Medium-High |
| 13 | Transparency and Explainability of AI Systems | Explainable AI | AI system decisions | Explainability requirements | Requirements analysis | Qualitative evaluation | Supports evidence/feedback/confidence output | Medium |
| 14 | Capstone Course SLR | Software engineering education | Literature on capstone projects | Taxonomy and findings | Systematic literature review | Literature synthesis | Domain background for project-based assessment | Medium |

## Key Takeaways

1. **TA Buddy** is the closest workflow reference because it uses source code + rubric → AI suggested grades → human accept/override.
2. **StepGrade** is the strongest reference for structured prompting and criterion-level reasoning.
3. **JorGPT** provides useful evaluation metrics such as MAE, correlation and time reduction.
4. **CodEv** supports optional consistency checking and feedback quality improvement.
5. The proposed project adapts these ideas to SEAL Hackathon, where input comes from GitHub and rubrics are dynamic by season/round/track.

## Gap Identified from Matrix

Existing works mostly focus on classroom assignments. The proposed research extends the workflow to hackathon management with GitHub diffs, dynamic rubrics, judge accept/override and ranking-oriented evaluation.
