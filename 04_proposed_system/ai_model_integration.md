# Bước 8: Chọn model AI và mô tả cách tích hợp

Dưới đây là mô tả chi tiết về mô hình AI được sử dụng trong hệ thống để hỗ trợ chức năng **"Tìm vị trí đỗ xe nhanh"** (Smart Parking Assistant) thông qua việc phân tích và gợi ý vị trí.

| Nội dung | Phân tích và Quyết định |
| --- | --- |
| **Model dùng là gì?** | Sử dụng **LLM (Large Language Model - Google Gemini)** kết hợp với kỹ thuật **Function Calling** và **RAG (Retrieval-Augmented Generation)**. *(Tùy chọn: Kết hợp thuật toán tìm kiếm Rule-based để hỗ trợ LLM).* |
| **Vì sao chọn model này?** | Có phù hợp với bài toán không? **Có, rất phù hợp**. LLM giúp người dùng tìm chỗ đỗ bằng ngôn ngữ tự nhiên thay vì phải tự thao tác thủ công (VD: *"Tìm giúp tôi chỗ đỗ gần thang máy tầng 2"*). Kỹ thuật Function Calling cho phép LLM mapping câu lệnh với cơ sở dữ liệu thời gian thực để tìm ra chỗ trống chính xác. Điều này nâng cao UX/UI và giúp người dùng không bị bối rối trong các bãi đỗ xe quá rộng. |
| **Model lấy từ đâu?** | - **Cơ sở lý thuyết**: Hướng tiếp cận tích hợp LLM vào xử lý dữ liệu giao thông/bãi đỗ lấy cảm hứng từ nghiên cứu *"Traffic flow perception system"* (ứng dụng LLMs kết hợp các model khác). Logic tìm kiếm và gợi ý chỗ đỗ tối ưu kế thừa tư tưởng từ bài báo *"Real-time slot allocation system"* (sử dụng ML và heuristic optimization để giảm thời gian tìm kiếm vị trí).<br>- **Nguồn triển khai thực tế**: Sử dụng **REST API / SDK chính thức** cung cấp bởi nền tảng **Google AI Studio** (Google Cloud). |
| **Input của model là gì?** | **Text (Văn bản)**: Câu truy vấn/yêu cầu của người dùng từ Mobile App.<br>**Bảng dữ liệu (JSON)**: Danh sách các slot đang trống (slot ID, tọa độ, khoảng cách đến thang máy) do Node.js Backend nạp vào làm Context (Ngữ cảnh). |
| **Output của model là gì?** | Trả về một **Khuyến nghị (Recommendation)**. Dữ liệu đầu ra là định dạng JSON cấu trúc hóa chứa `slot_id` tối ưu nhất để Mobile App render bản đồ/đường đi, kết hợp với **Phản hồi (Text)** thân thiện giao tiếp với người dùng. |
| **Cách tích hợp vào app?** | Tích hợp dạng **Node.js service** trực tiếp trên Backend. Khi Mobile App gửi lệnh yêu cầu tìm chỗ, Node.js sẽ gọi Gemini API kết hợp dữ liệu Database bãi đỗ để xử lý, sau đó trả kết quả về cho ứng dụng. |
| **Có baseline không?** | **Có. Baseline là Manual & Rule-based**: Nếu không dùng AI, hệ thống sẽ yêu cầu người dùng thao tác bằng tay (Manual) lướt xem sơ đồ bãi đỗ 2D trên app để tìm slot đang trống (màu xanh), hoặc dùng thanh công cụ Filter cứng để lọc theo tầng. |
