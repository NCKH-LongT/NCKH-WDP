# Tóm tắt Bài báo 12

## Trích dẫn

Lim, B., Arik, S. O., Loeff, N., & Pfister, T. (2019). *Temporal Fusion Transformers for Interpretable Multi-horizon Time Series Forecasting*. arXiv. https://arxiv.org/abs/1912.09363

## Vấn đề nghiên cứu

Dự báo đa chân trời là một bài toán khó khi dữ liệu đồng thời chứa biến đồng biến tĩnh, tín hiệu lịch sử và các đầu vào tương lai đã biết trước. Nhiều mô hình dự báo sâu đạt kết quả tốt nhưng vận hành như các "hộp đen", làm hạn chế giá trị của chúng đối với hỗ trợ ra quyết định trong thực tế.

## Phương pháp

Bài báo đề xuất `Temporal Fusion Transformer (TFT)`, một kiến trúc dựa trên attention kết hợp các lớp hồi tiếp để xử lý động học thời gian cục bộ với cơ chế self-attention có khả năng diễn giải đối với các phụ thuộc dài hạn. Mô hình cũng sử dụng các mạng chọn biến và cơ chế gating để triệt tiêu thành phần không cần thiết và nâng cao tính diễn giải.

## Dữ liệu

Đây là một công trình phương pháp luận về dự báo, được đánh giá trên nhiều bộ dữ liệu thực tế thay vì gắn với một miền ứng dụng duy nhất. Mục tiêu của bài báo là xác lập một kiến trúc dự báo tổng quát cho các bối cảnh chuỗi thời gian đa biến phức tạp.

## Đánh giá

Bài báo so sánh TFT với các chuẩn dự báo nhiều bước hiện có và đồng thời minh họa các trường hợp sử dụng liên quan đến tính diễn giải. Vì vậy, phần đánh giá xem xét cả hiệu năng dự báo lẫn mức độ hữu ích của mô hình trong việc hiểu động học thời gian và tầm quan trọng của đặc trưng.

## Kết quả

Nghiên cứu báo cáo sự cải thiện đáng kể về hiệu năng so với các chuẩn hiện hữu trên nhiều bộ dữ liệu thực tế. Bài báo cũng trình bày ba trường hợp sử dụng thực tiễn liên quan đến tính diễn giải, khiến TFT trở nên hấp dẫn trong những bối cảnh đòi hỏi vừa có chất lượng dự báo cao vừa có hành vi mô hình dễ hiểu.

## Hạn chế

TFT phức tạp hơn các mô hình dự báo LSTM đơn giản hơn và có thể đòi hỏi nhiều dữ liệu, công sức tinh chỉnh và tài nguyên tính toán hơn. Đối với một proof-of-concept ở quy mô sinh viên, gánh nặng triển khai có thể tương đối cao nếu chức năng dự báo chỉ là một phần mở rộng thứ cấp.

## Mức độ liên quan tới đề tài của nhóm

Bài báo liên quan trực tiếp vì `TFT` đã được liệt kê trong đề xuất của nhóm như một lựa chọn phân tích dự báo nâng cao. Công trình cung cấp cơ sở nghiên cứu vững chắc cho phần hỗ trợ dự báo của hệ thống, đặc biệt nếu nhóm muốn biểu diễn các xu hướng rủi ro có khả năng diễn giải thay vì chỉ sử dụng các dự báo dạng hộp đen.

## Hướng cải tiến khả dĩ

Trong dự án của nhóm, TFT nên được định vị như một mô hình so sánh nâng cao sau khi một đường cơ sở dự báo đơn giản hơn đã vận hành ổn định. Một ứng dụng thực tế là dự báo quỹ đạo ngắn hạn của CPU, bộ nhớ hoặc tình trạng lưu trữ, đồng thời hiển thị các tác nhân ảnh hưởng quan trọng nhất trên dashboard hoặc lớp phủ AR.
