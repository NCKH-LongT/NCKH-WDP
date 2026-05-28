# Paper 07 Summary

## Citation

- **Tên bài:** Optimizing guest experience in smart hospitality: Integrated fuzzy-AHP and machine learning for centralized hotel operations with IoT
- **Tác giả:** Nghiên cứu viên ngành Công nghệ khách sạn thông minh (ScienceDirect)
- **Năm:** 2024
- **Nguồn:** Alexandria Engineering Journal (ScienceDirect), Elsevier
- **DOI/Link:** [Link](https://www.sciencedirect.com/science/article/pii/S1110016824015229?via%3Dihub)

## Problem

Bài báo giải quyết vấn đề tối ưu hóa trải nghiệm khách hàng trong mô hình khách sạn thông minh tích hợp thiết bị kết nối vạn vật (IoT). Thách thức lớn nhất là làm thế nào để liên kết dòng dữ liệu khổng lồ từ các thiết bị cảm biến phần cứng IoT với việc đánh giá, dự báo chính xác mức độ hài lòng của khách hàng đối với từng dịch vụ cụ thể (như nhiệt độ phòng, ánh sáng, dịch vụ dọn dẹp) để đưa ra các điều chỉnh vận hành kịp thời.

## Method

Nghiên cứu đề xuất một kiến trúc hệ thống khách sạn thông minh tập trung (Centralized Smart Hotel Operations) kết hợp đồng thời ba thành phần công nghệ:
1. **Hạ tầng IoT & Nhận dạng khuôn mặt (Face Recognition):** Tích hợp camera AI thông minh tại sảnh đón tiếp để tự động nhận dạng khuôn mặt khách hàng và thực hiện quy trình Check-in tự động không tiếp xúc.
2. **Phương pháp Quyết định đa tiêu chí Delphi mờ (Fuzzy Analytic Hierarchy Process - FAHP):** Sử dụng để xác định trọng số và phân cấp mức độ quan trọng của các yếu tố ảnh hưởng trực tiếp đến trải nghiệm khách hàng (tiện nghi phòng ngủ, thái độ phục vụ, tốc độ internet).
3. **Mô hình Học máy (Machine Learning):** Sử dụng các mô hình học máy có giám sát gồm Mạng nơ-ron sâu (DNN - Deep Neural Network) và Rừng ngẫu nhiên (RF - Random Forest) để dự đoán mức độ hài lòng tổng thể của khách hàng dựa trên dữ liệu hành vi thu thập được từ IoT.

## Dataset

Bộ dữ liệu thực nghiệm bao gồm các thông số trạng thái thiết bị IoT thu thập từ các phòng khách sạn thông minh (nhiệt độ, độ ẩm, số lần bật/tắt thiết bị) kết hợp với bảng khảo sát phản hồi đánh giá trực tiếp của khách hàng sau khi lưu trú tại hệ thống khách sạn thử nghiệm.

## Evaluation

Hiệu năng của mô hình dự báo học máy được đo lường bằng các chỉ số lỗi thống kê tiêu chuẩn:
- **MSE (Mean Squared Error - Sai số bình phương trung bình)**
- **RMSE (Root Mean Squared Error - Căn sai số bình phương trung bình)**
- **R-squared ($R^2$ - Hệ số xác định)**

## Results

- Thiết lập thành công luồng nhận dạng khuôn mặt hỗ trợ Check-in tự động, rút ngắn thời gian xếp hàng làm thủ tục tại sảnh từ 15 phút xuống dưới 1 phút.
- Mô hình **Rừng ngẫu nhiên (Random Forest)** cho kết quả dự báo mức độ hài lòng của khách hàng vượt trội và ổn định hơn so với mạng DNN truyền thống (đạt chỉ số MSE và RMSE thấp hơn đáng kể, hệ số $R^2$ tiệm cận 0.90).
- Hệ thống hỗ trợ ban quản lý khách sạn tự động tối ưu hóa các thiết bị điều hòa, ánh sáng trong phòng dựa trên thói quen của khách, giúp tiết kiệm 20% điện năng vận hành.

## Limitations

- Chi phí đầu tư ban đầu cho hạ tầng thiết bị cảm biến phần cứng IoT và camera nhận diện khuôn mặt chuyên dụng rất lớn, khiến mô hình này khó áp dụng ngay cho phân khúc các khách sạn vừa, nhỏ hoặc homestay tự vận hành.

## Relevance to our topic

- **Mức độ liên quan:** Cao (Hybrid Technical Reference).
- **Lý do:** Bài báo cung cấp cái nhìn thực chứng về việc sử dụng các mô hình Machine Learning dự báo trải nghiệm người dùng và tự động hóa Check-in. Điều này củng cố định hướng phát triển các module thông minh cho hệ thống **SmartStay AI**.

## Possible improvement

Áp dụng trực tiếp vào **SmartStay AI**:
1. Đối với phiên bản v1.0 của **SmartStay AI** (tập trung vào tối ưu chi phí), thay vì dùng phần cứng camera IoT đắt đỏ, chúng tôi sẽ triển khai tính năng **Check-in bằng mã QR E-voucher** và tự động hóa gửi thông tin phòng qua Email/Zalo.
2. Ứng dụng mô hình phân tích và dự báo cảm xúc đơn giản (Sentiment Analysis) trên tập dữ liệu phản hồi dạng text của khách để đưa ra điểm số hài lòng tức thì, giúp ban quản lý nắm bắt nhanh xu hướng trải nghiệm của khách hàng mà không cần cài đặt cảm biến IoT.
