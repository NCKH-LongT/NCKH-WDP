# Weekly Report - Week 01

## Group Information

**Class:** SE1823

**Group:** 04

**Leader:** Mai Thị Thanh Ngân

**Members:**
- Nguyễn Quang Vinh
- Vũ Tiến Đạt
- Lê Nguyễn Xuân Lộc

---

## Tasks Completed This Week

| Member | Task | Result |
|--------|------|--------|
| Mai Thị Thanh Ngân | Điều phối nhóm, xác định hướng đề tài và phạm vi hệ thống | Chốt đề tài: AI-Based Rapid Source Code Evaluation System Using Predefined Rubrics for Programming Competitions |
| Nguyễn Quang Vinh | Phân tích bối cảnh cuộc thi lập trình và các vấn đề quản lý đánh giá source code | Xác định các vấn đề chính: thời gian chấm lâu, phụ thuộc vào kinh nghiệm cá nhân, khó kiểm tra toàn bộ repository trong thời gian ngắn |
| Vũ Tiến Đạt | Phân tích các nhóm người dùng và chức năng hệ thống | Xác định năm nhóm người dùng chính: Event Coordinator, Judge, Team Leader, Team Member, Admin |
| Lê Nguyễn Xuân Lộc | Đề xuất hướng công nghệ và tích hợp GitHub Automation với AI | Xác định tech stack MERN, GitHub API automation, LLM integration cho AI-assisted code grading |
| Cả nhóm | Hoàn thiện topic proposal | Hoàn thành `01_topic_proposal/topic_proposal.md` theo template với mô tả đầy đủ hệ thống SEAL |
| Cả nhóm | Thiết lập cấu trúc repository và nhánh làm việc | Làm việc trên nhánh `SE1823_G04` và tổ chức thư mục theo hướng dẫn trong README.md |
| Cả nhóm | Phân tích problem statement và research gap | Hoàn thành `03_problem_and_gap/problem_statement.md` và `03_problem_and_gap/research_gap.md` |

---

## Git Commits

| Commit ID | Message | Author |
|-----------|---------|--------|
| - | chore: initialize project structure | Mai Thị Thanh Ngân |
| - | docs: add group information and topic direction | Nguyễn Quang Vinh |
| - | docs: draft AI-based source code evaluation system topic proposal | Vũ Tiến Đạt |
| - | docs: define problem statement and research gap | Lê Nguyễn Xuân Lộc |
| - | docs: complete topic proposal and system overview | Mai Thị Thanh Ngân |

---

## Current Problems

1. **Chưa có dataset thực tế:** Nhóm cần dữ liệu từ các cuộc thi lập trình thực tế hoặc dữ liệu giả để kiểm tra hệ thống trong giai đoạn đánh giá.

2. **Độ chính xác của AI-assisted grading:** Cần xác định mức độ mà AI có thể đề xuất điểm một cách chính xác mà không cần quá nhiều can thiệp từ giám khảo.

3. **Phạm vi hệ thống rộng:** Hệ thống kết hợp nhiều module: competition management, GitHub automation, AI grading, rubric động, ranking - cần xác định scope cho giai đoạn này.

4. **Chưa xác định baseline:** Cần định rõ baseline cho AI model (sử dụng LLM sẵn có như OpenAI API, hay huấn luyện model riêng).

5. **Dynamic Rubric complexity:** Rubric động theo database yêu cầu thiết kế schema phức tạp - chưa có proof-of-concept.

---

## Plan for Next Week

1. **Tìm kiếm bài báo liên quan:**
   - Papers về LLM/AI trong automated code grading
   - Papers về GitHub automation và webhook
   - Papers về dynamic rubric management
   - Papers về hackathon management systems

2. **Xây dựng danh sách search keywords:**
   - "AI-assisted code grading"
   - "Source code evaluation rubric"
   - "GitHub webhook automation"
   - "LLM for programming assignment evaluation"
   - "Hackathon management system"

3. **Phân loại paper theo nhóm:**
   - Related Systems: hackathon platforms, code evaluation tools
   - AI/ML Methods: LLM prompting strategies, code analysis techniques
   - Domain Application: education, competitions, software quality

4. **Chuẩn bị literature review:**
   - Bắt đầu draft `02_related_work/literature_review_matrix.md`
   - Xác định các AI methods phù hợp cho đề tài (LLM prompting, static analysis, etc.)

5. **Làm rõ technical baseline:**
   - Xác định API providers (OpenAI/Anthropic) hoặc model local
   - Draft `04_proposed_system/ai_model_integration.md`
   - Xác định quy trình GitHub webhook -> AI analysis -> Judge scoring

---

## Questions for Instructor

1. Nhóm nên ưu tiên sử dụng OpenAI API, Anthropic API, hay huấn luyện model local từ đầu?

2. Với phạm vi hệ thống rộng (GitHub automation + dynamic rubric + AI grading), nhóm có nên thu hẹp scope cho giai đoạn đầu (ví dụ: chỉ tập trung vào AI code grading mà không có dynamic rubric) không?

3. Nhóm có thể sử dụng mã nguồn từ các submission cuộc thi tham khảo (hoặc synthetic code samples) để đánh giá AI model không?

4. Metric nào quan trọng nhất cho hệ thống: độ chính xác của AI suggestion, thời gian xử lý, hay ranking alignment với judge thực tế?

---

## Notes

- Repository branch: `SE1823_G04`
- Project folder structure organized theo hướng dẫn với 5 phases: topic proposal → related work → problem & gap → proposed system → methodology
- Sẽ tiếp tục cập nhật tiến độ hàng tuần
