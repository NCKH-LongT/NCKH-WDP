# Research Gap Analysis

## 1. Limitations of Existing Solutions (Hạn chế của các nghiên cứu/hệ thống trước)
Based on our literature review of recent state-of-the-art platforms and academic frameworks, existing solutions fall short in three major technical and functional areas:

* **Static File Dependency vs. Automated Live Sync:** Traditional science mapping software (such as CiteSpace or VOSviewer) requires users to manually export data files (`.txt`, `.csv`) from commercial databases (Scopus, Web of Science). There is a lack of continuous, cloud-based background synchronization via open academic data catalogs (like OpenAlex) that offers real-time accessibility to modern researchers.
* **Keyword Matching vs. Hybrid Deep Evaluation:** Most analytical dashboards rely on simple keyword occurrence frequencies or basic Latent Dirichlet Allocation (LDA) topic modeling. These methods lack semantic awareness, struggle with academic synonyms/acronyms, and do not score papers through a multidimensional rubric (e.g., combining rule-based completeness with LLM-based trend alignment).
* **Descriptive Analytics vs. Actionable Gap Generation:** Existing tools tell the user *what has been published* (descriptive charts) but fail to reason *what is missing*. Platforms utilizing advanced LLMs or RAG for paper screening usually generate unverified, hallucinated summaries without an internal validation mechanism or structured programmatic verification layer.

## 2. Defined Research Gap (Khoảng trống nghiên cứu được xác định)
> **Research Gap:** While existing publication tracking systems successfully deliver macro-level statistical visualization or isolated text-clustering, there remains a distinct technological gap in combining **automated open API synchronization** with **RAG and MCP-driven multi-criteria evaluation** to systematically discover, verify, and report actionable research gaps for end-users.

## 3. Our Proposed Improvements & Contributions (Cải tiến và Đóng góp của nhóm)
Our project directly addresses these limitations through the following system contributions:
* **Dynamic Data Pipeline Architecture:** Implementing a system scheduler that pulls live metadata from OpenAlex, Semantic Scholar, and Crossref into a unified MongoDB schema, bypassing the need for manual user file uploads.
* **MCP-Driven Hybrid Scoring Engine:** Integrating a Model Context Protocol (MCP) tools layer (`search_papers`, `get_publication_trend`) allowing the LLM to contextually query internal data, executing a strict **6-tier structured criterion-by-criterion rubric assessment** (Relevance, Semantic Similarity, Trend Alignment, Metadata Quality, Recency, Research Gap Relevance).
* **Dual-Layer Automated Verification:** Overcoming LLM generation unreliability by adding a rule-based system verification step that automatically parses and validates the generated Markdown analytical reports before presentation or persistence.