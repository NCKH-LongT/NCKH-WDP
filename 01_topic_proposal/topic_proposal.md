# Topic Proposal

## 1. Tên đề tài dự kiến

**AI-Based Rapid Source Code Evaluation System Using Predefined Rubrics for Programming Competitions**

Tên tiếng Việt đề xuất:

**Hệ thống đánh giá nhanh mã nguồn bằng AI dựa trên bộ tiêu chí định sẵn cho các cuộc thi lập trình**

---

## 2. Lĩnh vực ứng dụng

Lĩnh vực ứng dụng của đề tài là:

- Quản lý sự kiện
- Quản lý cuộc thi lập trình
- Giáo dục
- Kỹ thuật phần mềm
- Đánh giá mã nguồn tự động
- AI-assisted software evaluation

Đề tài được áp dụng vào hệ thống **SEAL – Smart Event & AI-assisted Hackathon Management Platform**, một nền tảng hỗ trợ quản lý các cuộc thi hackathon học thuật ngành Kỹ thuật Phần mềm.

---

## 3. Vấn đề thực tế

Trong các cuộc thi lập trình hoặc hackathon học thuật, quá trình đánh giá sản phẩm của đội thi thường gặp nhiều khó khăn:

- Số lượng đội thi nhiều khiến giám khảo mất nhiều thời gian để xem mã nguồn.
- Việc đánh giá source code thường phụ thuộc nhiều vào kinh nghiệm cá nhân của từng giám khảo.
- Giám khảo khó kiểm tra toàn bộ repository trong thời gian ngắn.
- Các tiêu chí như code quality, maintainability, readability, architecture, security và documentation thường khó được đánh giá nhanh.
- Ban tổ chức thiếu công cụ hỗ trợ tổng hợp thông tin từ repository như commit history, contribution activity, code changes và review summary.
- Việc chấm điểm thủ công có thể gây chậm trễ trong công bố kết quả.
- Các cuộc thi hackathon cần một công cụ hỗ trợ đánh giá nhanh nhưng vẫn dựa trên rubric rõ ràng.

Vì vậy, hệ thống cần tích hợp AI để hỗ trợ phân tích mã nguồn và tạo ra báo cáo đánh giá nhanh cho giám khảo.

---

## 4. Đối tượng người dùng

### 4.1 Event Coordinator

Là người tổ chức và quản lý cuộc thi.

Nhu cầu:

- Theo dõi tiến độ repository của các đội.
- Kích hoạt quá trình AI review.
- Xem trạng thái đánh giá source code.
- Quản lý kết quả và báo cáo đánh giá.

### 4.2 Judge

Là người chấm điểm bài thi.

Nhu cầu:

- Xem AI-generated code review summary.
- Tham khảo các issue mà AI phát hiện.
- Đánh giá source code theo rubric định sẵn.
- Tiết kiệm thời gian khi review repository.

### 4.3 Team Leader

Là người đại diện đội thi.

Nhu cầu:

- Quản lý repository của đội.
- Nộp link demo, báo cáo và presentation.
- Theo dõi trạng thái submission.

### 4.4 Team Member

Là thành viên đội thi.

Nhu cầu:

- Đóng góp source code vào repository.
- Theo dõi repository activity.
- Xem tiến độ submission của team.

### 4.5 Admin

Là người quản trị hệ thống.

Nhu cầu:

- Cấu hình GitHub API.
- Cấu hình third-party AI API.
- Quản lý webhook secret.
- Quản lý quyền truy cập và cấu hình hệ thống.

---

## 5. Lý do cần tích hợp AI

AI được tích hợp vào hệ thống nhằm hỗ trợ quá trình đánh giá source code trong các cuộc thi lập trình.

Các lý do chính bao gồm:

- Giảm thời gian review source code cho giám khảo.
- Tự động tạo bản tóm tắt chất lượng mã nguồn.
- Hỗ trợ phát hiện vấn đề trong code như:
  - code smell,
  - duplicated logic,
  - poor naming,
  - missing validation,
  - maintainability issue,
  - possible security issue.
- Hỗ trợ đánh giá source code theo rubric định sẵn.
- Tăng tính nhất quán trong quá trình đánh giá.
- Giúp giám khảo có thêm thông tin tham khảo trước khi đưa ra điểm cuối cùng.
- Hỗ trợ ban tổ chức theo dõi chất lượng và tiến độ repository của các đội.

Lưu ý: AI trong đề tài này không thay thế hoàn toàn giám khảo. AI chỉ đóng vai trò là công cụ hỗ trợ đánh giá và tạo báo cáo tham khảo.

---

## 6. Model AI dự kiến sử dụng

