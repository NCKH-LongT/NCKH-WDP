# Problem Statement

## 1. Practical Problem (Vấn đề thực tế)
In the rapidly evolving landscape of scientific research, the volume of academic publications and journals is expanding exponentially. Faculty, students, and independent researchers face immense challenges in tracking domain-specific research trends, identifying rising topics, and grasping the evolution of academic domains over time. 

Current scholarly search engines (e.g., Google Scholar, Scopus) are designed primarily for **static, keyword-based document retrieval**. They present users with flat lists of thousands of search results but fail to provide a macro-level, intuitive visualization of publication trajectories, shifting keywords, or emergent research patterns. Consequently, researchers spend a disproportionate amount of time manually screening titles and abstracts just to determine whether a sub-topic is growing, stagnant, or oversaturated.

## 2. Importance of the Problem (Vì sao vấn đề này quan trọng?)
Addressing this information overload and analytical gap is critical for several stakeholders:
- **For Students:** It accelerates the thesis formulation phase, preventing them from choosing obsolete or over-researched topics.
- **For Lecturers & Researchers:** It ensures their research alignments match global funding trends and high-impact journal preferences, saving months of misdirected literature review.
- **For Academic Institutions:** It assists in monitoring institutional publication impact and strategic research planning.

Without automated trend analysis and multi-dimensional evaluation, identifying genuine **Research Gaps** remains a high-barrier, highly subjective task prone to human oversight.

## 3. Core System Objectives (Mục tiêu cốt lõi của hệ thống)
To bridge this gap, our system provides an automated data pipeline that continuously synchronizes scientific metadata via open APIs (OpenAlex, Semantic Scholar, Crossref). By implementing **Semantic Search, Retrieval-Augmented Generation (RAG), and Model Context Protocol (MCP)**, the platform transitions from simple metadata fetching to an intelligent ecosystem that automatically evaluates papers using explicit rubrics, identifies domain blind spots, and drafts validated research gap analytical reports.