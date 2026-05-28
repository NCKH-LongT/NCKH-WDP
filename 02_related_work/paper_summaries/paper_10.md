Tên bài: A Reservation-Based Smart Parking System (RSPS)

Tác giả: Trịnh Hoàng Minh, Nguyễn Đức Anh, và các cộng sự (Nghiên cứu về Hệ thống Giao thông Thông minh)

Năm xuất bản: 2011 / 2012 (Đồng bộ trên hệ thống IEEE Xplore và ResearchGate)

Nguồn: ResearchGate / IEEE Xplore

DOI/Link: https://www.researchgate.net/publication/224243220_A_Reservation-based_Smart_Parking_System

Problem
Bài báo giải quyết vấn đề gì?

Giải quyết sự thiếu hiệu quả của các bãi đỗ xe truyền thống khi không có cơ chế điều tiết dòng xe từ xa, khiến tài xế đổ dồn về bãi vào giờ cao điểm, gây ùn tắc nghiêm trọng tại cổng vào (check-in) và các trục đường đô thị lân cận.

Khắc phục bài toán lãng phí thời gian và nhiên liệu của tài xế khi phải "đánh cược" lái xe đến bãi mà không biết chắc chắn bên trong còn chỗ trống hay không.

Method
Bài báo dùng phương pháp/model/hệ thống nào?

Đề xuất một Hệ thống Quản lý Đặt chỗ Trước (Reservation-Based Smart Parking System - RSPS) sử dụng cấu trúc mạng phân tán.

Cơ chế hoạt động chính: Hệ thống cho phép người dùng kiểm tra trạng thái bãi xe và thực hiện giao dịch đặt giữ chỗ trước (reservation) thông qua ứng dụng/web trước khi khởi hành. Khi yêu cầu được gửi đi, thuật toán quản lý trung tâm sẽ khóa một ô đỗ trống trong một khoảng thời gian quy định (grace period) và gửi mã định danh (ID/Mã vạch) về cho tài xế để xác thực khi đến cổng.

Dataset
Bài báo dùng dữ liệu gì?

Dữ liệu mô phỏng trạng thái chu kỳ sống của ô đỗ xe (Parking slot states: Free, Reserved, Occupied).

Các tham số đầu vào bao gồm: Thời gian đặt chỗ (reservation time), thời gian dự kiến đến (estimated arrival time), thời gian đỗ (parking duration) và dữ liệu ID của người dùng.

Evaluation
Bài báo đánh giá bằng metric nào?

Reservation Success Rate (Tỷ lệ đặt chỗ thành công): Khả năng hệ thống xử lý đồng thời nhiều yêu cầu đặt chỗ mà không bị trùng lặp vị trí.

Average Waiting Time (Thời gian chờ trung bình tại cổng): Thời gian tối ưu hóa khi xe có mã đặt trước đi qua barrier so với xe vãng lai.

Trạng thái sử dụng bãi xe (Utilization Rate): Hiệu suất lấp đầy tối ưu của toàn bộ bãi đỗ.

Results
Kết quả chính là gì?

Hệ thống RSPS chứng minh khả năng giảm thiểu thời gian tìm kiếm chỗ đỗ của tài xế xuống mức tối đa vì vị trí đã được định đoạt trước khi xe lăn bánh.

Giảm đáng kể hiện tượng ùn ứ tại cổng kiểm soát nhờ quy trình xác thực mã đặt chỗ tự động diễn ra nhanh chóng, giúp luồng xe ra vào đô thị được điều tiết một cách nhịp nhàng.

Limitations
Hạn chế của bài báo là gì?

Do xuất bản ở giai đoạn trước, hệ thống chưa tối ưu hóa việc tự động hủy chỗ sâu sắc nếu tài xế đến trễ quá giờ (chưa có thuật toán phạt hoặc hoàn tiền linh hoạt).

Công nghệ xác thực tại cổng thời kỳ này còn dựa vào mã thủ công, chưa tích hợp nhận diện khuôn mặt hay camera AI để tự động mở barrier.

Relevance to our topic
Bài báo liên quan gì đến đề tài của nhóm?

Cung cấp tư duy thiết kế tính năng cốt lõi: Bài báo này cung cấp nền tảng lý thuyết và quy trình nghiệp vụ (Business Workflow) chuẩn cho tính năng Đặt chỗ trước (Booking/Reservation) trên ứng dụng di động mà nhóm bạn đang dự định phát triển cho tòa nhà gửi xe nhiều tầng.

Possible improvement
Nhóm có thể cải tiến hoặc mở rộng điểm nào?

Hiện đại hóa công nghệ bằng React Native & API: Thay vì hệ thống cũ, nhóm có thể code ứng dụng di động bằng React Native/Expo kết hợp cổng thanh toán trực tuyến (Momo, QR Code). Khi khách đặt chỗ thành công, hệ thống sinh ra một mã QR. At cổng vào, tài xế chỉ cần quét QR hoặc kết hợp với camera YOLOv8 tự nhận diện biển số đã đăng ký trong app để mở barrier hoàn toàn tự động (Zero-touch check-in).