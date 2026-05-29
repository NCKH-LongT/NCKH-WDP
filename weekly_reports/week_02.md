# Weekly Report - Week 02

## Group Information

Class: SE1823
Group: G09
Project: AR-based Infrastructure Monitoring and Maintenance System
Leader: [Phan Võ Đức Huy]
Members:

- [Phan Võ Đức Huy] - [Leader]
- [Nguyễn Khánh Ngân] - [Member]
- [Lê Trần Anh Duy] - [Member]

## Tasks Completed This Week

| Member              | Task                                                                                              | Result     |
| ------------------- | ------------------------------------------------------------------------------------------------- | ---------- |
| [Phan Võ Đức Huy]   | Vẽ Conceptual ERD, Physical ERD, hỗ trợ tìm các nghiên cứu và keywords                            | Hoàn thành |
| [Lê Trần Anh Duy]   | Hoàn thiện usecase diagram, và cập nhật topic proposal                                            | Hoàn thành |
| [Nguyễn Khánh Ngân] | Tổng hợp các nghiên cứu và viết paper summaries, literature matrix, phác thảo system architecture | Hoàn thành |

## Git Commits

| Commit ID | Message                                                                          | Author            |
| --------- | -------------------------------------------------------------------------------- | ----------------- |
| 335f102   | review: add paper summaries, research questions, and literature review materials | [Phan Võ Đức Huy] |
| fa17977   | fix: revise wording                                                              | [Phan Võ Đức Huy] |

## Current Problems

- **Chưa chắc AI có đang “quá căng” so với phạm vi triển khai**: trong `01_topic_proposal/topic_proposal_vn.md`, nhóm đã định vị **AR là lớp tương tác cốt lõi**, còn **AI là lớp mở rộng phân tích** (phát hiện bất thường / insight dự đoán) trong **môi trường data center mô phỏng**. Nếu cố triển khai quá nhiều kỹ thuật AI cùng lúc thì rủi ro dàn trải và khó đảm bảo demo end-to-end.
- **Cần chốt baseline AI tối thiểu** để làm được luồng hoàn chỉnh: ưu tiên rule-based/threshold + anomaly score cơ bản; các mô hình nâng cao chỉ để mô tả hướng nghiên cứu hoặc làm optional.
- **Architecture/data-flow chưa “đóng đinh” ở mức implementable**: nguồn telemetry, cách tạo tình huống bất thường trong mô phỏng, schema dữ liệu tối thiểu, và mapping marker -> node/service cho AR vẫn chưa được chuẩn hoá.
- **Folder `03_problem_and_gap/` mới là skeleton** nên Problem Statement / Research Gap / Research Questions chưa được viết cụ thể theo đề tài AR + AI monitoring & maintenance.
- Phần actor đang không rõ là nên có actor người bán không, còn phía người mua đang suy nghĩ là chỉ có 2 actor là admin, và technician (hoặc là có technican, noc engineer, IT admin)

## Plan for Next Week

### Need review

- ERD
- Use case

### 1) Cải thiện scope & architecture (hướng PoC)

- Rà soát lại scope theo proposal: **AR-first** (bắt buộc), **AI-optional** (mở rộng nghiên cứu), demo trên **Docker-based simulated data center**.
- Chốt **MVP end-to-end**: Telemetry (Docker nodes/containers) -> Backend (ingest/store) -> Dashboard (visualize/alerts) -> AR client (marker -> overlay telemetry + hướng dẫn thao tác).
- Chốt **baseline AI**: anomaly detection mức tối thiểu (rule-based/threshold + scoring), định nghĩa đầu ra AI (anomaly score, warning label, insight ngắn) để tích hợp vào dashboard/AR.

### 2) Làm phần `03_problem_and_gap/`

- Viết `03_problem_and_gap/problem_statement.md`: bối cảnh, workflow hiện tại, pain points (dashboard tách rời không gian vật lý), stakeholders, impact, và “Need for AI support” ở mức hợp lý.
- Viết `03_problem_and_gap/research_gap.md`: tổng hợp hướng tiếp cận liên quan (AR monitoring, dashboard observability, AIOps/anomaly), nêu limitations và khoảng trống mà nhóm nhắm tới.
- Viết `03_problem_and_gap/research_questions.md`: chốt RQ bám sát đề tài (ví dụ: hiệu quả AR trong truy xuất ngữ cảnh; khả năng phát hiện bất thường trong telemetry mô phỏng; tác động của AI-insight lên quyết định bảo trì).

### 3) Bắt đầu hoàn thiện SRS/SDS + setup project để coding

- **SRS (phần đầu)**: mục tiêu hệ thống, actors, use cases chính, functional/non-functional requirements, acceptance criteria cho demo.
- **SDS (phần đầu)**: component diagram, data flow, database schema tối thiểu, API contracts (ingest telemetry / query node / alerts), logging & traceability.
- **Setup project**: khởi tạo skeleton repo cho backend + dashboard + telemetry collector + tài liệu, dựng Docker Compose môi trường mô phỏng để bắt đầu coding pipeline telemetry.

### Thiết kế hệ thống

- Phác thảo system architecture tổng thể cho hệ thống, bao gồm dashboard, backend, telemetry flow, AR client và lớp AI mở rộng.
- Chốt bộ telemetry tối thiểu cần thu thập như CPU, memory, network, service status và log sự kiện để phục vụ cả dashboard lẫn AR.

### Prototype và chuẩn bị demo

- Phân tích và lên kế hoạch làm prototype cho hai luồng quan trọng nhất: Docker telemetry -> dashboard và marker recognition -> AR overlay trên node mô phỏng.

## Questions for Instructor

- Với framing hiện tại (AR là lõi, AI là lớp mở rộng; PoC trên môi trường mô phỏng), instructor có đồng ý mức độ AI chỉ cần ở baseline + hướng mở rộng nghiên cứu không?
