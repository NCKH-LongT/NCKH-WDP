# Project Proposal

## 1. Tên đề tài dự kiến

_Personalized Career Orientation & Dynamic Learning Roadmap Platform for Software Engineering Students Using Artificial Intelligence_

Tên tiếng Việt đề xuất:

_Nền tảng định hướng nghề nghiệp và xây dựng lộ trình học tập cá nhân hóa cho sinh viên ngành Công nghệ phần mềm ứng dụng trí tuệ nhân tạo (AI)_

---

## 2. Lĩnh vực ứng dụng

Dự án thuộc các lĩnh vực:

- Trí tuệ nhân tạo (Artificial Intelligence)
- Công nghệ giáo dục (EdTech)
- Hệ thống định hướng nghề nghiệp
- Phân tích dữ liệu học tập
- Hỗ trợ phát triển kỹ năng ngành Công nghệ thông tin

Hệ thống hỗ trợ sinh viên:

- định hướng nghề nghiệp,
- xây dựng lộ trình học tập,
- phân tích kỹ năng,
- quản lý portfolio cá nhân.

---

## 3. Vấn đề thực tế

Hiện nay nhiều sinh viên ngành Công nghệ thông tin gặp khó khăn trong việc:

- xác định hướng nghề nghiệp phù hợp,
- lựa chọn kỹ năng cần học,
- theo kịp xu hướng công nghệ mới,
- xây dựng lộ trình học tập hiệu quả,
- chuẩn bị portfolio phù hợp với nhu cầu tuyển dụng.

Các phương pháp định hướng truyền thống thường:

- mang tính chung chung,
- thiếu cá nhân hóa,
- không cập nhật theo thị trường lao động thực tế.

Điều này dẫn đến:

- học sai công nghệ,
- thiếu kỹ năng thực tế,
- khó cạnh tranh khi xin thực tập hoặc việc làm.

---

## 4. Đối tượng người dùng

### 4.1 Student

Là sinh viên sử dụng hệ thống để định hướng nghề nghiệp và phát triển kỹ năng.

Nhu cầu:

- Xác định career path phù hợp.
- Xây dựng roadmap học tập cá nhân hóa.
- Phân tích skill gap.
- Theo dõi tiến độ học tập và kỹ năng.
- Quản lý GitHub và portfolio cá nhân.
- Chuẩn bị kỹ năng cho thực tập và tuyển dụng.

### 4.2 Academic Counselor

Là cố vấn học tập hoặc giảng viên.

Nhu cầu:

- Theo dõi tiến độ phát triển kỹ năng của sinh viên.
- Hỗ trợ định hướng nghề nghiệp.
- Đánh giá khả năng đáp ứng kỹ năng của sinh viên.
- Đưa ra khuyến nghị học tập phù hợp.

### 4.3 Industry Mentor

Là mentor doanh nghiệp hoặc Senior Developer.

Nhu cầu:

- Hỗ trợ sinh viên định hướng kỹ năng thực tế.
- Đề xuất công nghệ phù hợp với thị trường.
- Theo dõi sự phát triển kỹ năng của mentee.
- Góp ý về roadmap học tập và portfolio.

### 4.4 Admin

Là người quản trị hệ thống.

Nhu cầu:

- Quản lý người dùng và quyền truy cập.
- Cấu hình AI API và third-party services.
- Quản lý dữ liệu roadmap và skill framework.
- Theo dõi trạng thái hoạt động của hệ thống.

---

## 5. Lý do cần tích hợp AI

AI đóng vai trò cốt lõi giúp hệ thống:

- cá nhân hóa lộ trình học tập,
- phân tích kỹ năng sinh viên,
- đánh giá khoảng cách kỹ năng (skill gap),
- gợi ý công nghệ nên học,
- phân tích GitHub và portfolio,
- cập nhật xu hướng tuyển dụng theo thời gian thực.

AI giúp hệ thống:

- thông minh hơn,
- tự động hóa quá trình tư vấn,
- đưa ra khuyến nghị phù hợp với từng sinh viên.

Thay vì sử dụng roadmap cố định, hệ thống có thể:

- cập nhật theo xu hướng thị trường,
- điều chỉnh theo năng lực người dùng,
- đề xuất kỹ năng ưu tiên học tập.

Lưu ý: AI trong hệ thống đóng vai trò hỗ trợ định hướng và gợi ý học tập, không thay thế hoàn toàn cố vấn học tập hoặc mentor doanh nghiệp.

---

## 6. Model AI dự kiến sử dụng

Hệ thống không tự xây dựng hoặc huấn luyện mô hình AI riêng.

Thay vào đó, hệ thống sẽ tích hợp các third-party AI services thông qua API.

Các model/API dự kiến có thể sử dụng:

- OpenAI GPT-4 / GPT-4o
- Google Gemini API
- Claude API (nếu phù hợp)

Các kỹ thuật AI dự kiến áp dụng:

### 6.1 Natural Language Processing (NLP)

Ứng dụng để:

