# Topic Revision Log

---

## Version History

| Version | Date       | Author(s)         | Summary of Changes                        |
|---------|------------|-------------------|-------------------------------------------|
| v1.0    | 2026-05-29 | Tran Dinh Phong   | Initial proposal draft created           |

---

## v1.0 — 2026-05-29

### Revision Reason

Initial submission of topic proposal for SU26SWP06 — Scientific Journal Publication Trend Tracking System.

### Updated Scope

- Defined system as a web platform aggregating academic metadata from open APIs (Semantic Scholar, OpenAlex, Crossref).
- Identified three target user roles: Researcher, Lecturer/Student, System Administrator.
- Scoped core features: paper search, trend dashboard, trending topics view, keyword co-occurrence visualization, bookmarks, follow journals/topics, notifications, analytical report export.
- Scoped technical approaches: time-series publication counting, moving average smoothing, growth rate scoring, TF-IDF keyword ranking, keyword co-occurrence graph.
- Defined system constraints: metadata only (no full-text), selected domains (e.g., CS or AI), periodic sync (daily/weekly), free-tier API access only.

### Feedback From Instructor

*(Pending — awaiting instructor review)*

### Next Revision Notes

- Await feedback from instructor before proceeding to architecture design.
- Confirm final choice of primary external API (Semantic Scholar vs. OpenAlex vs. Crossref).
- Clarify whether keyword co-occurrence graph is in MVP or extended scope.
