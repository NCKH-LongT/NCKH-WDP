# Topic Proposal

## 1. Group Information

- Class: SE1823
- Group: G03
- Leader: Bùi Đức Anh
<<<<<<< Updated upstream
- Members: Lương Khánh Toàn, Lê Văn Kiên, Nguyễn Khánh Hưng,Tăng Thùy Thụy
=======
- Members:
>>>>>>> Stashed changes

## 2. Proposed Title

English title:

**Personalized Career Orientation & Learning Roadmap Platform for Software Engineering Students**

Vietnamese title:

**Nền tảng định hướng nghề nghiệp và xây dựng lộ trình học tập cá nhân hóa cho sinh viên ngành Công nghệ phần mềm**

## 3. Application Domain

The project belongs to the following application domains:

- Artificial Intelligence
- Education Technology
- Career Orientation System
- Learning Analytics
- Software Engineering Education
- Student Support System
- E-Portfolio Management

The system is designed to support Software Engineering students in career orientation, skill gap analysis, personalized learning roadmap generation, job market trend awareness, and GitHub-based portfolio development.

## 4. Problem Statement

Many Software Engineering students face difficulties in preparing for specific career roles in the software industry. Although students may learn many general subjects at university, they often do not know which career path is suitable for their current skills, interests, academic background, and project experience.

The main practical problems include:

1. Students have difficulty identifying a suitable career path such as Backend Developer, Frontend Developer, Mobile Developer, DevOps Engineer, Cloud Engineer, Data Engineer, or AI Engineer.
2. University curricula may not update quickly enough to match current industry requirements.
3. Students are overwhelmed by many online roadmaps and do not know which roadmap fits their current level.
4. Students may not clearly understand the gap between their current skills and the skills required by a target career role.
5. Students often build random projects that do not form a coherent portfolio story for potential employers.
6. Job market trends change quickly, but students rarely use job posting data to decide which skills should be learned first.

Traditional career guidance methods are often general, not personalized, and not updated according to real labor market demand. As a result, students may learn unsuitable technologies, lack practical skills, and face difficulty when applying for internships or entry-level jobs.

Therefore, a personalized AI-based platform is needed to help Software Engineering students identify suitable career paths, analyze skill gaps, generate learning roadmaps, and build professional e-portfolios based on their GitHub projects.

## 5. Motivation

This topic is important because career orientation and job readiness are major concerns for Software Engineering students. Choosing a suitable career path early can help students focus their learning, prepare better projects, and improve their chances of getting internships or entry-level jobs.

Traditional online roadmaps are useful, but they are usually static and do not consider each student’s current skills, academic background, GitHub projects, or target career role. In addition, these roadmaps are not always updated according to real job market trends.

By integrating AI into the system, students can receive more personalized and practical support. AI can analyze student profiles, compare current skills with career role requirements, summarize GitHub repositories, identify missing skills, and recommend learning priorities based on market demand.

The system does not replace academic counselors or industry mentors. Instead, it acts as an intelligent support tool that helps students make better learning and career decisions.

## 6. Target Users

The main users of the system are:

1. **Software Engineering Students**

   Students use the system to discover suitable career paths, analyze skill gaps, follow personalized learning roadmaps, track progress, and build e-portfolios.

2. **Academic Counselors**

   Academic counselors use the system to monitor student progress, understand student skill gaps, and provide better academic and career guidance.

3. **Industry Mentors**

   Industry mentors use the system to give practical feedback on career paths, technical skills, project portfolios, and industry expectations.

4. **Administrators**

   Administrators manage users, system data, skill frameworks, roadmap content, AI API configuration, and third-party service integration.

## 7. Proposed AI Model / Method

The project does not aim to build or train a completely new AI model from scratch. Instead, it focuses on integrating existing AI models and AI-based methods into a practical student support platform.

The proposed AI models and methods include:

- **Large Language Model API**

  The system may use GPT, Gemini, or similar LLM APIs for the AI Virtual Mentor module. The LLM will support career-related question answering, roadmap explanation, and personalized learning advice.

- **Retrieval-Augmented Generation**

  RAG can be used to improve chatbot responses by retrieving relevant information from career role requirements, skill trees, learning resources, job trend data, and student profiles.

- **Natural Language Processing**

  NLP will be used to process user questions, analyze job descriptions, extract skills from recruitment posts, and summarize GitHub README files.

