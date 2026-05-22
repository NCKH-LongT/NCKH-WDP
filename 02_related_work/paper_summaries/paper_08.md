# Tóm tắt Bài báo 08

## Trích dẫn

Vajda, D. L., Do, T. V., Berczes, T., & Farkas, K. (2024). *Machine learning-based real-time anomaly detection using data pre-processing in the telemetry of server farms*. *Scientific Reports, 14*, 23288. https://doi.org/10.1038/s41598-024-72982-z

## Vấn đề nghiên cứu

Trong các hệ thống telemetry, phát hiện bất thường phải đồng thời đạt độ chính xác và tốc độ cao. Nhiều phương pháp gần đây cho kết quả tốt trên các chỉ số ngoại tuyến nhưng chưa đủ nhanh cho vận hành thời gian thực, đặc biệt trong telemetry của cụm máy chủ, nơi người vận hành cần độ trễ phát hiện ở mức thấp.

## Phương pháp

Bài báo đề xuất hai thuật toán, `AnDePeD` và `AnDePeD Pro`. Ý tưởng cốt lõi là khai thác tính chu kỳ của tín hiệu telemetry thông qua bước tiền xử lý bằng `variational mode decomposition (VMD)`, sau đó áp dụng bộ phát hiện bất thường dựa trên `LSTM` lên chuỗi thời gian phần dư. Hệ thống được triển khai trong một testbed telemetry dựa trên `OpenTelemetry (OTel)`.

## Dữ liệu

Nhóm tác giả xây dựng một testbed telemetry cho một cụm máy chủ riêng, bao gồm web server, tác vụ huấn luyện AI, ứng dụng xử lý dữ liệu IoT và nền tảng phát triển. Ngoài ra, họ cũng sử dụng dữ liệu thu thập từ `AWS` và đánh giá trên các tập dữ liệu có tính chu kỳ phù hợp với kịch bản telemetry của server farm.

## Đánh giá

Các thuật toán được so sánh với những bộ phát hiện tiên tiến thông qua `Precision`, `Recall`, `F-score` và `MCC`. Bài báo đồng thời đánh giá `initialisation delay` và `detection delay`, là những tiêu chí đặc biệt quan trọng đối với môi trường vận hành thời gian thực.

## Kết quả

Bài báo cho thấy các phương pháp đề xuất đạt hiệu năng tương đương các đường cơ sở mạnh trên các chỉ số phân loại chuẩn, đồng thời vượt trội so với phần lớn phương án thay thế về độ trễ khởi tạo và độ trễ phát hiện. `AnDePeD Pro` được nhấn mạnh là bộ phát hiện tốt nhất trong số các mô hình được thử nghiệm xét theo tốc độ phát hiện, khiến nó đặc biệt hấp dẫn cho giám sát telemetry trong thực tế.

## Hạn chế

Cách tiếp cận này chuyên biệt cho telemetry có tính chu kỳ và phụ thuộc vào các lựa chọn tiền xử lý có thể không chuyển giao đồng đều sang mọi loại tín hiệu hạ tầng. Công trình cũng tập trung vào phát hiện bất thường ở phía backend hơn là tương tác bảo trì có con người trong vòng lặp.

## Mức độ liên quan tới đề tài của chúng tôi

Bài báo rất gần với bài toán backend của chúng tôi vì xử lý trực tiếp telemetry của server farm, phát hiện bất thường thời gian thực và bối cảnh triển khai hướng tới observability. Nghiên cứu này củng cố cơ sở biện minh cho việc sử dụng AI chuỗi thời gian trên các chỉ số hạ tầng đa biến trong trung tâm dữ liệu mô phỏng.

## Hướng cải tiến khả dĩ

Trong dự án của chúng tôi, có thể lấy cảm hứng từ bài báo này để đánh giá không chỉ độ chính xác phát hiện bất thường mà còn cả tính kịp thời của cảnh báo. Ngay cả khi không triển khai VMD, chúng tôi vẫn có thể kế thừa luận điểm rằng tiền xử lý và các chỉ số độ trễ là quan trọng khi điểm bất thường được dùng để hỗ trợ bảo trì có AR theo thời gian thực.
