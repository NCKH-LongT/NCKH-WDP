# Weekly Report - Week 02

## Group Information

- **Class:** SE1823
- **Group:** Group 01
- **Topic:** AI Study Hub (Hệ thống Quản lý Tài liệu Học tập AI)
- **Leader:** Nguyễn Thiên Ân
- **Members:** Châu Hiếu Nhân, Mai Thành Nhân, Lê Ngọc Bảo Khánh, Vũ Lưu Kiệt

---

## Tasks Completed This Week

| Member | Task | Result |
| :--- | :--- | :--- |
| **Nguyễn Thiên Ân** | - Chủ trì họp nhóm phân chia công việc.<br>- Tổng hợp danh sách từ khóa và viết báo cáo tuần. | - Hoàn thành file `week_02.md`. <br>- Thống nhất cấu trúc thư mục dự án trên Git. |
| **Châu Hiếu Nhân** | - Tìm kiếm và thẩm định các tài liệu liên quan trực tiếp đến đề tài (Hệ thống quản lý tài liệu, trợ lý học tập). | - Tìm được 5 bài báo thuộc **Nhóm 1 (Directly Related)** đạt chuẩn học thuật. |
| **Mai Thành Nhân** | - Khảo sát và tìm kiếm tài liệu về các mô hình và phương pháp AI (Kiến trúc RAG, Vector Embedding). | - Tìm được 3 bài báo thuộc **Nhóm 2 (AI Models/Methods)**. |
| **Lê Ngọc Bảo Khánh**| - Nghiên cứu tài liệu về domain ứng dụng (Xu hướng số hóa giáo dục EdTech, văn hóa chia sẻ dữ liệu sinh viên). | - Tìm được 2 bài báo thuộc **Nhóm 3 (Domain Application)**. |
| **Vũ Lưu Kiệt** | - Xây dựng bộ từ khóa tìm kiếm (Primary, Domain-specific, Method keywords).<br>- Định dạng bảng biểu Markdown và kiểm tra trùng lặp tài liệu. | - Hoàn thành file `search_keywords.md`. <br>- Hỗ trợ kiểm tra tính hợp lệ của link DOI. |

---

## Git Commits

| Commit ID | Message | Author |
| :---: | :--- | :--- |


---

## Current Problems

- **Vấn đề 1:** Một số bài báo khoa học chất lượng cao trên các nền tảng lớn (IEEE, Springer) yêu cầu tài khoản trả phí hoặc quyền truy cập nội bộ mới xem được bản full-text đầy đủ.
- **Giải pháp tạm thời:** Nhóm tận dụng các nguồn tài liệu mở (Open Access), kho lưu trữ mã nguồn mở **arXiv**, và công cụ **Google Scholar** để tải các bản thảo PDF được chia sẻ công khai của tác giả.

---

## Plan for Next Week

- **Nhiệm vụ 1:** Hoàn thiện sơ đồ ca sử dụng tổng quan (Use Case Diagram) cho hệ thống AI Study Hub dựa trên các Functional Requirements đã đề xuất.
- **Nhiệm vụ 2:** Phân tích kỹ thuật chi tiết cho các Actor (User, Admin, ChatbotService) để chuẩn bị cho việc thiết kế Database ở các tuần tiếp theo.
- **Nhiệm vụ 3:** Cả nhóm cùng đọc kỹ nội dung cốt lõi của 10 bài báo đã chọn để trích xuất các giải pháp công nghệ áp dụng trực tiếp vào dự án (đặc biệt là phương pháp Chunking văn bản và chọn Vector Database).

---

## Questions for Instructor

- **Câu hỏi 1:** Thầy cho em hỏi trong danh sách 10 bài báo liên quan, nếu có một số tài liệu ở định dạng bản thảo (Preprint) từ nguồn arXiv thì có được chấp nhận hoàn toàn làm tài liệu tham khảo chính thống cho nghiên cứu không ạ?
- **Câu hỏi 2:** Về phần lưu trữ tài liệu (Cloud Storage), nhóm em dự kiến dùng kiến trúc lưu trữ dạng Object (như AWS S3, Cloudinary)