# Paper 01 Summary

## Citation
*   **Tên bài:** Predictive Smart Parking Availability System Using Machine Learning.
*   **Tác giả:** Navinkumar Dhopre, Aishwarya Godre, Durga Mundhe, Sadhana Somwanshi, Shital Musmade.
*   **Năm:** Tháng 4 năm 2026.
*   **Nguồn:** International Research Journal of Engineering and Technology (IRJET), Tập 13, Số 04.
*   **DOI/Link:** https://www.irjet.net/archives/V13/i4/IRJET-V13I04148.pdf.

## Problem
**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết vấn đề khó khăn trong việc tìm kiếm bãi đỗ xe ở các khu vực đô thị đông đúc, nguyên nhân dẫn đến ùn tắc giao thông, lãng phí nhiên liệu và ô nhiễm môi trường. Các hệ thống đỗ xe truyền thống thường chỉ cung cấp thông tin về tình trạng chỗ trống hiện tại mà thiếu đi khả năng dự báo tình trạng đỗ xe trong tương lai để hỗ trợ tài xế.

## Method
**Bài báo dùng phương pháp/model/hệ thống nào?**
Nghiên cứu đề xuất **Hệ thống dự đoán chỗ đỗ xe thông minh (Predictive Smart Parking Availability System)** sử dụng kiến trúc đa tầng (multi-tier architecture):
*   **Mô hình Học máy (Machine Learning):** Sử dụng các thuật toán học máy có giám sát (supervised machine learning algorithms) để phân tích quy luật từ dữ liệu đỗ xe.
*   **Hệ thống tương tác:** Xây dựng một nền tảng web tích hợp bản đồ (Google Maps API) giúp hiển thị trực quan tình trạng và dự đoán bãi đỗ xe cho nhiều địa điểm. Hệ thống cho phép người dùng tìm kiếm, xem tình trạng dự đoán và tiến hành đặt trước chỗ đỗ xe.

## Dataset
**Bài báo dùng dữ liệu gì?**
Hệ thống sử dụng **dữ liệu đỗ xe trong quá khứ (historical parking data)**. Các đặc trưng đầu vào (input features) để huấn luyện mô hình bao gồm: ngày, thời gian trong ngày, ngày trong tuần, thông tin định danh vị trí đỗ xe và lịch sử mức độ sử dụng bãi đỗ (occupancy patterns/records).

## Evaluation
**Bài báo đánh giá bằng metric nào?**
Bài báo không đánh giá mô hình bằng các metric định lượng truyền thống của học máy (như Accuracy, F1-score). Thay vào đó, hệ thống được đánh giá tính khả thi thông qua các phương pháp **kiểm thử phần mềm (Testing)** bao gồm: Kiểm thử đơn vị (Unit tests), Kiểm thử tích hợp (Integration tests) và Kiểm thử toàn trình (End-to-end testing) nhằm đảm bảo hệ thống đặt chỗ, hiển thị bản đồ, tính bảo mật và API dự đoán vận hành chính xác, ổn định trong nhiều điều kiện khác nhau.

## Results
**Kết quả chính là gì?**
Hệ thống đã kết hợp thành công việc xử lý dữ liệu lịch sử và huấn luyện mô hình học máy để nhận diện quy luật đỗ xe theo thời gian và vị trí, từ đó cung cấp các dự báo hữu ích. Về mặt người dùng, giao diện web hoạt động hiệu quả, trực quan, cho phép đăng ký, tìm kiếm, xem dự báo trên bản đồ và hoàn tất việc đặt chỗ trước một cách nhanh chóng với các thao tác tối giản.

## Limitations
**Hạn chế của bài báo là gì?**
Dựa trên những định hướng phát triển ở phần kết luận, hệ thống hiện tại chưa có ứng dụng di động riêng biệt (dedicated mobile application), chưa tích hợp dữ liệu thời gian thực từ hệ thống cảm biến IoT để tối ưu hóa việc phát hiện chỗ đỗ, và năng lực dự đoán vẫn còn có thể nâng cấp thêm thay vì chỉ dùng các thuật toán học máy tiêu chuẩn hiện tại.

## Relevance to our topic
**Bài báo liên quan gì đến đề tài của nhóm?**
Bài báo này có mức độ liên quan mật thiết nếu đề tài của nhóm bạn tập trung vào: **Bãi đỗ xe thông minh (Smart Parking)**, xây dựng **Hệ thống giao thông thông minh (ITS)**, ứng dụng **Machine Learning** để dự đoán dữ liệu giao thông, hoặc phát triển nền tảng ứng dụng web tích hợp đặt chỗ và bản đồ định vị.

## Possible improvement
**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Từ những gợi ý của tác giả, nhóm có thể mở rộng đề tài của mình bằng cách:
*   Phát triển **ứng dụng di động (mobile app)** thay vì chỉ giới hạn ở nền tảng web.
*   Tích hợp trực tiếp **dữ liệu cảm biến IoT theo thời gian thực (real-time IoT sensor data)** để kết hợp với mô hình học máy nhằm nhận diện tính trạng chiếm dụng của bãi đỗ xe chính xác và tức thời hơn.
*   Nghiên cứu ứng dụng các **mô hình học sâu tiên tiến (advanced deep learning models)** để nâng cao độ chuẩn xác của việc dự báo chỗ trống.