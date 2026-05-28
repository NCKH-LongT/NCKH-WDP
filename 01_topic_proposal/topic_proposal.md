# Topic Proposal

## 1. Group Information

- Class: SE1820
- Group: 3
- Leader: Hồ Minh Nghĩa
- Members: Lê Quốc Huy, Phạm Trung Tín, Đàm Mạnh Dũng, Bùi Quang Vinh


## 2. Proposed Title

- English title: Parking Building Management System
- Vietnamese title: Hệ thống quản lý tòa nhà gửi xe

## 3. Application Domain

Ví dụ: Giao thông đô thị, Quản lý bãi đỗ xe, IoT / Smart Building

## 4. Problem Statement (Vấn đề thực tế)

Nhiều tòa nhà và bãi đỗ xe đô thị gặp các vấn đề sau:

- Khó khăn trong việc tìm chỗ trống, dẫn tới tắc nghẽn và lãng phí thời gian.
- Sử dụng không hiệu quả không gian đỗ (một số khu vực quá tải, một số bị bỏ trống).
- Quản lý thủ công gây sai sót trong theo dõi thu phí, báo cáo và phân bổ chỗ.
- Thiếu dự báo cầu dẫn tới lập kế hoạch không chính xác trong giờ cao điểm.

## 5. Target Users (Đối tượng người dùng)

- Người lái xe (khách đến tòa nhà, nhân viên, cư dân).
- Ban quản lý tòa nhà / bãi đỗ xe.
- Nhân viên thu phí và bảo trì.
- Ứng dụng quản lý trung tâm điều hành (dashboard cho quản lý).

## 6. Motivation (Lý do cần tích hợp AI)

- Tự động phát hiện và báo cáo tình trạng chỗ đỗ theo thời gian thực (giảm chờ tìm chỗ).
- Dự báo nhu cầu chỗ đỗ theo khung thời gian để tối ưu phân bổ và nhân lực.
- Tự động đọc biển số và hỗ trợ thu phí, giảm sai sót thủ công.
- Tối ưu lộ trình hướng dẫn và phân phối xe vào vị trí trống, giảm ùn tắc nội bộ.

## 7. Proposed AI Model / Method (Model AI dự kiến sử dụng)

- Computer Vision (object detection): YOLOv8 / EfficientDet để phát hiện xe và chỗ trống từ camera giám sát.
- OCR / ALPR (Automatic License Plate Recognition): OpenCV + Tesseract hoặc mô hình chuyên dụng để đọc biển số.
- Time-series forecasting: XGBoost / Prophet / LSTM để dự báo mật độ đỗ theo giờ/ngày.
- Optimization / Recommendation: heuristic hoặc học tăng cường nhẹ (RL) để gợi ý phân bổ chỗ và lộ trình nội bộ.
- Optional: Embeddings + similarity search cho lưu trữ lịch sử khách/xe và gợi ý (nếu cần tính năng cá nhân hóa).

## 8. System Features (Các chức năng chính)

1. Dashboard quản trị: hiển thị tỷ lệ lấp đầy, báo cáo, cảnh báo bất thường.
2. Real-time occupancy detection: cập nhật chỗ trống theo camera/sensor.
3. License plate recognition & automated billing.
4. Arrival prediction & smart guidance: gợi ý lộ trình cho lái xe đến chỗ trống gần nhất.
5. Historical analytics & forecasting: báo cáo sử dụng và dự báo nhu cầu.

## 9. Expected Contribution (Kết quả mong muốn)

1. Hệ thống prototype cho quản lý tòa nhà gửi xe hoạt động theo thời gian thực.
2. Mô-đun phát hiện chỗ trống và nhận diện biển số có độ chính xác thực tế (mục tiêu: >90% phát hiện, >85% OCR trong điều kiện chuẩn).
3. Mô hình dự báo ngắn hạn (theo giờ) giúp giảm thời gian tìm chỗ trung bình ít nhất 20%.
4. Dashboard báo cáo và cơ chế thử nghiệm so sánh với baseline (rule-based / sensor-only).

## 10. Evaluation Plan (tóm tắt)

- Dataset: Video/camera feed từ bãi đỗ xe (ghi nhãn chỗ trống), tập ảnh biển số, log truy cập thực tế.
- Baseline: Đếm sensor/đếm thủ công, hoặc TF-IDF không áp dụng (rule-based allocation).
- Metrics: Accuracy (detection), OCR accuracy, MAE/RMSE cho dự báo, time-to-park (giảm trung bình), user satisfaction (khảo sát).
- Procedure: Thu thập dữ liệu thực nghiệm nhỏ, đánh giá offline và thử nghiệm chạy demo trên một kịch bản mô phỏng.

## 11. Related Papers (gợi ý)

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | Real-time parking occupancy detection using deep learning | | | |
| 2 | Automatic license plate recognition for parking systems | | | |
| 3 | Short-term parking demand forecasting using machine learning | | | |

---


