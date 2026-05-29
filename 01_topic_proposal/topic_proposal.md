## Scientific Journal Publication Trend Tracking System

---

## Group Information

Semester: SU26
Class: SE1822
Subject: WDP391
Group: 04
Contributors: Tran Dinh Phong, Pham Duc Thanh Phuong, Dang Thanh Tu, Ngo Nhat Minh

---

## 1. Proposed Title

Scientific Journal Publication Trend Tracking System

## 2. Application Domain

The proposed system belongs to the following fields:

- Academic Data Analytics and Visualization
- Scientific Literature Mining
- Research Trend Detection and Forecasting
- Information Retrieval from Bibliographic APIs
- Knowledge Discovery in Academic Databases
- Dashboard and Data Visualization for Research Intelligence

The project is positioned as a web-based platform that aggregates metadata from open academic APIs such as Semantic Scholar, OpenAlex, or Crossref to help researchers, lecturers, and students analyze publication trends across selected research fields. Rather than building a full-text search engine, the system focuses on trend visualization, keyword tracking, and research topic discovery — areas currently underserved by existing academic search platforms.

## 3. Problem Statement

The rapid growth in the volume of scientific publications has made it increasingly difficult for researchers, lecturers, and students to stay informed about evolving research trends. Academic search platforms such as Google Scholar, Scopus, and Web of Science are primarily designed for paper retrieval rather than trend intelligence. They allow users to find specific papers but do not offer structured tools for visualizing how research topics emerge, grow, or decline over time.

This gap creates several practical limitations:

- Researchers cannot easily observe how a topic evolves across years or identify which sub-fields are gaining or losing momentum.
- Keyword-based search interfaces do not provide visual or temporal context for understanding the research landscape.
- Lecturers and students must manually browse large collections to determine which topics are currently active or worth pursuing.
- There is no lightweight, accessible tool that combines paper metadata aggregation, trend analysis, and interactive visualization in a single platform.
- Existing commercial research intelligence tools are expensive and not accessible to individual researchers or academic institutions with limited resources.

Therefore, this project proposes a web platform that collects and processes publicly available paper metadata from free academic APIs, then applies statistical analysis and visualization techniques to surface publication trends, identify emerging topics, and support research discovery across selected domains such as Computer Science or Artificial Intelligence.

## 4. Target Users

- **Researcher**: Analyzes research trends in depth, tracks journals and specific keywords over time, discovers newly emerging topics, and reviews publication statistics across time periods.
- **Lecturer / Student**: Searches for reference papers, explores popular or trending research topics, saves papers or keywords of interest, and views a simplified trend dashboard for course or thesis guidance.
- **System Administrator**: Manages user accounts and access permissions, configures external API data sources, schedules and monitors data synchronization, and oversees system health.

## 5. Research Motivation for AI Integration

The primary motivation for incorporating analytical and AI-assisted features is to move beyond simple data aggregation and provide users with actionable research intelligence. Raw publication counts and keyword frequencies alone are insufficient for trend interpretation; the system needs to surface patterns that are not immediately obvious from browsing.

##### 5.1 Volume and Velocity of Academic Publications

The number of papers published annually in fields such as Computer Science and Artificial Intelligence has grown exponentially. Manually identifying which topics are rising, peaking, or declining across thousands of papers per year is not feasible without automated analysis. Statistical aggregation and trend modeling are necessary to make this information accessible and interpretable.

##### 5.2 Keyword Co-occurrence and Topic Clustering

Individual keywords rarely describe a research topic in isolation. Related terms tend to appear together and form topic clusters. Analyzing keyword co-occurrence patterns allows the system to group semantically related concepts into coherent research topics and present them as discoverable clusters on the trend dashboard, rather than requiring users to guess which keywords to search.

##### 5.3 Temporal Trend Analysis

Publication trends change over time in ways that reflect broader shifts in the research community. A topic that attracted few papers five years ago may now be one of the fastest-growing areas. Modeling these temporal dynamics — through time-series aggregation or lightweight trend scoring — enables the system to flag emerging topics and provide users with a forward-looking view of the research landscape.

##### 5.4 Personalized Research Discovery

Users have different research interests and prior knowledge. By allowing users to follow specific journals, keywords, or topics, and by tracking their bookmarking behavior, the system can provide personalized recommendations and notifications when new papers align with their interests. This reduces discovery time and improves the relevance of the information presented to each user.

## 6. Proposed Technical Approaches

##### 6.1 Trend Analysis

- **Time-Series Publication Counting**: Annual and quarterly paper counts per keyword or topic are aggregated from the collected metadata to produce trend curves. These trend curves form the basis for identifying growing, stable, or declining research areas.

- **Moving Average Smoothing**: A simple moving average is applied over publication counts to reduce noise from irregular publication patterns and highlight underlying trends more clearly.

- **Growth Rate Scoring**: A relative growth rate score is computed for each keyword or topic by comparing recent publication counts against historical baselines. Topics with consistently high growth rates are surfaced as emerging areas on the trend dashboard.

##### 6.2 Keyword and Topic Analysis

