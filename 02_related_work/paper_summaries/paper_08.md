# Citation

- **Title:** Enhancing Horse Racing Outcome Prediction through Feature Selection and Machine Learning Techniques
- **Authors:** Dr. B.Lavanya
- **Year:** 2024
- **Source:** Journal of Artificial Intelligence and Data Science Techniques
- **DOI/Link:** Enhancing Horse Racing Outcome Prediction through Feature Selection and Machine Learning Techniques

# Problem

- Dự đoán kết quả đua ngựa cực kỳ đau đầu vì có quá nhiều biến số đan xen (phong độ ngựa, tay nghề nài, thời tiết, loại sân).
- Các phương pháp thống kê cũ bị "ngợp" và quá tải trước lượng dữ liệu khổng lồ và chứa nhiều thông tin nhiễu.

# Method

- Đề xuất mô hình FSSVM-HR: Kết hợp thuật toán RFE để tự động lọc bỏ các thuộc tính thừa/nhiễu và dùng thuật toán SVM làm lõi để phân loại ngựa thắng/thua.
- So sánh thực nghiệm với 3 thuật toán AI khác: CNN, ANN, và Random Forest để tìm ra mô hình tối ưu nhất.

# Dataset

- Nguồn dữ liệu đua ngựa quốc tế lấy từ Kaggle.
- Các thuộc tính chính: Tên sân (course), nài ngựa (jockeyName), ngựa (horseName, Age), điều kiện mặt sân (condition), cân nặng cõng (weightLb), điểm phong độ lịch sử (OR/RPRc) và tỷ lệ cược (Decimal price).
- Biến mục tiêu cần đoán: Ngựa thắng (res_win) hoặc lọt top vị trí (res_place).

# Evaluation

- Đánh giá bằng các chỉ số chuẩn của AI (Accuracy, Precision, Recall, F1-Score).
- Tập trung mạnh vào Accuracy (độ chính xác tổng thể) và Specificity (độ đặc hiệu – khả năng lọc trúng những con ngựa chắc chắn thua).

# Results

- **SVM (Mô hình đề xuất):** Thắng tuyệt đối với 96% Accuracy và 95% Specificity.
- **CNN:** Đứng nhì với 85% Accuracy.
- **Random Forest:** Đạt 73% Accuracy nhưng lọc ngựa thua khá tốt (83% Specificity).
- **ANN:** Hiệu suất tệ nhất, độ đặc hiệu chỉ đạt 62% (gần như bất lực trong việc đoán ngựa thua).

# Limitations

- Dữ liệu mới chỉ đóng khung trong các thông số cơ bản của trận đấu, chưa mở rộng ra các yếu tố môi trường bên ngoài hoặc bối cảnh khác.
- Chưa thử nghiệm hết các tùy chỉnh kiến trúc nâng cao để tối ưu thêm mô hình.

# Relevance to our topic

- **Thiết kế Database chuẩn:** Bài báo cung cấp sẵn một bộ thuộc tính (Schema mẫu) rất thực tế để nhóm định hình cấu trúc các bảng/collections dữ liệu trên hệ thống web.
- **Xác thực tính khả thi:** Chứng minh bằng số liệu rằng việc nhúng một microservice AI (lõi SVM) vào Web qua API để làm tính năng "Giả lập giải đua" hay "Gợi ý kèo cược" là hoàn toàn khả thi với độ chính xác cao.

# Possible improvement

- **Tích hợp Bio-data:** Nhóm có thể mở rộng bằng cách nạp thêm dữ liệu sinh học thực tế của ngựa (nhịp tim, tần số sải chân, lịch sử chấn thương) thay vì chỉ dùng dữ liệu kết quả thô như bài báo.
- **Xây dựng AI dạng Kết hợp (Ensemble):** Phối hợp thế mạnh của cả SVM (chính xác cao) và Random Forest (độ bền vững dữ liệu) để tạo ra một bộ lọc kép, chạy Real-time trực tiếp trên Dashboard của trang quản trị.