- xử lý câu hỏi người dùng,
- phân tích mô tả công việc,
- phân tích README GitHub,
- phân tích portfolio và kỹ năng.

### 6.2 Recommendation System

Ứng dụng để:

- gợi ý roadmap học tập,
- đề xuất kỹ năng phù hợp,
- đề xuất khóa học hoặc công nghệ nên học.

### 6.3 Semantic Skill Analysis

Ứng dụng để:

- phân tích mối liên hệ giữa các kỹ năng,
- đánh giá độ phù hợp nghề nghiệp,
- xác định skill gap.

### 6.4 Trend Analysis

Ứng dụng để:

- phân tích xu hướng công nghệ,
- cập nhật nhu cầu tuyển dụng từ thị trường lao động,
- đề xuất công nghệ đang được doanh nghiệp ưu tiên.

---

## 7. Kết quả mong muốn

### 7.1 Về mặt hệ thống

- Xây dựng được nền tảng định hướng nghề nghiệp ứng dụng AI.
- Tạo roadmap học tập cá nhân hóa cho từng sinh viên.
- Hỗ trợ phân tích skill gap tự động.
- Hỗ trợ quản lý GitHub Portfolio.
- Cập nhật xu hướng công nghệ theo thị trường tuyển dụng.
- Hỗ trợ theo dõi tiến độ học tập và phát triển kỹ năng.

### 7.2 Về mặt người dùng

Hệ thống giúp sinh viên:

- học đúng kỹ năng,
- theo sát nhu cầu doanh nghiệp,
- cải thiện khả năng thực tập và tuyển dụng,
- có định hướng nghề nghiệp rõ ràng hơn,
- xây dựng portfolio phù hợp với vị trí mong muốn.

### 7.3 Về mặt nghiên cứu ứng dụng AI

- Đánh giá khả năng ứng dụng AI trong định hướng nghề nghiệp.
- Phân tích hiệu quả của AI Recommendation System đối với sinh viên.
- So sánh mức độ phù hợp của roadmap AI-generated với roadmap truyền thống.
- Đề xuất mô hình hỗ trợ học tập cá nhân hóa trong lĩnh vực Software Engineering Education.

---

## 8. Phạm vi đề tài

### 8.1 In Scope

Đề tài tập trung vào:

- quản lý người dùng và hồ sơ kỹ năng,
- phân tích skill gap,
- xây dựng learning roadmap cá nhân hóa,
- tích hợp GitHub Portfolio,
- tích hợp third-party AI API,
- phân tích xu hướng công nghệ,
- đề xuất kỹ năng và công nghệ phù hợp,
- dashboard theo dõi tiến độ học tập.

### 8.2 Out of Scope

Đề tài không bao gồm:

- tự xây dựng AI model,
- tự training hoặc fine-tuning AI model,
- thay thế hoàn toàn vai trò của mentor hoặc counselor,
- cam kết tuyển dụng hoặc giới thiệu việc làm,
- xây dựng nền tảng học trực tuyến hoàn chỉnh như Coursera/Udemy,
- triển khai hệ thống tuyển dụng doanh nghiệp đầy đủ.

---

## 9. Định hướng áp dụng vào hệ thống

Trong hệ thống, đề tài sẽ được áp dụng vào các module:

- Career Orientation Module
- Skill Gap Analysis Module
- Personalized Learning Roadmap Module
- GitHub Portfolio Analysis Module
- Technology Trend Analysis Module
- Student Dashboard
- Mentor/Counselor Dashboard

Quy trình tổng quan:

1. Sinh viên tạo tài khoản và cập nhật hồ sơ kỹ năng.
2. Hệ thống phân tích kỹ năng hiện tại của sinh viên.
3. Sinh viên lựa chọn career path mong muốn.
4. AI phân tích skill gap và xu hướng thị trường.
5. Hệ thống tạo roadmap học tập cá nhân hóa.
6. Sinh viên cập nhật GitHub và portfolio.
7. AI tiếp tục đánh giá tiến độ và đề xuất kỹ năng mới.
8. Mentor/Counselor theo dõi và hỗ trợ định hướng.
9. Hệ thống cập nhật roadmap theo sự phát triển của sinh viên và thị trường công nghệ.

---

## 10. Kết luận

Đề tài _Personalized Career Orientation & Dynamic Learning Roadmap Platform for Software Engineering Students Using Artificial Intelligence_ phù hợp với nhu cầu thực tế của sinh viên ngành Công nghệ thông tin trong bối cảnh thị trường công nghệ thay đổi nhanh chóng.

Việc tích hợp AI giúp hệ thống có khả năng cá nhân hóa lộ trình học tập, phân tích kỹ năng và hỗ trợ định hướng nghề nghiệp hiệu quả hơn. Hệ thống không thay thế hoàn toàn mentor hoặc counselor mà đóng vai trò là công cụ hỗ trợ giúp sinh viên phát triển kỹ năng đúng hướng, phù hợp với nhu cầu tuyển dụng và xu hướng công nghệ hiện đại.
