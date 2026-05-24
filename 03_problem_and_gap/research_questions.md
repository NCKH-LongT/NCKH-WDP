# Research Questions (RQs)

To guide the implementation, evaluation, and empirical assessment of the **AI-assisted Scientific Publication Trend Analysis System**, the project focuses on answering the following four research questions:

---

### **RQ1. (Technical Accuracy & Semantic Capability)**
> *How accurately can the proposed semantic search and RAG framework categorize and score publication metadata compared to traditional rule-based or keyword-matching mechanisms?*
* **Focus:** Evaluates the accuracy of the semantic search module and the reliability of the LLM-assigned scores (Relevance, Semantic Similarity) against a baseline of traditional strict keyword queries.

### **RQ2. (AI Tool Interoperability & Grounding)**
> *To what extent does the integration of Model Context Protocol (MCP) tools minimize LLM hallucinations when generating research gap analytical reports?*
* **Focus:** Measures how effectively the MCP tools layer (`get_publication_trend`, `find_similar_papers`) grounds the AI output in real internal database numbers rather than allowing the model to fabricate external academic statistics.

### **RQ3. (System Reliability & Verification)**
> *How effective is the dual-layer automated verification step in filtering out corrupted, incomplete, or logically inconsistent AI-generated analytical evaluation scores?*
* **Focus:** Investigates the performance of the system logic that screens the JSON outputs and Markdown reports from the AI service before saving them to the database or delivering them to Researchers/Students.

### **RQ4. (User Workflow Efficiency & Actionability)**
> *How much time can the system save users during the initial literature review and research gap discovery phase compared to manual analysis on standard academic search engines?*
* **Focus:** Measures user experience (UX) and efficiency gains for both students and lecturers, tracking the reduction in hours spent aggregating multi-year trend patterns manually.