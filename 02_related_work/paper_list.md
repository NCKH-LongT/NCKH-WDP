# Paper List - Updated with 4 Additional References

## Research focus

**AI-assisted Source Code Evaluation and Ranking Based on Dynamic Rubrics in Programming Competitions**

The project application is a full Hackathon management system, but the **scientific paper only focuses on the AI-assisted source code evaluation module**. The AI component is treated as a supporting module: it suggests criterion-level scores, evidence, feedback, confidence, and judge questions; human judges make the final decision.

## Core papers for the scientific paper

| Core No | Paper | Authors | Year | Main Role in This Research | How It Is Used |
|---:|---|---|---:|---|---|
| 1 | **Rubric Is All You Need: Improving LLM-based Code Evaluation With Question-Specific Rubrics** | Pathak et al. | 2025 | Dynamic / question-specific rubric for LLM-based code evaluation | Main theoretical basis for using dynamic rubrics by event, round, track, and problem statement. Strongly supports criterion-level AI review. |
| 2 | **Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments: An Experience Report (TA Buddy)** | Nagakalyani et al. | 2025 | Human-in-the-loop AI-assisted source code grading | Main workflow reference: source code + problem + rubric → AI suggestions → human accept/override. |
| 3 | **StepGrade: Grading Programming Assignments with Context-Aware LLMs** | Akyash et al. | 2025 | Structured prompting / step-by-step code evaluation | Used to design the project prompt: evaluate each criterion separately with evidence and feedback. |
| 4 | **JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models** | Cisneros-González et al. | 2025 | Evaluation methodology and human comparison | Used for metrics such as MAE, correlation, time reduction, feedback quality, and instructor oversight. |
| 5 | **CodEv: An Automated Grading Framework Leveraging Large Language Models for Consistent and Constructive Feedback** | Tseng et al. | 2025 | Reliability, consistency, CoT-style evaluation, feedback quality | Used for discussion and future reliability features such as consistency checks and agreement testing. |

## Additional supporting papers added in this update

| No | Paper | Authors | Year | Source | Type | Use in Research |
|---:|---|---|---:|---|---|---|
| 15 | **Rubric Is All You Need: Improving LLM-based Code Evaluation With Question-Specific Rubrics** | Pathak et al. | 2025 | arXiv | **Core** | Added as the strongest new core paper. It directly supports dynamic/question-specific rubric design and criterion-level evaluation. |
| 16 | **The Future of Grading Programming Assignments in Education: The Role of ChatGPT in Automating the Assessment and Feedback Process** | Jukiewicz | 2024 | Thinking Skills and Creativity | Supporting | Empirical support that ChatGPT-style LLMs can grade programming tasks with correlation to teacher scores, but still need human verification. |
| 17 | **A Survey on LLM-as-a-Judge** | Survey paper | 2024/2025 | arXiv / survey | Method-supporting | Supports methodology around LLM-as-a-judge, reliability, bias, human alignment, and robustness. |
| 18 | **Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena** | Zheng et al. | 2023 | NeurIPS / arXiv | Optional supporting | Useful for background on LLM-as-a-judge, pairwise comparison, human agreement, and evaluation bias. Not code-specific. |

## Paper grouping after the update

### A. Core papers to use in the main scientific paper

1. **Rubric Is All You Need** — dynamic/question-specific rubric.
2. **TA Buddy** — human-in-the-loop AI-assisted source code grading.
3. **StepGrade** — structured / step-by-step prompting.
4. **JorGPT** — evaluation methodology and human-score comparison.
5. **CodEv** — reliability, consistency, and constructive feedback.

### B. Supporting papers

6. **The Future of Grading Programming Assignments** — empirical ChatGPT grading evidence.
7. **A Survey on LLM-as-a-Judge** — reliability and bias framework.
8. **Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena** — general LLM-as-a-judge foundation, optional.

### C. Lower-priority papers from the previous list

The remaining papers can stay in the literature matrix for completeness but should not dominate the scientific paper. They are useful for background, future work, or system context, not for the main contribution.

## Final decision

The scientific paper should be built around the following logic:

```text
Rubric Is All You Need  → why dynamic/question-specific rubrics matter
TA Buddy                → how AI suggestions are used by human graders
StepGrade               → how to design structured criterion-level prompts
JorGPT                  → how to evaluate AI scores against human scores
CodEv                   → how to discuss reliability and consistency
```

The application only needs to implement a practical subset:

```text
Dynamic rubric
+ source code / GitHub diff
+ structured LLM prompt
+ AI suggested criterion scores
+ evidence and feedback
+ judge accept/override
+ final score / ranking
```
