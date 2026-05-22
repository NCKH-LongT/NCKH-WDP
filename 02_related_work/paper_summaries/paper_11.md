# Tóm tắt Bài báo 11

## Trích dẫn

Xu, J., Wu, H., Wang, J., & Long, M. (2021). *Anomaly Transformer: Time Series Anomaly Detection with Association Discrepancy*. arXiv. https://arxiv.org/abs/2110.02642

## Vấn đề nghiên cứu

Phát hiện bất thường không giám sát trong chuỗi thời gian là bài toán khó vì các điểm bất thường xuất hiện hiếm và thường không khác biệt rõ rệt dưới các tiêu chí theo từng điểm. Bài báo đặt vấn đề liệu Transformer có thể xác lập một tiêu chí bất thường mang tính phân biệt cao hơn bằng cách mô hình hóa các quan hệ liên kết trên toàn bộ chuỗi hay không.

## Phương pháp

Nhóm tác giả đề xuất `Anomaly Transformer` với cơ chế `Anomaly-Attention`. Ý tưởng trung tâm là `association discrepancy`: các điểm bình thường hình thành liên kết phong phú hơn với toàn bộ chuỗi, trong khi điểm bất thường có xu hướng chỉ liên kết tập trung với các điểm lân cận. Một chiến lược minimax được sử dụng để khuếch đại sự khác biệt giữa hai loại hành vi này.

## Dữ liệu

Bài báo đánh giá trên sáu bộ chuẩn phát hiện bất thường chuỗi thời gian không giám sát, trải rộng trên ba lĩnh vực ứng dụng: `service monitoring`, `space and earth exploration` và `water treatment`. Điều này khiến công trình có ý nghĩa đối với các bài toán phân tích chuỗi theo phong cách telemetry thực tế.

## Đánh giá

Mô hình được so sánh với các bộ phát hiện bất thường không giám sát tiên tiến trên nhiều bộ chuẩn. Cấu trúc đánh giá nhằm kiểm định liệu mô hình Transformer dựa trên liên kết có cải thiện chất lượng phát hiện bất thường trên các miền tuần tự đa dạng hay không.

## Kết quả

Bài báo báo cáo kết quả tốt nhất hiện thời trên sáu bộ dữ liệu chuẩn được nêu trong phần tóm tắt. Đóng góp chính của công trình là cho thấy cơ chế attention của Transformer có thể được chuyển hóa thành một tiêu chí phát hiện bất thường tường minh, thay vì chỉ đóng vai trò như bộ mã hóa chuỗi tổng quát.

## Hạn chế

Các mô hình dựa trên Transformer đòi hỏi chi phí tính toán cao hơn so với các đường cơ sở gọn nhẹ như Isolation Forest. Chúng cũng có thể khó biện minh trong một proof-of-concept quy mô nhỏ nếu lợi ích từ mô hình hóa thời gian không vượt trội rõ rệt so với phần phức tạp tăng thêm.

## Mức độ liên quan tới đề tài của chúng tôi

Bài báo tương thích trực tiếp với hướng `Transformer-based time-series model` trong đề xuất của chúng tôi. Công trình đặc biệt liên quan vì một trong các miền chuẩn mà nó đánh giá là `service monitoring`, vốn có sự tương đồng khái niệm rõ rệt với observability hạ tầng và AIOps.

## Hướng cải tiến khả dĩ

Trong dự án của chúng tôi, nên xem lớp mô hình này như một mở rộng nâng cao thay vì một đường cơ sở bắt buộc. Một hướng thực tiễn là so sánh chất lượng phát hiện và chi phí tính toán của nó với LSTM Autoencoder và Isolation Forest trên cùng một tập cửa sổ telemetry.
