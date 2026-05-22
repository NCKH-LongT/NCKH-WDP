# Tóm tắt Bài báo 10

## Trích dẫn

Wei, Y., Jang-Jaccard, J., Xu, W., Sabrina, F., Camtepe, S., & Boulic, M. (2022). *LSTM-Autoencoder based Anomaly Detection for Indoor Air Quality Time Series Data*. arXiv. https://arxiv.org/abs/2204.06701

## Vấn đề nghiên cứu

Các phương pháp thống kê truyền thống và học máy nông thường gặp khó khăn trong việc phát hiện các bất thường phụ thuộc vào quan hệ thời gian dài hạn. Bài báo khảo sát liệu một mô hình `LSTM-Autoencoder` có thể cải thiện phát hiện bất thường trên dữ liệu chuỗi thời gian đa biến bằng cách học các phụ thuộc dài hạn và hành vi tái tạo hay không.

## Phương pháp

Mô hình được đề xuất kết hợp các lớp `LSTM` với một `Autoencoder`. Thành phần LSTM học các phụ thuộc thời gian xuyên suốt chuỗi, trong khi autoencoder sử dụng sai số tái tạo để xác định một mẫu là bình thường hay bất thường. Ngưỡng phát hiện bất thường được suy ra từ hành vi tái tạo trên dữ liệu chuỗi.

## Dữ liệu

Các thí nghiệm được thực hiện trên tập dữ liệu chuỗi thời gian chất lượng không khí trong nhà `Dunedin CO2`, được thu thập từ các triển khai thực tế tại trường học ở New Zealand. Dù miền ứng dụng không phải telemetry hạ tầng, cấu trúc dữ liệu vẫn là đa biến và có tính tuần tự.

## Đánh giá

Bài báo đánh giá mô hình so với các phương pháp phát hiện bất thường tương tự và báo cáo hiệu năng phân loại, với trọng tâm là kiểm định liệu mô hình tái tạo theo thời gian dạng lai này có thể nhận diện bất thường trong chuỗi một cách ổn định hay không.

## Kết quả

Nghiên cứu báo cáo độ chính xác rất cao, đạt `99.50%`, vượt qua các mô hình tương đương trên tập dữ liệu được khảo sát. Quan trọng hơn đối với đề tài của nhóm, bài báo chứng minh vì sao autoencoder dựa trên LSTM là một bộ phát hiện bất thường theo thời gian hợp lý khi các phụ thuộc dài hạn đóng vai trò đáng kể.

## Hạn chế

Miền ứng dụng của nghiên cứu là chất lượng không khí trong nhà thay vì hạ tầng tính toán, và độ phức tạp của telemetry máy chủ có thể khác biệt đáng kể so với dữ liệu cảm biến CO2. Độ chính xác cao trong một miền không tự động bảo đảm khả năng chuyển giao sang phát hiện bất thường hạ tầng.

## Mức độ liên quan tới đề tài của nhóm

Bài báo hữu ích vì đề xuất của nhóm đã nêu rõ `LSTM Autoencoder` như một mô hình ứng viên cho phát hiện bất thường. Công trình này củng cố trực giác rằng các mô hình tái tạo theo chuỗi có thể nắm bắt hành vi thời gian bất thường vượt ra ngoài các vi phạm ngưỡng đơn giản.

## Hướng cải tiến khả dĩ

Đối với dự án của nhóm, có thể điều chỉnh mô hình này cho các cửa sổ hạ tầng đa biến như CPU, bộ nhớ, mạng, lưu trữ và tín hiệu tình trạng container. Nhóm cũng nên đánh giá bằng các chỉ số ở mức sự kiện, vì độ chính xác tính theo điểm đơn lẻ có thể đánh giá quá cao tính hữu dụng trong vận hành thực tế.
