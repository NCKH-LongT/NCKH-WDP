# Paper 03 Summary

## Citation
- **Tên bài:** Artificial Intelligence (AI) in the Hospitality Industry: A Review Article
- **Tác giả:** Suhail Ahmad Bhat, Nisar Ahmad Khan
- **Năm:** 2021
- **Nguồn:** Kiến trúc tri thức Springer, Chuyển đổi số trong ngành dịch vụ.
- **DOI/Link:** https://doi.org/10.1007/978-3-030-58669-0_21

## Problem
Ngành công nghiệp khách sạn và dịch vụ lưu trú đang đứng trước áp lực chuyển đổi số lớn để đáp ứng kỳ vọng ngày càng cao của khách hàng về tính cá nhân hóa và tốc độ phục vụ. Nghiên cứu giải quyết vấn đề hệ thống hóa các lý thuyết phân mảnh về AI trong ngành nhà hàng - khách sạn, nhằm làm rõ AI đang thay đổi trải nghiệm khách hàng và tối ưu hóa vận hành nội bộ như thế nào.

## Method
Bài báo tiếp cận theo phương pháp **Tổng quan nghiên cứu hệ thống (Systematic Literature Review)**. Tác giả thu thập, sàng lọc các nghiên cứu học thuật chất lượng cao từ các cơ sở dữ liệu lớn (Scopus, Web of Science, Google Scholar) trong giai đoạn từ 2010 - 2020 để phân nhóm và xây dựng khung lý thuyết toàn diện về các chiều tác động của AI.

## Dataset / Context
Khảo sát toàn diện bối cảnh ngành công nghiệp hiếu khách (Hospitality Industry) toàn cầu, tập trung sâu vào các mô hình khách sạn thông minh (Smart Hotels), hệ thống tự động hóa và các ứng dụng chatbot tương tác.

## Evaluation & Metrics
Vì là bài báo dạng Review, các tiêu chí đánh giá dựa trên:
- Tỷ lệ đóng góp công nghệ của các phân nhóm AI (Robotics, Chatbots, PMS thông minh).
- Mức độ cải thiện chỉ số hài lòng của khách hàng (Customer Satisfaction) và hiệu quả giảm chi phí vận hành (Operational Cost Reduction).

## Results
Nghiên cứu chỉ ra 3 nhóm ứng dụng cốt lõi của AI đang thống trị và định hình lại ngành khách sạn:
1. **Hệ thống tương tác tiền sảnh (Front-of-house AI):** Trợ lý ảo, Chatbot AI phục vụ 24/7 giúp giải đáp thông tin phòng, đặt phòng tức thì mà không cần nhân viên trực ca.
2. **Hệ thống quản trị hậu sảnh (Back-of-house AI):** Tự động hóa quy trình quản lý buồng phòng, tối ưu hóa giá phòng động theo thị trường (Dynamic Pricing).
3. **Cá nhân hóa trải nghiệm (Personalization):** AI phân tích hành vi và feedback cũ của khách để gợi ý dịch vụ đi kèm phù hợp.
- Bài báo kết luận: Việc triển khai AI giúp tăng tỷ lệ giữ chân khách hàng và giảm tới 30% khối lượng công việc thủ công lặp đi lặp lại của nhân viên khách sạn.

## Limitations
Nghiên cứu chủ yếu dựa trên tổng hợp lý thuyết, chưa đi sâu vào đo lường các thông số kỹ thuật cụ thể (độ trễ, kiến trúc thuật toán chi tiết) của một hệ thống công nghệ cụ thể.

## Relevance to our topic
Mức độ liên quan: Rất cao (Background / Framework-foundational paper). Bài báo này cung cấp khung lý thuyết nền tảng vững chắc để viết chương mở đầu (Lý do chọn đề tài) và Chương Cơ sở lý thuyết cho đồ án SmartStay AI.

## Possible improvement for our system
Áp dụng trực tiếp để bảo vệ và thiết kế **SmartStay AI**:
1. Sử dụng khung phân loại của bài báo để thiết kế cấu trúc hệ thống SmartStay AI thành 2 phân hệ rõ ràng: Phân hệ Front-of-house (Chatbot AI hỗ trợ đặt phòng trực tuyến 24/7 cho khách hàng) và Phân hệ Back-of-house (Dashboard quản trị, phân tích doanh thu và dán nhãn phản hồi cho admin).
2. Lấy các luận điểm của bài báo về "nhu cầu phản hồi tức thì" để làm tiêu chuẩn kỹ thuật cho module Chatbot: Phải áp dụng RAG tối ưu để ép độ trễ xuống thấp nhất, đáp ứng đúng tâm lý khách hàng thời đại số.