- **Embedding Model / Semantic Similarity**

  Embedding-based similarity can be used to compare student skills with target career role requirements and identify skill gaps.

- **Recommendation Model**

  Recommendation methods will be used to suggest suitable career paths, learning roadmaps, technical skills, and learning resources.

- **Keyword Frequency Analysis**

  Keyword frequency analysis will be used in the Market Pulse module to identify trending technologies from job postings.

- **GitHub README Analysis**

  AI will be used to analyze README files, extract project objectives, identify tech stacks, and generate portfolio summaries.

## 8. System Features

The main features of the system are:

1. **AI Virtual Mentor**

   A natural language chatbot that allows students to ask career-related questions and receive personalized technical career advice.

2. **Dynamic Learning Roadmap**

   The system allows students to select a target career role and automatically generates a hierarchical skill tree with prioritized learning steps and curated learning resources.

3. **Skill Gap Analysis**

   The system compares the student’s current skills with the required skills of the selected career role and generates a report showing missing skills and urgent learning priorities.

4. **Market Pulse**

   The system collects job posting data from IT job portals, analyzes skill keywords in job descriptions, and displays trend charts for in-demand technologies.

5. **E-Portfolio Management**

   The system allows students to link their GitHub account, synchronize public repositories, summarize README files, extract tech stacks, and generate a shareable portfolio URL.

6. **User Management**

   The system supports authentication using Email/Password and Google OAuth 2.0. It also stores chat history, skill assessments, roadmap progress, and portfolio data.

## 9. Expected Contribution

The expected contributions of the project are:

1. A personalized AI-based career orientation platform for Software Engineering students.

2. A skill gap analysis mechanism that maps student skills to specific career role requirements.

3. A dynamic learning roadmap generation method based on student profile, target career role, and market skill demand.

4. A Market Pulse module that analyzes job posting data to identify trending Software Engineering skills.

5. An AI-supported e-portfolio system that summarizes GitHub repositories and helps students present project experience more clearly.

6. A practical integration of LLM, NLP, semantic matching, recommendation methods, and GitHub data in a student support system.

## 10. Evaluation Plan

The system will be evaluated using both technical metrics and user-centered evaluation.

- **Dataset:**

  Student profiles, self-declared skills, GitHub repositories, README files, career role skill requirements, and job descriptions collected from IT job portals such as LinkedIn, TopCV, or similar sources.

- **Baseline:**

  Static online roadmaps, manual career guidance, keyword-based skill matching, or LLM-only chatbot without retrieval and personalization.

- **Metrics:**

  Recommendation relevance, Precision@K, Recall@K, skill matching accuracy, response time, roadmap completion rate, and user satisfaction.

- **Expert evaluation:**

  Academic counselors or industry mentors can review the generated roadmaps, skill gap reports, and portfolio summaries to evaluate their usefulness, correctness, and practical value.

- **User survey:**

  Software Engineering students can evaluate the system based on ease of use, usefulness, roadmap clarity, career guidance quality, portfolio usefulness, and overall satisfaction.

## 11. Related Papers

| No  | Title                                                                                                                                                                                   | Year | Source                                                        | Link / DOI                              |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---: | ------------------------------------------------------------- | --------------------------------------- |
| 1   | C3-IoC: A Career Guidance System for Assessing Student Skills using Machine Learning and Network Visualisation                                                                          | 2023 | International Journal of Artificial Intelligence in Education | Springer Paper Link                     |
| 2   | SkillGap AI: An AI-Powered Career Guidance Platform                                                                                                                                     | 2026 | International Journal For Multidisciplinary Research          | IJFMR Paper Link                        |
| 3   | A Review on AI-Based Chatbots for Personalized Career Guidance                                                                                                                          | 2025 | IJARCST                                                       | DOI: 10.15662/IJARCST.2025.0805011      |
| 4   | Reducing Career Path Anxiety among Vocational Students with an AI-Driven Career Guidance System Integrating Skills Mapping, Adaptive Mentoring, and Real-Time Labor Market Intelligence | 2025 | Zenodo Preprint                                               | https://doi.org/10.5281/zenodo.17355217 |
| 5   | Personalized Learning Path Recommendation Based on Learner Profile and Knowledge Graph                                                                                                  | 2025 | Computing and Informatics                                     | DOI: 10.31577/cai_2025_4_983            |
