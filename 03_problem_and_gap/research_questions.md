# Research Questions

## Main Research Question

How can a Retrieval-Augmented Generation (RAG)-based AI system be integrated into a centralized academic document management platform to improve the accuracy, efficiency, and usability of knowledge retrieval for university students?

## Sub Research Questions

**RQ1 — RAG Effectiveness (Accuracy & Groundedness)**
How effectively does a RAG-based pipeline improve the accuracy and groundedness of question answering over student-uploaded academic documents compared to a standard LLM baseline?

> _Đo lường: Faithfulness, Answer Relevancy, Citation Precision (RAGAS framework); so sánh RAG vs. vanilla LLM (GPT-4o mini / Gemini Flash)._

**RQ2 — Technical Design (Chunking & Retrieval Optimization)**
What text chunking strategy and embedding configuration yield the highest retrieval relevance for heterogeneous academic document formats (PDF, PPTX, DOCX) in a student knowledge management system?

> _Đo lường: MRR (Mean Reciprocal Rank), Recall@k; so sánh fixed-size chunking vs. sentence-based vs. semantic-based chunking._

**RQ3 — User-Centered Outcome (Usability & Cognitive Load)**
To what extent does integrating AI-powered semantic search and auto-summarization into a centralized document platform reduce the time and cognitive effort required for university students to locate and comprehend academic materials?

> _Đo lường: Task Completion Time, NASA-TLX cognitive load score, SUS (System Usability Scale); thực hiện qua user study với sinh viên đại học._
