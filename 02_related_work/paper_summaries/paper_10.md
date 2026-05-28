# Paper 10 Summary

## Citation

- **Tên bài:** AI Impact on Hotel Guest Satisfaction via Tailor-Made Services
- **Tác giả:** Nghiên cứu viên ngành Công nghệ Dịch vụ (MDPI)
- **Năm:** 2024
- **Nguồn:** Information (MDPI), Vol. 15, No. 11
- **DOI/Link:** [Link](https://www.mdpi.com/2078-2489/15/11/700)

## Problem

Nghiên cứu giải quyết vấn đề đánh giá thực nghiệm tác động của trí tuệ nhân tạo (AI) trong việc cá nhân hóa các dịch vụ khách sạn thiết kế riêng (Tailor-made Services) đến sự hài lòng tổng thể của khách lưu trú. Trong khi các nghiên cứu trước đây chủ yếu dừng lại ở mức độ lý thuyết hoặc định tính, bài báo này tập trung đo lường định lượng cụ thể thái độ của khách hàng đối với các khuyến nghị cá nhân hóa do AI đưa ra (như gợi ý phòng, gợi ý món ăn, và lịch trình hoạt động).

## Method

Nghiên cứu áp dụng phương pháp **Nghiên cứu thực nghiệm định lượng (Quantitative Empirical Research)**:
- **Xây dựng mô hình nghiên cứu:** Thiết lập các giả thuyết đo lường tác động trực tiếp và gián tiếp của AI cá nhân hóa dịch vụ đến sự hài lòng của khách hàng (Guest Satisfaction).
- **Phân tích nhân tố:** Sử dụng mô hình cấu trúc tuyến tính (SEM - Structural Equation Modeling) để xử lý dữ liệu khảo sát.
- **Biến trung gian:** Đưa vào kiểm tra hai biến số trung gian quan trọng là **Mức độ tin tưởng vào công nghệ AI (Trust in AI)** và **Kinh nghiệm công nghệ của khách hàng (Technology Experience)**.

## Dataset

Tập dữ liệu khảo sát thực tế thu thập từ **340 du khách** tại hai quốc gia Đông Âu là Serbia và Hungary, những người đã trực tiếp trải nghiệm các dịch vụ hỗ trợ bằng AI trong quá trình lưu trú tại các khách sạn thông minh.

## Evaluation

Đo lường mức độ ảnh hưởng của các thành phần thông qua thang đo Likert chuẩn hóa và phân tích đường dẫn (Path Analysis) của mô hình SEM để tính toán các hệ số tác động ($\beta$) và mức độ ý nghĩa thống kê ($p$-value).

## Results

- Việc ứng dụng AI để cá nhân hóa dịch vụ (gợi ý ăn uống, hoạt động giải trí và loại phòng phù hợp) giúp tăng đáng kể và trực tiếp chỉ số hài lòng của khách lưu trú (Guest Satisfaction).
- **Vai trò của Sự tin tưởng:** Niềm tin của khách hàng vào tính bảo mật và độ chính xác của hệ thống AI là nhân tố trung gian cốt lõi. Nếu khách hàng không tin tưởng hệ thống, tác động tích cực của việc cá nhân hóa sẽ bị triệt tiêu hoàn toàn.
- **Kinh nghiệm công nghệ:** Nhóm du khách có hiểu biết và kinh nghiệm sử dụng công nghệ cao (Tech-savvy guests) dễ dàng chấp nhận và cảm thấy hài lòng hơn với các dịch vụ tự động bằng AI so với nhóm khách hàng truyền thống.

## Limitations

- Phạm vi khảo sát địa lý chỉ giới hạn tại hai quốc gia Serbia và Hungary, điều này có thể tạo ra các sai lệch về mặt văn hóa hành vi tiêu dùng so với các khu vực năng động khác như Đông Nam Á hoặc Bắc Mỹ.

## Relevance to our topic

- **Mức độ liên quan:** Rất cao (Empirical Domain Reference).
- **Lý do:** Bài báo cung cấp bằng chứng thực tế rõ ràng ủng hộ việc phát triển các dịch vụ cá nhân hóa (Tailor-made services) bằng AI. Đây chính là mục tiêu cốt lõi của tính năng gợi ý phòng và chăm sóc khách hàng tự động trên **SmartStay AI**.

## Possible improvement

Áp dụng trực tiếp vào **SmartStay AI**:
1. Triển khai tính năng **Gợi ý dịch vụ thiết kế riêng (Tailor-made Recommendation)**: Tận dụng OpenAI API để phân tích sở thích của khách trong quá trình chat, từ đó gợi ý chính xác loại phòng và các dịch vụ bổ sung (ví dụ: tour du lịch địa phương, thực đơn ăn tối, thuê xe) phù hợp với bối cảnh chuyến đi của họ.
2. Xây dựng **Giao diện thân thiện và dễ sử dụng (Ease of Use)**: Để vượt qua rào cản của những khách hàng ít kinh nghiệm công nghệ (như kết luận của bài báo), giao diện chat của SmartStay AI phải cực kỳ tối giản, hỗ trợ cả các nút bấm gợi ý nhanh (Quick Replies) để khách hàng không cần gõ phím quá nhiều vẫn tương tác được với AI.
