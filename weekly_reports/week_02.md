# Weekly Report - Week 02

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
| Mai Thị Thanh Ngân | Điều phối tiến độ related work và kiểm tra sự phù hợp với topic proposal | Xác định các hướng paper cần tìm gồm LLM code grading, GitHub automation, rubric management và hackathon platforms |
| Nguyễn Quang Vinh | Tìm kiếm paper về LLM/AI trong code grading và automated evaluation | Bổ sung các paper liên quan đến code quality assessment, automated feedback generation và programming assignment evaluation |
| Vũ Tiến Đạt | Xây dựng search keywords và search queries | Hoàn thành `02_related_work/search_keywords.md` với các nhóm keyword theo AI code grading, GitHub automation, rubric management và hackathon systems |
| Lê Nguyễn Xuân Lộc | Phân loại paper theo nhóm nghiên cứu | Hoàn thành `02_related_work/paper_list.md` theo nhóm Related Systems (hackathon/code evaluation platforms), AI/ML Methods (LLM prompting, static analysis) và Domain Application Papers |
| Cả nhóm | Chuẩn bị literature review | Tạo bản khung `02_related_work/literature_review_matrix.md` để phục vụ phân tích sâu ở các tuần tiếp theo |
| Cả nhóm | Xác định baseline cho AI model | Quyết định sử dụng LLM API (OpenAI/Claude) thay vì fine-tuning model riêng ở giai đoạn này |

---

## Git Commits

| Commit ID | Message | Author |
|-----------|---------|--------|
| w2-001 | docs: add search keywords for related work | Vũ Tiến Đạt |
| w2-002 | docs: add related paper list | Nguyễn Quang Vinh |
| w2-003 | docs: classify papers by research category | Lê Nguyễn Xuân Lộc |
| w2-004 | docs: prepare literature review matrix | Mai Thị Thanh Ngân |
| w2-005 | docs: update weekly report for week 02 | Mai Thị Thanh Ngân |

---

## Current Problems

1. **Paper tìm kiếm còn phân tán:** Các paper về code grading, GitHub automation và hackathon management tách rời nhau, chưa có paper nào cover đầy đủ cả workflow (GitHub → AI analysis → Judge).

2. **Chưa đọc và tóm tắt chi tiết từng paper:** Danh sách paper đã được chọn nhưng chưa có phân tích sâu theo template paper summary.

3. **Literature review matrix mới ở mức chuẩn bị:** Bản khung vẫn còn trống, cần điền nội dung chi tiết từ các paper.

4. **Chưa có proof-of-concept:** Chưa thử nghiệm LLM prompting với sample code để xác định mức độ chính xác của AI suggestion.

5. **Dynamic Rubric design chưa rõ:** Cấu trúc dữ liệu cho dynamic rubric theo database vẫn chưa được thiết kế cụ thể.

---

## Plan for Next Week

1. **Đọc chi tiết tối thiểu 5-7 paper đã chọn:**
   - 2 papers về LLM/AI code grading
   - 2 papers về GitHub automation hoặc code analysis
   - 2 papers về rubric-based assessment hoặc hackathon management

2. **Hoàn thành các file paper summaries:**
   - Viết chi tiết các `02_related_work/paper_summaries/paper_0X.md`
   - Bao gồm: objective, method, key findings, relevance to project, limitations

3. **Cập nhật literature review matrix:**
   - Điền đầy đủ nội dung sau khi hoàn thành paper summaries
   - Xác định relationship giữa các paper và project requirements

4. **Xác định AI method phù hợp:**
   - Quyết định prompt engineering strategy cho LLM
   - Draft `04_proposed_system/ai_model_integration.md` với chi tiết về LLM API calls, context window, token limits

5. **Thiết kế rubric schema:**
   - Bắt đầu draft schema cho dynamic rubric management
   - Xác định cấu trúc criterion, weight, scoring logic

6. **Chuẩn bị proof-of-concept:**
   - Thu thập sample code từ GitHub repositories
   - Thử nghiệm prompt với 5-10 code samples để xác định chất lượng AI suggestion

---

## Questions for Instructor

1. Nhóm có nên cố gắng tìm paper combine GitHub automation + AI grading + dynamic rubric, hay có thể kết hợp insights từ 3 nhóm paper riêng biệt không?

2. Literature review matrix có cần bao gồm tối thiểu bao nhiêu paper (5, 10, 15) để được coi là đầy đủ cho giai đoạn này?

3. Khi thử nghiệm LLM prompt với code samples, nên dùng prompt engineering (few-shot, chain-of-thought) hay direct prompting đã đủ?

4. Nhóm nên focus vào ranking alignment (AI score vs Judge score correlation) hay focus vào accuracy của từng criterion trước?

5. Dynamic rubric schema có cần support versionning (rubric v1, v2) hay cố định một phiên bản cho toàn bộ project?

---

## Notes

- Repository branch: `SE1823_G04`
- Đã xác định sử dụng LLM API thay vì model custom ở giai đoạn này
- Cần chuẩn bị sample code collection để test AI model
- Sẽ cập nhật tiến độ hàng tuần