- **Keyword Co-occurrence Graph**: Co-occurrence relationships between keywords that appear together in paper metadata are extracted and stored as a graph structure. This graph is used to generate topic clusters and to power the keyword relationship visualization on the dashboard.

- **TF-IDF-Based Keyword Ranking**: Term frequency and inverse document frequency weighting is applied across paper abstracts and keyword fields to rank the most representative and distinctive keywords for each research area and time period.

##### 6.3 Data Collection and Synchronization

- **External API Integration**: Paper metadata is retrieved periodically from free academic APIs including Semantic Scholar, OpenAlex, or Crossref. The system stores normalized metadata records including title, abstract, keywords, publication year, authors, and journal name.

- **Scheduled Synchronization**: A background job runs on a configurable schedule (daily or weekly) to pull newly published or updated records from the configured API sources and update the local database without requiring manual intervention.

## 7. Core System

##### 7.1 User-Facing Web Application

- **User Authentication and Authorization**: The system supports account registration, login, and role-based access control. Researcher and Lecturer/Student roles have access to trend analysis and paper discovery features, while the Administrator role has access to system configuration and user management.

- **Paper Search**: Users can search for papers by keyword, author name, or journal title. Search results display paper titles, abstracts, authors, publication years, and journal names sourced from the synchronized metadata database.

- **Paper Detail View**: Each paper has a dedicated detail page showing its full metadata including abstract, keywords, authors, journal, and publication year, along with links to the original source when available.

- **Trend Dashboard**: An interactive dashboard visualizes publication trends over time for selected keywords, topics, or journals. Charts include annual publication counts, growth rate trends, and keyword frequency over time using line charts and bar charts.

- **Trending Topics View**: A dedicated section surfaces the most active and fastest-growing research topics based on recent publication activity and growth rate scores. Users can browse trending topics by field or time period.

- **Keyword Relationship Visualization**: A visual graph or cluster map displays co-occurrence relationships between keywords, allowing users to explore how related research concepts are connected and identify topic neighborhoods.

- **Bookmarks**: Users can bookmark papers or keywords they want to revisit. Bookmarked items are accessible from a personal library page.

- **Follow Journals and Topics**: Users can follow specific journals or research topics to receive notifications when new papers matching their interests are detected during the next synchronization cycle.

- **Notifications**: The system delivers in-app notifications informing users of newly published papers in their followed journals or topics following each scheduled data update.

- **Analytical Report Generation**: Users can generate simple downloadable reports summarizing publication trends for a selected keyword or topic over a specified time range, exported as a PDF or CSV file.

##### 7.2 Administrator Panel

- **User Management**: The administrator can view, activate, deactivate, and assign roles to user accounts.

- **API Data Source Configuration**: The administrator can configure which external academic APIs are enabled, set API keys or request parameters, and define the target research fields or domains from which data is collected.

- **Data Synchronization Management**: The administrator can view the status of the last synchronization run, trigger a manual sync, and review logs of data ingestion activity.

- **System Monitoring**: A simple system overview page shows the number of papers, journals, and keywords in the database, along with synchronization history.

##### 7.3 Backend and Data Pipeline

- **Metadata Ingestion Pipeline**: A scheduled pipeline fetches paper metadata from the configured external APIs, normalizes the data into a unified schema, deduplicates records by DOI or title hash, and stores them in the application database.

- **Trend Computation Layer**: After each synchronization cycle, a background computation task updates keyword publication counts by year, recalculates growth rate scores, and refreshes co-occurrence graph data to reflect the latest state of the dataset.

- **REST API**: The backend exposes a REST API consumed by the web frontend. Endpoints support paper search, trend queries, bookmark management, notification retrieval, and admin operations.

## 8. System Constraints and Assumptions

- The system uses publicly available metadata from academic APIs such as Semantic Scholar, OpenAlex, or Crossref through their free-tier access.
- Only paper metadata is collected, including title, abstract, keywords, publication year, authors, and journal name. Full-text content is not processed due to copyright and storage limitations.
- Collected data is assumed to be valid, reasonably structured, and consistently available from the configured third-party APIs.
- The system analyzes data within a selected set of research domains (for example, Computer Science or Artificial Intelligence) to manage scope and reduce dataset complexity.
- Data updates follow a periodic schedule (daily or weekly) and do not require real-time synchronization.
- The platform does not perform full-text indexing or semantic embedding of paper content in the initial version.

## 9. Expected Results

The expected outcomes of this project include:

- A functional web platform that aggregates academic paper metadata from open APIs and presents publication trends through interactive visualizations.

- A trend analysis layer that surfaces growing and emerging research topics based on historical publication data, keyword frequency, and growth rate scoring.

- A personalized research discovery experience allowing users to follow topics and journals, bookmark papers, and receive notifications about new publications relevant to their interests.

- A keyword relationship visualization that helps users explore topic neighborhoods and understand how research concepts are interconnected.

- A demonstration of how open academic data APIs can serve as the data foundation for a lightweight but useful research intelligence tool accessible to individual researchers and academic communities without subscription fees.
