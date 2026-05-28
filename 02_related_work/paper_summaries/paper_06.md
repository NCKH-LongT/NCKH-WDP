Tên bài: Predictive Smart Parking Availability System Using Machine Learning

Tác giả: Navinkumar Dhopre, Aishwarya Godre, Durga Mundhe, Sadhana Somwanshi, Shital Musmade

Năm xuất bản: 2024 (Đồng bộ mã hóa IEEE Xplore: 10443421)

Nguồn: International Research Journal of Engineering and Technology (IRJET), Tập 13, Số 04

DOI/Link: https://www.irjet.net/archives/V13/i4/IRJET-V13I04148.pdf

Problem
Bài báo giải quyết vấn đề gì?

Giải quyết tình trạng khó khăn khi tìm kiếm vị trí đỗ xe tại các đô thị lớn đông dân cư – nguyên nhân chính dẫn đến ùn tắc giao thông, lãng phí nhiên liệu và gia tăng ô nhiễm môi trường.

Khắc phục nhược điểm của các hệ thống quản lý truyền thống: Các hệ thống cũ chỉ hiển thị trạng thái trống/đầy tại thời điểm hiện tại (tính tĩnh), hoàn toàn thiếu năng lực dự báo xu hướng dòng xe trong tương lai để hỗ trợ tài xế chủ động lên kế hoạch di chuyển.

Method
Bài báo dùng phương pháp/model/hệ thống nào?

Nghiên cứu đề xuất một kiến trúc hệ thống đa tầng (Multi-tier Architecture) bao gồm:

Tầng Xử lý AI/Machine Learning: Áp dụng các thuật toán học máy có giám sát (Supervised Machine Learning) để phân tích, khai phá dữ liệu và nhận diện quy luật lấp đầy bãi xe.

Tầng Ứng dụng & Tương tác: Xây dựng nền tảng Web-based tích hợp bản đồ thông qua Google Maps API để trực quan hóa dữ liệu. Hệ thống cung cấp các phân hệ chức năng: Tìm kiếm vị trí bãi đỗ, hiển thị biểu đồ trạng thái dự báo và thực hiện nghiệp vụ đặt chỗ trước (Reservation system).

Dataset
Bài báo dùng dữ liệu gì?

Sử dụng tập dữ liệu lịch sử đỗ xe (Historical parking dataset).

Các thuộc tính/đặc trưng đầu vào (Input features) dùng để huấn luyện mô hình bao gồm: Ngày trong tháng, khung thời gian trong ngày (timestamp), các ngày trong tuần (thứ hai - chủ nhật), mã định danh vị trí đỗ (parking slot ID) và lịch sử mật độ chiếm dụng (occupancy patterns).

Evaluation
Bài báo đánh giá bằng metric nào?

Thay vì tập trung vào các chỉ số định lượng thuần túy của mô hình học máy (như Accuracy, F1-Score), nghiên cứu tập trung đánh giá tính thực tiễn và độ ổn định vận hành của phần mềm (Software Engineering Metrics).

Hệ thống được kiểm thử toàn diện qua 3 giai đoạn: Kiểm thử đơn vị (Unit Testing), Kiểm thử tích hợp (Integration Testing), và Kiểm thử toàn trình (End-to-End Testing) nhằm bảo đảm luồng dữ liệu giữa API dự báo, hệ thống bản đồ và cổng thanh toán/đặt chỗ hoạt động không có lỗi.

Results
Kết quả chính là gì?

Mô hình học máy đã học và nhận diện thành công các quy luật di chuyển của dòng xe theo chuỗi thời gian, đưa ra các kết quả dự báo có độ tin cậy cao về số ô đỗ còn trống tiếp theo.

Về mặt công nghệ phần mềm, hệ thống đã tối ưu hóa trải nghiệm người dùng (UX/UI): Giao diện web chạy mượt mà, cho phép tài xế định vị bãi đỗ trên bản đồ, xem dự báo xu hướng đông đúc và hoàn tất quy trình đặt giữ chỗ trước với độ trễ thao tác cực thấp.

Limitations
Hạn chế của bài báo là gì?

Hệ thống hiện tại mới chỉ triển khai trên nền tảng Web, chưa có ứng dụng di động độc lập (Dedicated Mobile App) để tài xế tiện thao tác khi đang lái xe.

Năng lực phát hiện ô trống hoàn toàn dựa trên dữ liệu lịch sử tích lũy, chưa được tích hợp hệ thống cảm biến phần cứng thời gian thực (Real-time IoT sensors) để cập nhật biến động tức thời.

Relevance to our topic
Bài báo liên quan gì đến đề tài của nhóm?

Trùng khớp trực tiếp về bài toán cốt lõi: Giải quyết vấn đề vận hành, điều phối dòng xe ra vào liên tục tại các đô thị lớn thông qua phần mềm thông minh.

Cung cấp Logic nghiệp vụ (Business Logic): Bài báo cung cấp quy trình thiết kế tính năng "Đặt chỗ trước" (Reservation) và giải pháp hiển thị trạng thái trực quan – đây là các tính năng bắt buộc phải có cho phần mềm quản lý tòa nhà gửi xe nhiều tầng của nhóm.

Possible improvement
Nhóm có thể cải tiến hoặc mở rộng điểm nào?

Nâng cấp nền tảng di động: Chuyển đổi và phát triển hệ thống thành ứng dụng di động đa nền tảng (Mobile App sử dụng React Native/Expo) để tài xế dễ dàng sử dụng ngay trên xe.

Tích hợp Thị giác máy tính thời gian thực: Thay vì chỉ dùng dữ liệu lịch sử hoặc cảm biến IoT đắt đỏ, nhóm có thể kết hợp với mô hình YOLOv8 (từ bài báo trước) để quét camera tại các tầng bãi xe, tự động cập nhật trạng thái trống/đầy theo thời gian thực (Real-time data stream) trực tiếp vào mô hình dự báo Machine Learning.

Nâng cấp thuật toán AI: Ứng dụng các mô hình học sâu chuyên cho dữ liệu chuỗi thời gian như LSTM hoặc GRU để tăng độ chính xác cho tính năng dự báo chỗ trống vào các khung giờ cao điểm của tòa nhà.