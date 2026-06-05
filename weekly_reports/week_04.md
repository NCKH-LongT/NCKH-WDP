# Weekly Report - Week 04

## Group Information

- **Class**: SE1823
- **Group**: G03
- **Leader**: Bùi Đức Anh
- **Members**: Lương Khánh Toàn, Lê Văn Kiên, Nguyễn Khánh Hưng, Tăng Thùy Thụy

## Tasks Completed This Week

| Member                    | Task                                                                                                                                                            | Result                                                                                                                                          |
| :------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bùi Đức Anh**           | Tổng hợp dữ liệu học thuật, viết phần Giới thiệu (Introduction) và thiết lập 4 Câu hỏi nghiên cứu (RQ1 - RQ4) cho bài báo khoa học.                             | Hoàn thành bản phác thảo các chương đầu tại tệp `02_related_work/research_questions.md`.                                                        |
| **Lương Khánh Toàn**      | Ghép nối dữ liệu từ các tệp tóm tắt cá nhân để hoàn thiện bảng Ma trận tổng quan văn liệu; viết phần Khoảng trống nghiên cứu (Research Gap).                    | Hoàn thành tích hợp dữ liệu 11 bài báo tại tệp `02_related_work/literature_review_matrix.md` và `research_gap.md`.                              |
| **Lê Văn Kiên**           | Phân tích sâu kiến trúc dữ liệu điểm chạm AI, xây dựng cấu trúc luồng dữ liệu (Data Flow) và định dạng JSON Input/Output cho cấu hình Chatbot.                  | Hoàn thành tài liệu thiết kế kỹ thuật tại tệp `03_system_architecture/data_ai_architecture.md`.                                                 |
| **Nguyễn Khánh Hưng**     | Khảo sát chi tiết kiến trúc ứng dụng, phân rã sơ đồ Use Case hệ thống và thiết lập cấu trúc định tuyến tổng thể cho 14 trang chức năng.                         | Hoàn thành đặc tả luồng đi và phân rã các lớp tại tệp `03_system_architecture/ui_ux_routing.md`.                                                |
| **Tăng Thùy Thụy**        | Chuẩn bị và tối ưu hóa hệ thống mã Prompt AI phục vụ việc dựng Prototype giao diện Mockup cho 5 trang màn hình cốt lõi của nền tảng.                            | Đóng gói trọn bộ prompt thiết kế cấu trúc UI đồng bộ theo tiêu chuẩn Modern & Clean.                                                            |
| **Cả nhóm (All members)** | Họp nhóm thống nhất tích hợp mô hình kinh doanh gói Premium (35k/7 ngày và 69k/tháng) vào kiến trúc hệ thống; rà soát, kiểm tra chéo toàn bộ mã nguồn Markdown. | Đạt sự đồng bộ 100% dữ liệu trên nhánh `SE1823_G03`, không xảy ra xung đột Git; chốt xong phương án thiết kế luồng nạp và phân quyền tài khoản. |

## Git Commits

| Commit ID | Message | Author |
| :-------- | :------ | :----- |

## Current Problems

- Việc chuyển dịch từ thuật toán Doc2vec truyền thống sang kỹ thuật nhúng LLM (Gemini Embedding API) hiện đại đòi hỏi nhóm phải nghiên cứu thêm cách thức tối ưu hóa token đầu vào khi bóc tách các tệp tin dependency cấu hình thư viện lớn.
- Gặp một số khó khăn nhỏ trong việc chuẩn hóa thuật ngữ tiếng Anh chuyên ngành khi viết phần Phương pháp nghiên cứu dự kiến (Proposed Methodology) cho bài báo khoa học để bám sát mô hình IOM.

## Plan for Next Week

- Bắt đầu triển khai thiết kế chi tiết chương Phương pháp nghiên cứu (Methodology) và phác thảo sơ đồ luồng thuật toán chi tiết cho module nhận diện thiên hướng năng lực ngầm (Latent Talent Identification).
- Sử dụng bộ prompt AI đã chuẩn bị ở tuần này để tiến hành sinh và dựng hoàn chỉnh giao diện Prototype thực tế cho 5 trang trọng tâm (LoginPage, Dashboard, Repo List, Analysis Result, ChatAI).

## Questions for Instructor

- Thưa thầy, khi Chatbot AI thực hiện bóc tách các tệp cấu hình dependency (`package.json`, `requirements.txt`) để đối chiếu với bộ tín hiệu kỹ năng chuẩn, nhóm em có cần thiết kế thêm một tầng lọc trung gian để loại bỏ các thư viện tiện ích thông thường (như thư viện format code, linting code) trước khi đẩy dữ liệu vào mô hình Embedding để tiết kiệm chi phí API không ạ?
