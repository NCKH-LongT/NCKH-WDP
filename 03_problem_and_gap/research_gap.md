# Research Gap and Contributions (Khoảng trống nghiên cứu và Đóng góp của đề tài)

Để định hình vị trí khoa học và thực tiễn của đề tài **SmartStay AI**, chúng tôi đã thực hiện tổng hợp và đối chiếu 11 nghiên cứu khoa học học thuật tiêu biểu nhất trong miền ứng dụng công nghệ khách sạn (Hospitality Technology). Dưới đây là phân tích chi tiết về khoảng trống nghiên cứu (Research Gap) và các đóng góp cốt lõi (Contributions) của đề tài:

---

## 1. Các bài nghiên cứu trước đã giải quyết như thế nào? (Related Work Overview)

Các nghiên cứu trước đây về ứng dụng công nghệ và trí tuệ nhân tạo (AI) trong ngành khách sạn thường tiếp cận theo ba hướng chính:

1. **Nghiên cứu lý thuyết và hành vi vĩ mô:** 
   Nhiều nghiên cứu hệ thống hóa các chiều tác động lý thuyết của AI đối với ngành dịch vụ (Bhat & Khan, 2021; Dutta et al., 2023) hoặc khảo sát tâm lý, thái độ chấp nhận công nghệ của du khách đối với trợ lý ảo bằng bảng hỏi định lượng (Emerald, 2020; MDPI, 2024).

2. **Hệ thống quản lý khách sạn (HMS) truyền thống:**
   Xây dựng các giải pháp quản lý phòng và đặt phòng trực tuyến dựa trên các chức năng CRUD chuẩn và cơ sở dữ liệu quan hệ đồng bộ (ResearchGate, 2022; ResearchGate, 2023), giúp số hóa các thao tác hành chính tiền sảnh.

3. **Giải pháp AIoT và phần cứng thông minh đắt tiền:**
   Tích hợp các mạng lưới cảm biến kết nối vạn vật (IoT) trong phòng ngủ thông minh kết hợp với camera AI nhận diện khuôn mặt tại sảnh để tự động hóa check-in và dự báo sự hài lòng của khách hàng dựa trên học máy (Alexandria, 2024; Elsevier, 2025).

---

## 2. Các bài nghiên cứu trước còn hạn chế gì? (The Research Gap)

Mặc dù mang lại nhiều giá trị, các nghiên cứu trước đây vẫn bộc lộ những khoảng trống nghiên cứu (Research Gaps) lớn sau:

- **Sự thiếu hụt giải pháp thực tiễn tích hợp gọn nhẹ (SaaS):**
   Các nghiên cứu lý thuyết hành vi thuần túy (Bài 03, 06, 11) thiếu đi các kiến trúc kỹ thuật hoặc mã nguồn triển khai thực tế. Ngược lại, các nghiên cứu kỹ thuật (Bài 07, 09) lại quá phụ thuộc vào hạ tầng phần cứng IoT và camera AI nhận diện khuôn mặt vô cùng đắt đỏ, khiến giải pháp này hoàn toàn nằm ngoài khả năng tài chính của phân khúc **khách sạn vừa và nhỏ (SMEs)** hay homestay tự vận hành.

- **Vấn đề ảo tưởng thông tin (Hallucination) của Chatbot:**
   Các chatbot ứng dụng trong ngành khách sạn trước đây thường là chatbot dạng kịch bản cứng nhắc (rule-based) gây nhàm chán, hoặc nếu dùng LLM thế hệ mới (Bài 06) thì lại dễ gặp hiện tượng ảo tưởng thông tin (hallucination) về giá phòng và phòng trống do thiếu cơ chế đồng bộ trực tiếp với Cơ sở dữ liệu thời gian thực (Real-time DB).

