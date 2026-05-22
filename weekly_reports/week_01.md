# Weekly Report - Week 01

## Group Information

- Class: SE1822
- Group: G05
- Leader: Nguyễn Chí Bảo
- Members: Nguyễn Thị Yến Nhi, Trần Minh Kiệt, Thái Minh Tuấn, Nguyễn Vũ Len

## Tasks Completed This Week

| Member | Task | Result |
|---|---|---|
| Nguyễn Chí Bảo | Chọn đề tài, viết topic proposal (mục 1–6, 9–10), thiết lập nhánh Git, tìm 1 paper | Hoàn thành topic proposal, tạo nhánh SE1822_G05, tìm paper [1] Jakob & Menendez 2021 |
| Nguyễn Thị Yến Nhi | Viết topic proposal (mục 7–8: AI Model + System Features), tìm 1 paper | Hoàn thành mục AI Model/Method + System Features, tìm paper [2] Wang et al. 2021 |
| Trần Minh Kiệt | Viết topic proposal (mục 11: Related Papers), tìm 1 paper | Hoàn thành bảng Related Papers, tìm paper [3] Amari et al. 2023 |
| Thái Minh Tuấn | Tạo cấu trúc thư mục theo README template, tìm 1 paper | Hoàn thành cấu trúc thư mục đầy đủ, tìm paper [4] Zhang et al. 2024 |
| Nguyễn Vũ Len | Viết topic revision log, review topic proposal, tìm 1 paper | Hoàn thành revision log, tìm paper [5] Wang, Li & Xie 2022 |

## Summary of Week 1

### Đề tài đã chọn
**AI-Enhanced Slot Allocation for Multi-Story Parking Building Management Systems**
(Phân bổ chỗ đỗ xe tăng cường AI cho hệ thống quản lý tòa nhà gửi xe nhiều tầng)

### Lĩnh vực
Smart Parking, Transportation Management, Resource Allocation Optimization, Applied AI.

### Tech Stack
- Backend: Node.js + Express.js
- Web Frontend: React.js
- Mobile App: React Native
- Database: MongoDB + Mongoose
- Realtime: Socket.IO

### Research Questions
- **RQ1:** Phân tầng theo loại xe ảnh hưởng thế nào đến hiệu quả sử dụng chỗ đỗ?
- **RQ2:** Phân bổ slot tự động có giảm thời gian tìm chỗ so với chọn tự do?
- **RQ3:** Nên ưu tiên tiêu chí nào khi phân bổ slot (MCDM)?
- **RQ4:** Thuật toán phân bổ có cải thiện tỷ lệ sử dụng giờ cao điểm?

### AI Components (mới bổ sung)
- Peak Hour Prediction (Random Forest / Gradient Boosting)
- Parking Duration Prediction (Linear Regression / Random Forest)

### Papers đã tìm được (5 bài)
| No | Paper | Người tìm |
|---|---|---|
| 1 | Jakob & Menendez (2021) — Differentiated Parking, Transportation Letters, Q2 | Nguyễn Chí Bảo |
| 2 | Wang et al. (2021) — Centralized Parking Control, TRC, Q1 | Nguyễn Thị Yến Nhi |
| 3 | Amari et al. (2023) — MCDM/TOPSIS for Parking, Sustainability, Q2 | Trần Minh Kiệt |
| 4 | Zhang et al. (2024) — Peak Demand Allocation/NSGA-II, Systems, Q1 | Thái Minh Tuấn |
| 5 | Wang, Li & Xie (2022) — Reservation-Aware Capacity, TRC, Q1 | Nguyễn Vũ Len |

## Deliverables

| File | Trạng thái |
|---|---|
| `01_topic_proposal/topic_proposal.md` | Hoàn thành |
| `01_topic_proposal/topic_revision_log.md` | Hoàn thành |
| Cấu trúc thư mục đầy đủ | Hoàn thành |

## Git Commits

| Commit ID | Message | Author |
|---|---|---|
| - | topic: create topic proposal with AI-enhanced parking system | Nguyễn Chí Bảo |
| - | topic: add AI model, system features, related papers | Nguyễn Thị Yến Nhi, Trần Minh Kiệt |
| - | docs: setup directory structure per README template | Thái Minh Tuấn |
| - | docs: add topic revision log | Nguyễn Vũ Len |

## Current Problems

- Mới tìm được 5 bài báo cơ bản — cần tìm thêm 5 bài nữa ở tuần sau.
- Chưa có dataset thực tế — dự kiến sử dụng seed data giả lập.
- Chưa xác định rõ baseline cho việc so sánh AI vs rule-based.

## Plan for Next Week

- Hoàn thành `02_related_work/search_keywords.md` — từ khóa tìm kiếm.
- Hoàn thành `02_related_work/paper_list.md` — mở rộng lên 10 papers.
- Bắt đầu tóm tắt paper (paper_summaries) — mỗi thành viên 1 paper.
- Tìm thêm 5 bài báo bổ sung cho đủ 10 papers.

## Questions for Instructor

- Dataset giả lập (seed data 500+ sessions) có được chấp nhận cho phần evaluation không?
- Đề tài sử dụng thuật toán tối ưu hóa (optimization algorithms) + AI prediction — có cần thêm model AI nào khác không?
