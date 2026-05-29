# TOPIC PROPOSAL: SEAL AI AUDITOR

> [!NOTE]  
> **Đề tài đề xuất:** SEAL Hackathon Management System.
> **Tên tiếng Việt:** Hệ thống quản lý cuộc thi SEAL Hackathon ngành Kỹ thuật Phần mềm.

---

## 1. LĨNH VỰC ỨNG DỤNG (APPLICATION DOMAINS)

Dự án được ứng dụng vào lĩnh vực:

- **Quản lý cuộc thi lập trình (Hackathon Management):** Quản lý quy trình đăng ký, duyệt đội thi, vòng chấm thi và xếp hạng trực tiếp.
- **Tự động hóa quy trình phát triển (Git Automation):** Tự động cấp phát tài nguyên lập trình qua GitHub REST API.
- **Đánh giá chất lượng mã nguồn (Code Quality Review):** Phân tích kỹ thuật và phân tích Git diff.
- **Hỗ trợ chấm điểm theo tiêu chí (Rubric-based Assessment):** Ánh xạ lịch sử mã nguồn trực tiếp vào bộ tiêu chí đánh giá.

---

## 2. VẤN ĐỀ THỰC TẾ & SỰ CẦN THIẾT CỦA ĐỀ TÀI (PRACTICAL PROBLEM)

Tổ chức các cuộc thi lập trình (Hackathon) là hoạt động cốt lõi để thúc đẩy đổi mới sáng tạo trong các trường Đại học và Doanh nghiệp. Tuy nhiên, quy trình vận hành thủ công hiện nay đang đối mặt với những thách thức lớn:

- **Gánh nặng quản trị của Ban tổ chức (BTC):** Việc xác thực email danh tính, phê duyệt đội thi, khởi tạo thủ công hàng chục GitHub Private Repository và phân quyền cho từng thí sinh mất nhiều thời gian, dễ sai sót.
- **Quy trình chấm thi thủ công:** Việc chấm điểm thực hiện qua file Excel riêng lẻ của từng giám khảo, phải thu thập và nhập lại toàn bộ kết quả thủ công, dẫn đến chậm trễ và dễ xảy ra sai sót.
- **Kênh liên lạc còn hạn chế:** Kênh thông tin liên lạc hạn chế giữa ban tổ chức, mentor, đội thi và người tham gia.
  **Giải pháp:** Dự án **SEAL Hackathon Management System** được thiết kế để tự động hóa 100% khâu cấp phát tài nguyên Git và áp dụng **AI** để hỗ trợ đánh giá, "kiểm toán" kỹ thuật toàn diện mã nguồn của thí sinh và đưa ra gợi ý chấm điểm.

---

## 3. ĐỐI TƯỢNG NGƯỜI DÙNG (USER PERSONAS)

Nền tảng hướng tới thiết kế trải nghiệm tối ưu cho các nhóm đối tượng sau:

### 3.1. Hackathon Participant (Thí sinh tham gia)

- **Nhu cầu:** Đăng ký tài khoản và tạo đội trực tuyến nhanh chóng; nhận email xác thực lời mời vào đội tự động; tự động có quyền truy cập vào GitHub Private Repository do hệ thống cấp phát.

### 3.2. Event Coordinator (Ban tổ chức - BTC)

- **Nhu cầu:** Theo dõi nhanh danh sách đội thi; tự động hóa quy trình tạo repo GitHub và cấp quyền lập trình; theo dõi tiến độ code thực tế của toàn bộ các đội qua Dashboard tập trung; quản lý các cuộc thi, vòng thi và thiết lập bộ khung chấm điểm (Rubrics).

### 3.3. Hackathon Judge (Ban giám khảo - BGK)

- **Nhu cầu:** Xem báo cáo phân tích kỹ thuật chi tiết của AI cho từng đội thi; tham khảo điểm số Rubric gợi ý ; xem phân tích thế mạnh/hạn chế của dự án; truy cập bộ câu hỏi chất vấn sâu sắc được AI soạn thảo riêng cho từng nhóm dựa trên cấu trúc code thực tế của họ, chấm điểm cho đội thi.

---

## 4. LÝ DO TÍCH HỢP TRÍ TUỆ NHÂN TẠO (WHY INTEGRATE AI)

Công nghệ AI đóng vai trò là "Giám sát viên kỹ thuật 24/7" giúp chấm thi chính xác tuyệt đối:

- **Phân tích chất lượng mã nguồn:** Đọc hiểu các đoạn Git diff (dòng code thay đổi) để tự động bóc tách Tech Stack thực tế, phát hiện các thư viện sử dụng và xác định mô hình kiến trúc phần mềm.
- **Kiểm duyệt bảo mật mã nguồn (Security Auditing):** Quét qua các đoạn vá lỗi code thời gian thực để cảnh báo ngay lập tức nếu thí sinh để lộ API Keys, mật khẩu hoặc cấu hình hệ thống thiếu an toàn.
- **Đánh giá mức độ trưởng thành của công nghệ AI (RAG Maturity):** Tự động phát hiện xem đội thi có thực sự xây dựng giải pháp AI nâng cao hay không (như phát hiện hybrid_search, reranking, agentic_routing) hay chỉ là chatbot gọi API cơ bản.
- **Giảm tải công việc chấm thi:** Đánh giá chi tiết bài làm của các đội thi theo tiêu chí Rubric định sẵn, giúp giám khảo đưa ra quyết định chấm thi nhanh chóng, chính xác.

