# Literature Review Matrix

| Paper | Research Problem | AI / Method | Rubric / Criteria | Context | Evaluation Method | Lessons for SEAL | Priority |
|---|---|---|---|---|---|---|---|
| Implementing AI-Based Code Review Automation: A Case Study in Academic Software Development (2025) | Reduce review time and improve consistency in academic code review | GPT-4 + static analysis tools (Pylint, Flake8, Checkstyle) | Coding standards and review criteria | 150 student projects / 450 assignments | Issue detection accuracy, review time reduction, student feedback | Useful pipeline: static analysis → GPT-4 → feedback → instructor validation. Shows AI can reduce review time but still requires human-in-the-loop validation. | Medium |
| TRACE: AI-Assisted Assessment of Collaborative Projects in Computer Science Education (2026) | Fair assessment of collaborative software projects and individual contributions | Repository mining, NLP, GitHub analytics, static analysis | Quality metrics with configurable weights | GitHub Classroom and collaborative software projects | Pearson correlation with instructor grades, grading time reduction, student perception | Useful for repository tracking, dashboard analytics, project quality metrics, and GitHub-based evaluation workflows. | Medium |
| Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments (SIGCSE 2025) | Improve grading efficiency for introductory programming assignments | Code Llama fine-tuned for grading | Explicit rubric with criterion-based scoring | Introductory programming assignments | Compare AI-assisted grading vs manual grading | Important workflow: source code + rubric → AI suggested score → human accept/override → final grade. Very similar to judge workflow in SEAL. | High |
| JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models (2025) | Support instructors in grading programming assignments using LLMs | LLM-based instructor-aided grading | Customizable rubric: correctness, documentation, efficiency, readability, requirement compliance | Undergraduate programming education | Statistical comparison using adjusted R² and MAE | Provides useful rubric criteria for SEAL and supports comparison between AI-generated scores and human evaluation. | Medium |
| A Systematic Comparison of Large Language Models for Automated Assignment Assessment in Programming Education (2026) | Compare multiple LLMs for automated grading | Comparison of 18 LLMs (Claude, Gemini, GPT-4, GPT-5, DeepSeek) | No explicit rubric | 6,000+ programming submissions | Statistical tests, clustering, ICC, grade agreement | Useful for benchmarking AI models, validating AI-human agreement, and justifying why AI should support — not replace — judges. | Medium |

## Overall Findings

### Common Research Trends

Most recent studies focus on:

- AI-assisted grading,
- repository mining,
- rubric-based evaluation,
- LLM-assisted source code analysis,
- human-in-the-loop evaluation,
- reducing grading time while maintaining consistency.

### Research Gaps

Current studies mainly focus on:

- classroom assignments,
- educational grading,
- course projects.

Few studies focus specifically on:

- programming competitions,
- hackathon evaluation,
- realtime repository monitoring,
- GitHub webhook integration,
- AI-assisted competition management systems.

### Contribution Opportunity for SEAL

SEAL can contribute by combining:

- hackathon management,
- GitHub integration,
- repository tracking,
- webhook-based monitoring,
- rubric-based AI review,
- judge-assisted evaluation workflows.

The system also extends previous research into the context of:

- programming competitions,
- collaborative hackathon projects,
- realtime evaluation support.