Hệ thống không tự xây dựng hoặc huấn luyện mô hình AI riêng.

Thay vào đó, hệ thống sẽ tích hợp với third-party AI services thông qua API.

Các model/API dự kiến có thể sử dụng:

- OpenAI API
- Google Gemini API
- Claude API
- Third-party code review API nếu phù hợp

AI service sẽ nhận dữ liệu đầu vào như:

- repository metadata,
- commit diff,
- changed files,
- source code snippets,
- predefined rubric,
- programming language,
- project description.

AI service sẽ trả về kết quả như:

- code review summary,
- detected issues,
- maintainability feedback,
- readability feedback,
- possible security concerns,
- suggested improvements,
- optional AI-generated score based on rubric.

---

## 7. Kết quả mong muốn

### 7.1 Về mặt hệ thống

- Hệ thống có thể tích hợp GitHub repository cho từng đội thi.
- Hệ thống có thể nhận webhook từ GitHub khi có commit mới.
- Hệ thống có thể lưu commit history và repository activity vào database.
- Hệ thống có thể gửi source code hoặc commit diff đến third-party AI API.
- Hệ thống có thể lưu kết quả AI review.
- Giám khảo có thể xem AI review summary trên dashboard.
- Ban tổ chức có thể theo dõi trạng thái review của từng team.
- Hệ thống hỗ trợ đánh giá source code theo rubric định sẵn.

### 7.2 Về mặt người dùng

- Giám khảo giảm thời gian đọc và phân tích toàn bộ source code.
- Ban tổ chức có cái nhìn tổng quan về tiến độ và chất lượng repository.
- Đội thi được quản lý repository rõ ràng hơn.
- Kết quả đánh giá có thêm dữ liệu tham khảo từ AI.

### 7.3 Về mặt nghiên cứu ứng dụng AI

- Đánh giá khả năng sử dụng AI trong việc hỗ trợ review source code.
- So sánh mức độ hữu ích của AI review đối với giám khảo.
- Xem xét khả năng áp dụng third-party AI services trong môi trường cuộc thi học thuật.
- Đề xuất quy trình sử dụng AI như một công cụ hỗ trợ đánh giá trong programming competitions.

---

## 8. Phạm vi đề tài

### 8.1 In Scope

Đề tài tập trung vào:

- quản lý event và competition,
- quản lý team và repository,
- tích hợp GitHub API,
- xử lý GitHub webhook,
- tracking commit activity,
- tích hợp third-party AI API,
- review source code dựa trên rubric,
- hiển thị AI review summary cho judge/coordinator.

### 8.2 Out of Scope

Đề tài không bao gồm:

- tự xây dựng AI model,
- tự training hoặc fine-tuning AI model,
- thay thế hoàn toàn vai trò của giám khảo,
- tự động quyết định đội thắng cuộc,
- phân tích toàn bộ source code ở mức compiler/runtime testing chuyên sâu,
- triển khai online judge đầy đủ như HackerRank hoặc Codeforces.

---

## 9. Định hướng áp dụng vào hệ thống SEAL

Trong hệ thống SEAL, đề tài này sẽ được áp dụng vào module:

- GitHub Integration Module
- Repository Tracking Module
- AI-assisted Code Review Module
- Judge Dashboard
- Event Coordinator Dashboard

Quy trình tổng quan:

1. Event Coordinator tạo cuộc thi.
2. Hệ thống tạo hoặc liên kết repository cho từng team.
3. Team members commit source code lên repository.
4. GitHub gửi webhook về hệ thống.
5. Hệ thống lưu commit data vào database.
6. Coordinator hoặc hệ thống trigger AI review.
7. Hệ thống gửi repository data hoặc commit diff đến third-party AI API.
8. AI trả về review summary.
9. Judge xem AI review summary và chấm điểm theo rubric.
10. Hệ thống lưu điểm và hỗ trợ công bố kết quả.

---

## 10. Kết luận

Đề tài **AI-Based Rapid Source Code Evaluation System Using Predefined Rubrics for Programming Competitions** phù hợp với định hướng phát triển hệ thống SEAL vì nó giải quyết một vấn đề thực tế trong các cuộc thi lập trình: đánh giá source code nhanh, minh bạch và có hỗ trợ bởi AI.

Hệ thống không thay thế giám khảo mà cung cấp công cụ hỗ trợ để giám khảo đánh giá hiệu quả hơn dựa trên rubric định sẵn. Việc tích hợp GitHub và third-party AI services giúp SEAL trở thành một nền tảng quản lý hackathon hiện đại, có khả năng theo dõi repository, phân tích mã nguồn và hỗ trợ đánh giá trong thời gian ngắn.