---

## 5. MÔ HÌNH VÀ CÔNG NGHỆ AI DỰ KIẾN (PROPOSED AI MODELS)

Nền tảng tích hợp dịch vụ AI đám mây thông qua API thế hệ mới nhất của Google để tối ưu hóa chi phí vận hành và tài nguyên hạ tầng phần cứng:

- **Core Engine:** **Google Gemini API (gemini-3.1-flash-lite)**.
- **Dữ liệu đầu vào (Input):** Thông tin Metadata của Commit (thành viên thực hiện, message), danh sách các file thay đổi, và toàn bộ nội dung Git diff patch (mã nguồn được thêm/bớt).
- **Dữ liệu đầu ra (Output):** Kết quả phân tích có cấu trúc JSON bao gồm: tech_stack, rag_maturity level, assessment (advantages, disadvantages, security warnings), và gợi ý điểm Rubric kèm bộ câu hỏi chất vấn.

---

## 6. PHẠM VI ĐỀ TÀI (PROJECT SCOPE)

Để đảm bảo tính khả thi cao trong thời gian triển khai, đề tài phân định rõ ràng ranh giới phạm vi:

### 6.1. Thuộc phạm vi dự án (In Scope)

- Xây dựng cổng đăng ký và tạo đội thi xác thực email 100% (gửi mail xác thực lời mời gia nhập nhóm).
- Tích hợp **GitHub REST API** để tự động hóa khâu tạo Private Repository và phân quyền thành viên đội thi khi Admin duyệt.
- Scheduler chạy nền tự động đồng bộ hóa commits và git diff của tất cả các đội thi 30 phút một lần.
- Tích hợp **Gemini 3.1 Flash Lite API** để phân tích kỹ thuật từng lần push (per-push) và tổng hợp lịch sử cấp team (team aggregate).
- Cổng chấm điểm Rubric trực quan dành cho BGK và bảng xếp hạng Leaderboard cập nhật điểm số trực tiếp.
- Xây dựng hệ thống trên hạ tầng hiện đại: **React (Frontend), Node.js/Express (Backend), MongoDB (Database)**.

### 6.2. Nằm ngoài phạm vi dự án (Out of Scope)

- Tự xây dựng, huấn luyện hoặc fine-tune một mô hình ngôn ngữ lớn (LLM) riêng biệt về code từ đầu.
- Tích hợp trực tiếp hệ thống CI/CD để triển khai tự động ứng dụng của thí sinh lên cloud (chỉ dừng lại ở mức lấy mã nguồn về để phân tích kỹ thuật tĩnh).
- Tự động quyết định điểm số và xếp hạng của đội thi mà hoàn toàn không có sự can thiệp của Ban giám khảo (Bắt buộc phải áp dụng quy trình **Human-in-the-loop** - BGK kiểm tra, điều chỉnh điểm số gợi ý từ AI và đưa ra quyết định cuối cùng).

---

## 7. KẾT QUẢ MONG NUỐN & GIÁ TRỊ THỰC TIỄN (EXPECTED RESULTS)

### 7.1. Về mặt hệ thống

- Trợ lý ảo AI phân tích git diff và trả về kết quả cấu trúc JSON chính xác 100% với độ trễ phản hồi dưới 2 giây.
- Quy trình tự động hóa GitHub hoạt động trơn tru: tự động tạo repo, phân quyền collaborator không có sai sót.
- Giao diện Dashboard chấm thi hoạt động realtime, đồng bộ điểm số tức thời lên Leaderboard chung cuộc.

### 7.2. Về mặt giá trị thực tiễn

- Giúp Ban tổ chức tiết kiệm **90% thời gian** vận hành, cấp phát tài nguyên Git thủ công cho các đội thi.
- Giúp Ban giám khảo có cái nhìn toàn diện, khách quan 360 độ về quá trình code thực tế của các đội.
- Giúp thí sinh nâng cao chất lượng mã nguồn thông qua phản hồi nhanh về bảo mật và tiêu chuẩn kỹ thuật.

### 7.3. Về mặt nghiên cứu ứng dụng AI

- Đánh giá tính hiệu quả thực tế của mô hình ngôn ngữ lớn (LLM) thế hệ mới (Gemini 3.1 Flash Lite) trong tác vụ phân tích mã nguồn động và đối chiếu tiêu chí chất lượng (Quantitative & Qualitative Software Auditing).
- Đóng góp mô hình kết hợp "AI đề xuất - Con người quyết định" phục vụ chấm thi công bằng và minh bạch trong giáo dục công nghệ thông tin.

---
