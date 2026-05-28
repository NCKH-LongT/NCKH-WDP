# Paper 05 Summary

## Citation

- **Tên bài:** Design and build a hotel service reservation and verification system using web-based e-KTP
- **Tác giả:** Nghiên cứu viên / Tác giả thuộc lĩnh vực An ninh hệ thống (ResearchGate)
- **Năm:** 2023
- **Nguồn:** ResearchGate
- **DOI/Link:** [Link](https://www.researchgate.net/publication/376760701_Design_and_build_a_hotel_service_reservation_and_verification_system_using_web-based_e-KTP)

## Problem

Khi thực hiện đặt phòng khách sạn trực tuyến, việc xác thực danh tính khách hàng (Customer Identity Verification) là vô cùng quan trọng để ngăn chặn các hành vi giả mạo, lừa đảo, hoặc đặt phòng ảo (fake booking). Các phương thức xác thực truyền thống như chụp ảnh chứng minh thư thủ công thường tốn thời gian đối chiếu và không đảm bảo tính bảo mật dữ liệu cũng như tính chính danh của khách hàng trong thời gian thực.

## Method

Nghiên cứu đề xuất thiết kế và xây dựng một **Hệ thống đặt phòng và xác thực dịch vụ khách sạn dựa trên nền tảng Web tích hợp thẻ định danh điện tử e-KTP (electronic KTP)**:
- **Tích hợp phần cứng e-KTP Reader:** Hệ thống kết nối với đầu đọc thẻ căn cước công dân điện tử hoặc sử dụng API quét OCR thẻ căn cước điện tử.
- **Xác thực tự động (Automated Verification):** Dữ liệu từ thẻ e-KTP của khách hàng được đọc, đối chiếu và xác thực trực tiếp với cơ sở dữ liệu dân cư để kiểm tra tính hợp lệ trước khi cho phép kích hoạt mã đặt phòng.
- **Kiến trúc Web-based:** Vận hành linh hoạt trên trình duyệt web, đảm bảo cả khách hàng và lễ tân đều có thể truy cập kiểm tra trạng thái xác thực.

## Dataset

Hệ thống sử dụng dữ liệu thẻ căn cước điện tử e-KTP giả lập (hoặc thử nghiệm nội bộ trên mẫu thẻ thật) để kiểm tra tính năng kết nối đầu đọc thẻ và kiểm thử độ chính xác của luồng xác thực danh tính khách hàng đặt phòng.

## Evaluation

Hệ thống được đánh giá qua các chỉ số:
- **Thời gian xác thực (Verification Speed):** Thời gian cần thiết để đọc và xác thực danh tính của một khách hàng.
- **Độ chính xác xác thực (Authentication Accuracy):** Tỷ lệ nhận diện chính xác thẻ thật/thẻ giả và đối khớp thông tin cá nhân.
- **Tính bảo mật (Security):** Khả năng mã hóa dữ liệu cá nhân của khách hàng khi truyền tải trong hệ thống.

## Results

- Xây dựng thành công hệ thống đặt phòng trực tuyến có lớp bảo mật xác thực danh tính bằng thẻ căn cước điện tử e-KTP.
- Rút ngắn thời gian làm thủ tục xác thực danh tính khi nhận phòng (Check-in) xuống chỉ còn vài giây thông qua việc quét thẻ tự động thay vì nhập tay thủ công.
- Tăng cường độ an toàn và độ tin cậy của giao dịch đặt phòng, giảm thiểu tối đa tình trạng đặt phòng ảo.

## Limitations

- Hệ thống phụ thuộc nhiều vào hạ tầng phần cứng đọc thẻ căn cước điện tử e-KTP, gây khó khăn cho việc triển khai rộng rãi ở quy mô đặt phòng trực tuyến từ xa tại nhà (nơi khách hàng không có thiết bị đọc chuyên dụng).
- Chưa tích hợp AI để tự động nhận diện khuôn mặt đối khớp với ảnh trên thẻ căn cước (Face Matching).

## Relevance to our topic

- **Mức độ liên quan:** Trung bình (Domain Security Reference).
- **Lý do:** Bài báo gợi ý giải pháp bảo mật và xác thực thông tin khách hàng trong quy trình Check-in/Check-out của khách sạn. Đối với đề tài **SmartStay AI**, việc bảo mật thông tin và xác thực giao dịch qua ZaloPay hoặc nhận diện danh tính khách hàng là vô cùng quan trọng.

## Possible improvement

Áp dụng trực tiếp vào **SmartStay AI**:
1. Đối với luồng **Check-in thông minh**, thay vì dùng đầu đọc thẻ phần cứng phức tạp tại quầy, SmartStay AI sẽ áp dụng công nghệ **OCR (Optical Character Recognition) tích hợp AI** trên ứng dụng di động để khách hàng tự chụp ảnh Căn cước công dân (CCCD) và tự động trích xuất thông tin điền vào hồ sơ đặt phòng.
2. Tích hợp giải pháp xuất hóa đơn điện tử e-voucher bằng **Mã QR định danh bảo mật** được gửi qua email/Zalo của khách hàng sau khi thanh toán thành công qua ZaloPay, giúp lễ tân quét QR code xác thực check-in cực kỳ nhanh chóng.
