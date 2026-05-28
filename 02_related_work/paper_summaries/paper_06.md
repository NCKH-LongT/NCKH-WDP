# Paper 06 Summary

## Citation

- **Tên bài:** Adoption of AI-based Chatbots for Hospitality and Tourism
- **Tác giả:** Nghiên cứu viên ngành Dịch vụ du lịch (Emerald)
- **Năm:** 2020
- **Nguồn:** International Journal of Contemporary Hospitality Management, Vol. 32, No. 10
- **DOI/Link:** [Link](https://www.emerald.com/ijchm/article-abstract/32/10/3199/125105/Adoption-of-AI-based-chatbots-for-hospitality-and?redirectedFrom=fulltext&utm_source=chatgpt.com)

## Problem

Nghiên cứu tập trung giải quyết bài toán chấp nhận công nghệ (Technology Acceptance) của người dùng đối với các trợ lý ảo tương tác tự động bằng AI (Chatbots) trong ngành du lịch và lưu trú. Mặc dù nhiều khách sạn triển khai chatbot để tiết kiệm chi phí, nhưng tỷ lệ khách hàng thực sự tin tưởng và tiếp tục sử dụng dịch vụ này vẫn còn hạn chế. Nghiên cứu làm rõ các yếu tố tâm lý nào thúc đẩy hoặc cản trở ý định sử dụng chatbot của khách du lịch.

## Method

Nghiên cứu áp dụng mô hình khảo sát thực nghiệm kết hợp với lý thuyết chấp nhận công nghệ mở rộng:
- **Khung lý thuyết:** Sử dụng Mô hình Chấp nhận Công nghệ (TAM - Technology Acceptance Model) mở rộng, bổ sung thêm các biến số về **Sự tin tưởng (Trust)**, **Cảm giác tương tác xã hội (Social Presence)** và **Kinh nghiệm công nghệ của khách hàng (Technology Experience)**.
- **Phương pháp thu thập:** Phát bảng hỏi khảo sát (Survey) quy mô rộng đến các du khách đã từng có trải nghiệm tương tác với chatbot của các hãng du lịch hoặc khách sạn.
- **Phân tích dữ liệu:** Sử dụng mô hình cấu trúc tuyến tính (SEM - Structural Equation Modeling) để kiểm định các giả thuyết nghiên cứu.

## Dataset

Mẫu khảo sát thực tế gồm hàng trăm khách du lịch đa quốc gia đã từng sử dụng chatbot để đặt phòng, đặt vé máy bay hoặc hỏi thông tin du lịch trực tuyến.

## Evaluation

Hệ thống được đánh giá gián tiếp dựa trên thái độ và hành vi của người dùng qua các chỉ số:
- **Perceived Usefulness (Nhận thức tính hữu ích):** Mức độ tiện lợi chatbot mang lại.
- **Perceived Ease of Use (Nhận thức tính dễ dùng):** Thiết kế giao diện và tốc độ phản hồi.
- **Trust (Sự tin tưởng):** Mức độ tin cậy của thông tin phòng và giá mà chatbot cung cấp.
- **Intention to Use (Ý định sử dụng):** Khả năng khách hàng sẽ tiếp tục dùng chatbot cho các giao dịch sau.

## Results

- **Nhận thức tính hữu ích và Sự tin tưởng** là hai nhân tố có tác động mạnh mẽ nhất đến ý định sử dụng chatbot của khách du lịch.
- **Tính cá nhân hóa (Personalization)** và **Tốc độ phản hồi tức thì** đóng vai trò quyết định trong việc xây dựng niềm tin của khách hàng vào hệ thống AI.
- Nếu chatbot phản hồi sai thông tin hoặc bị lặp lại câu hỏi (hallucination/lỗi logic), sự tin tưởng của người dùng sẽ sụt giảm nghiêm trọng, dẫn đến việc họ rời bỏ hệ thống để tìm kiếm nhân viên là con người.

## Limitations

- Nghiên cứu tập trung vào khía cạnh hành vi và tâm lý học của người dùng, chưa cung cấp giải pháp kiến trúc kỹ thuật hoặc mã nguồn cụ thể để khắc phục các hạn chế về mặt hội thoại của chatbot.

## Relevance to our topic

- **Mức độ liên quan:** Rất cao (Business/Behavioral Reference).
- **Lý do:** Bài báo chỉ ra "Sự tin tưởng" là chìa khóa để chatbot đặt phòng thành công. Điều này đặt ra yêu cầu cho **SmartStay AI** là Chatbot AI không được phép đưa ra thông tin sai lệch về phòng trống và giá phòng (hallucinations).

## Possible improvement

Áp dụng trực tiếp vào **SmartStay AI**:
1. Để xây dựng **Sự tin tưởng (Trust)** cao nhất, chatbot AI của SmartStay AI phải được tích hợp chặt chẽ với cơ sở dữ liệu thời gian thực (Real-time DB) thông qua pipeline RAG để trả lời chính xác 100% tình trạng phòng trống và giá phòng, thay vì để LLM tự sinh thông tin ngẫu nhiên.
2. Thiết lập quy trình **Human-in-the-loop (Hộp thư chung Omnichannel Inbox)**: Khi Chatbot AI nhận thấy câu hỏi vượt quá khả năng xử lý hoặc khách hàng thể hiện sự không hài lòng (Sentiment tiêu cực), hệ thống sẽ tự động chuyển hướng cuộc hội thoại và thông báo cho nhân viên khách sạn nhảy vào tiếp quản (take over) tức thời, đảm bảo trải nghiệm khách hàng không bị đứt gãy.
