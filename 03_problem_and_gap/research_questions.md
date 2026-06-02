# Câu hỏi nghiên cứu và Mục tiêu Xác thực (Research Questions & Objectives)

## 1. Câu hỏi nghiên cứu (Research Questions)

- **RQ1 (Khía cạnh Học máy):** Mô hình Machine Learning ứng dụng thuật toán XGBoost đạt được độ chính xác và hiệu suất phân tích là bao nhiêu khi dự đoán xác suất chiến thắng dựa trên tập dữ liệu lịch sử (thành tích, đặc trưng sinh học của ngựa, năng lực nài ngựa, và điều kiện trận đấu)?
- **RQ2 (Khía cạnh Hỗ trợ Quyết định):** Việc cung cấp các chỉ số dự báo xác suất khách quan từ Module AI có giúp cải thiện hiệu quả và thay đổi hành vi ra quyết định của người dùng (khán giả) so với phương pháp đánh giá truyền thống dựa trên trực giác hoặc bảng tỷ lệ cược tĩnh của nhà cái hay không?
- **RQ3 (Khía cạnh Vận hành Hệ thống):** Kiến trúc phần mềm đề xuất giúp tối ưu hóa hiệu quả quản lý giải đấu (thời gian xử lý thủ tục đăng ký, tính chính xác của việc ghi nhận kết quả và cập nhật bảng xếp hạng) như thế nào so với các quy trình phân mảnh trước đây?
- **RQ4 (Khía cạnh Tích hợp Hệ thống):** Việc kết hợp đồng bộ giữa Module AI và hệ thống quản lý phân quyền đa vai trò có tác động như thế nào đến tính minh bạch mang lại cho Ban tổ chức và mức độ hài lòng chung về trải nghiệm người dùng (UX)?

## 2. Mục tiêu và Phương pháp Xác thực (Evaluation Metrics & Methodology)

Để trả lời các câu hỏi nghiên cứu trên một cách khoa học, đề tài áp dụng các phương pháp đo lường chuẩn mực sau:

### 2.1. Đánh giá Định lượng Mô hình AI (Đối với RQ1)

Mô hình dự đoán không chỉ được đánh giá bằng các chỉ số phân loại đơn giản, mà áp dụng các bộ lọc kiểm định xác suất chặt chẽ theo tiêu chuẩn toán học của _Glenn W. Brier (1950)_:

- **Accuracy / Top-1 Accuracy:** Tỷ lệ lượt đua mô hình đoán chính xác vị trí Quán quân thực tế.
- **Top-3 Accuracy:** Tỷ lệ ngựa được mô hình xếp trong nhóm 3 cá thể có xác suất cao nhất, có kết quả thực tế nằm trong Top 3 (phù hợp với các thể thức cược Place/Show quốc tế).
- **Log Loss (Cross-Entropy Loss):** Đo lường mức độ sai lệch giữa xác suất dự báo và kết quả thực tế. Hàm phạt nặng các dự báo sai nhưng có độ tự tin cao ($p$ tiến về 1).
- **Brier Score (BS):** Chỉ số đo lường bình phương sai số của các dự báo xác suất đa lớp, đánh giá độ hiệu chuẩn (Calibration) của mô hình:

$$BS = \frac{1}{N} \sum_{i=1}^{N} \sum_{j=1}^{C} (p_{ij} - y_{ij})^2$$

> Trong đó:
>
> - $N$: Tổng số lượt đua đưa vào đánh giá.
> - $C$: Số lượng ngựa tham gia trong lượt đua $i$.
> - $p_{ij}$: Xác suất dự báo của mô hình cho việc cá thể ngựa $j$ sẽ chiến thắng ở lượt đua $i$.
> - $y_{ij}$: Nhãn thực tế (Nhận giá trị $1$ nếu ngựa $j$ thắng lượt đua $i$, và giá trị $0$ nếu ngược lại).
> - _Chỉ số $BS$ càng gần 0 thể hiện mô hình dự báo xác suất càng hoàn hảo._

### 2.2. Đánh giá Hiệu năng Hệ thống và Nghiệp vụ (Đối với RQ3)

- **Task Completion Time (TCT):** Đo lường và so sánh thời gian hoàn thành các tác vụ cốt lõi (Đăng ký thi đấu, phê duyệt hồ sơ nài/ngựa, khởi tạo lịch đấu tự động) trên hệ thống mới so với quy trình cũ.
- **Data Consistency Rate:** Đánh giá tỷ lệ đồng bộ và tính toàn vẹn của dữ liệu điểm số, bảng xếp hạng khi hệ thống tự động xử lý so với các điểm nghẽn nhập liệu thủ công trước đây.

### 2.3. Đánh giá Định tính và Trải nghiệm Người dùng (Đối với RQ2 & RQ4)

- **Thực nghiệm Kiểm chứng (A/B Testing mô phỏng):** Chia nhóm người dùng trải nghiệm hệ thống có và không có Module hỗ trợ từ AI để đánh giá mức độ thay đổi trong hành vi chọn lựa và tỷ lệ chiến thắng trong hệ thống cược ảo.
- **System Usability Scale (SUS):** Sử dụng thang đo SUS gồm 10 câu hỏi tiêu chuẩn quốc tế để khảo sát diện rộng, đánh giá độ thỏa dụng của giao diện Dashboard thống kê và các tính năng phân quyền hệ thống.

## 3. Tài liệu tham khảo (References)

- Brier, G. W. (1950). Verification of forecasts expressed in terms of probability. _Monthly Weather Review_, 78(1), 1-3.