- **Hạn chế trong phân tích phản hồi trải nghiệm khách hàng:**
   Các nghiên cứu tiền xử lý cảm xúc bài đánh giá cũ (Bài 02) chủ yếu dừng lại ở mức độ phân cực toàn văn bản (Document-level Sentiment), chưa thể tự động bóc tách sâu xuống cấp độ từng khía cạnh dịch vụ chi tiết (Aspect-Based Sentiment Analysis) một cách tự động và trực quan trên Dashboard cho nhà quản lý.

> [!IMPORTANT]
> **Tóm tắt Research Gap:**
> *Existing AI-powered hospitality management solutions mainly focus on expensive hardware-based IoT smart rooms or generic conversational chatbots prone to hallucination, while limited attention has been given to a lightweight, integrated SaaS platform that combines real-time RAG-driven booking validation with automated aspect-based sentiment review analysis specifically tailored for small and mid-sized hotels (SMEs).*

---

## 3. Nhóm sẽ cải tiến điểm nào? (Proposed Improvements)

Hệ thống **SmartStay AI** trực tiếp cải tiến và giải quyết các hạn chế trên thông qua ba giải pháp kỹ thuật tinh gọn:

1. **Pipeline RAG đồng bộ Database thời gian thực (Real-time RAG Chatbot):**
   Thay vì để chatbot LLM tự sinh câu trả lời ngẫu nhiên, SmartStay AI tích hợp pipeline RAG (Retrieval-Augmented Generation) kết nối trực tiếp với DB trạng thái phòng trống thực tế của khách sạn. Chatbot AI sẽ tự động kiểm tra, xác thực và chốt đơn đặt phòng với độ chính xác 100%, triệt tiêu hoàn toàn hiện tượng ảo tưởng thông tin.

2. **Quy trình "Human-in-the-loop" tích hợp Unified Inbox:**
   Để vượt qua giới hạn hội thoại của chatbot (Bài 01) và xây dựng lòng tin cho khách hàng (Bài 06), hệ thống thiết lập cơ chế tự động chuyển hướng cuộc trò chuyện và cảnh báo cho nhân viên là con người nhảy vào tiếp quản (take over) ngay lập tức khi phát hiện ý kiến tiêu cực hoặc yêu cầu phức tạp từ khách.

3. **Phân tích cảm xúc đa khía cạnh tự động (Aspect-Based Sentiment Analysis):**
   Ứng dụng mô hình ngôn ngữ lớn (LLM API) trên Dashboard hậu sảnh để tự động quét, phân loại cảm xúc phản hồi của khách hàng theo từng khía cạnh dịch vụ cụ thể (Vệ sinh, Nhân sự, Tiện nghi, Giá cả) mà không cần lắp đặt bất kỳ cảm biến IoT đắt tiền nào.

---

## 4. Đóng góp của nhóm là gì? (Our Contributions)

Đề tài nghiên cứu của nhóm mang lại hai đóng góp lớn:

- **Đóng góp khoa học (Academic Contribution):**
   Đề xuất và benchmark thành công một khung kiến trúc tích hợp tinh gọn kết hợp luồng nghiệp vụ đặt phòng HMS truyền thống với Conversational AI (RAG) và NLP (Sentiment Analysis). Cung cấp bằng chứng thực nghiệm về tính hiệu quả của các mô hình ngôn ngữ nhỏ (như GPT-4.1-mini) trong việc nâng cao sự hài lòng của khách hàng và tối ưu hóa chi phí vận hành ngành dịch vụ.

- **Đóng góp thực tiễn (Practical Contribution):**
   Xây dựng thành công một giải pháp phần mềm dạng dịch vụ (SaaS) **SmartStay AI** hoàn chỉnh, hoạt động mượt mà trên môi trường Web và Mobile. Giải pháp giúp các chủ khách sạn vừa và nhỏ tiết kiệm 40% - 50% thời gian trực tổng đài, giảm đáng kể sự phụ thuộc vào các sàn OTA (tăng tỷ lệ đặt phòng trực tiếp), ngăn chặn overbooking và quản lý chất lượng dịch vụ chuyên nghiệp dựa trên dữ liệu phản hồi thực tế của khách hàng.
