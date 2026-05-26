# Weekly Report - Week 03

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
| Mai Thị Thanh Ngân | Phối hợp, phân công công việc chi tiết và kiểm tra tiến độ reading list | Hoàn thiện lịch đọc 5-7 paper ưu tiên và phân công viết paper summaries |
| Nguyễn Quang Vinh | Viết và hoàn thiện 3 paper summaries | Hoàn thành `02_related_work/paper_summaries/paper_01.md`, `paper_02.md`, `paper_03.md` với analysis: objective, method, findings |
| Vũ Tiến Đạt | Thu thập sample code từ GitHub để sử dụng cho proof-of-concept prompts | Thu thập 20 sample submissions (public repos, synthetic examples) và lưu danh sách reference |
| Lê Nguyễn Xuân Lộc | Bắt đầu thử nghiệm prompt với LLM trên một số sample code | Thực hiện initial prompting với OpenAI API: 5 samples, đo lường suggestion quality và ghi nhận cases cần cải thiện |
| Cả nhóm | Cập nhật literature review matrix và phân phối task summaries | Cập nhật `02_related_work/literature_review_matrix.md` (draft) và bắt đầu mapping paper → project requirements |
| Cả nhóm | Bắt đầu thiết kế schema cho dynamic rubric | Tạo draft schema ở `04_proposed_system/ai_model_integration.md` và `04_proposed_system/database_mapping_iom.md` (phiên bản sơ khai) |

---

## Git Commits

| Commit ID | Message | Author |
|-----------|---------|--------|
| w3-001 | docs: add three paper summaries | Nguyễn Quang Vinh |
| w3-002 | feat: collect sample code list for POC | Vũ Tiến Đạt |
| w3-003 | test: initial LLM prompting experiments | Lê Nguyễn Xuân Lộc |
| w3-004 | docs: update literature review matrix | Mai Thị Thanh Ngân |

---

## Current Problems

1. **Quality variance in sample submissions:** Một số sample code có phạm vi quá rộng hoặc chứa quá nhiều dependencies, khó để prompt AI để đánh giá toàn diện.

2. **Prompt engineering needed:** Initial prompts trả về kết quả không đồng nhất giữa các samples; cần thiết kế few-shot examples và rõ ràng hơn cho từng criterion.

3. **Rubric schema ambiguity:** Draft schema còn chung chung về weight và aggregation; cần thảo luận để chuẩn hóa các criterion và mô tả scoring rules.

4. **Token / context limits:** Một số submissions lớn vượt kích thước context; cần quyết định strategy (trích xuất phần code quan trọng, hoặc gửi file con thay vì toàn bộ repo).

5. **Evaluation baseline chưa hoàn thiện:** Cần xác định cách so sánh AI suggestions với judge scores (correlation metric, confusion per-criterion).

---

## Plan for Next Week

1. **Hoàn thành ít nhất 5 paper summaries:** Hoàn tất `02_related_work/paper_summaries/paper_04.md` → `paper_06.md`.

2. **Refine prompts and run larger POC:** Thiết kế few-shot prompts cho từng criterion, thử nghiệm trên 30-50 samples, thu thập AI suggestions và so sánh với manual labels.

3. **Finalize rubric schema draft:** Định nghĩa criterion, weight, scoring rules, và lưu schema versioned (v0.1) trong `04_proposed_system/database_mapping_iom.md`.

4. **Define evaluation metrics and baseline:** Chọn metrics (per-criterion accuracy, macro F1, correlation with judge ranking) và viết `05_methodology/evaluation_metrics.md` (draft).

5. **Prepare short demo for instructor:** Chuẩn bị a short demo (notebook or script) showing prompt → AI suggestion → rubric scoring for 5 representative samples.

6. **Organize next week commits and tasks:** Tạo issues/tasks in repo for prompt refinement, data labeling, rubric finalization.

---

## Questions for Instructor

1. Nhóm có thể sử dụng public repository submissions làm sample không (về mặt bản quyền/ethics), hay cần synthetic examples thay thế?

2. Giáo viên ưu tiên metric nào cho giai đoạn proof-of-concept: correlation với judge scores hay per-criterion accuracy?

3. Với context limit, nhóm nên tập trung vào sub-file analysis (e.g., main solution file) hay gửi toàn bộ repository để AI phân tích?

---

## Notes

- Repository branch: `SE1823_G04`
- Đã thu thập 20 sample code cho POC; cần thêm labels/manual scores để đánh giá AI suggestions
- Tiếp tục cập nhật literature review và hoàn thiện prompt engineering
