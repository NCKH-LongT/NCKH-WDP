# Phát biểu vấn đề nghiên cứu (Problem Statement)

## 1. Bối cảnh và Thách thức trong Quản lý Giải đua ngựa

Đua ngựa là một ngành công nghiệp thể thao và giải trí có cấu trúc vận hành phức tạp, đòi hỏi sự phối hợp đồng bộ và quản lý chặt chẽ giữa nhiều thực thể: Ban tổ chức, Chủ ngựa, Nài ngựa (Jockey), Trọng tài và Khán giả. Trong một giải đấu diễn ra liên tục, khối lượng nghiệp vụ hành chính và kỹ thuật cần xử lý vô cùng lớn, bao gồm: xác thực hồ sơ sinh trắc học và phong độ của ngựa, phân lịch thi đấu theo hạng cân/độ tuổi, ghi nhận kết quả thời gian thực (real-time), tính điểm xếp hạng tổng sắp, và vận hành hệ thống đặt cược.

Tuy nhiên, thực trạng quản lý tại nhiều trường đua hiện nay vẫn đang đối mặt với tình trạng **phân mảnh công nghệ (Technology Fragmentation)**. Việc lạm dụng các phương pháp thủ công hoặc các hệ thống phần mềm quản lý rời rạc (Silos) đã dẫn đến những hệ lụy nghiêm trọng sau:

- **Bất đối xứng thông tin (Information Asymmetry):** Do dữ liệu bị lưu trữ phân tán, quy trình đăng ký, xác nhận tư cách tham gia của nài ngựa và ngựa tốn rất nhiều thời gian, dễ dẫn đến hiện tượng sai sót hoặc làm giả hồ sơ thi đấu.
- **Rủi ro về tính toàn vẹn dữ liệu (Data Integrity Risks):** Việc cập nhật kết quả thủ công sau mỗi lượt đua làm tăng tỷ lệ sai lệch dữ liệu do yếu tố con người, ảnh hưởng trực tiếp đến tính khách quan, minh bạch và uy tín của Ban tổ chức.
- **Thiếu công cụ hỗ trợ quyết định dựa trên dữ liệu (Data-driven Decision Making):** Khán giả và các nhà phân tích thiếu các công cụ khách quan để đánh giá xác suất chiến thắng của từng cá thể ngựa trước cuộc đua. Quy trình này hiện tại phần lớn phụ thuộc vào cảm tính cá nhân hoặc các bảng tỷ lệ cược (odds) tĩnh do nhà cái cấu hình, vốn mang nặng tính thương mại và thiếu cơ sở khoa học dữ liệu.

## 2. Cơ hội từ Dữ liệu lớn và Trí tuệ Nhân tạo (AI)

Trong kỷ nguyên chuyển đổi số, dữ liệu lịch sử về thành tích thi đấu, đặc trưng sinh học của ngựa, năng lực của nài ngựa, cùng các biến số môi trường như điều kiện thời tiết và kết cấu mặt sân đang được thu thập ngày một dày đặc. Đây là nguồn tài nguyên cốt lõi để ứng dụng các mô hình Học máy (Machine Learning) nhằm chuyển hóa dữ liệu thô thành các dự báo xác suất có giá trị cao.

Do đó, bài nghiên cứu này đặt ra yêu cầu cấp thiết: **Xây dựng một nền tảng Web quản lý giải đua ngựa toàn diện có tích hợp mô hình AI** nhằm tối ưu hóa quy trình vận hành hành chính, đồng thời cung cấp khả năng dự đoán xác suất chiến thắng chính xác, hỗ trợ người dùng đưa ra quyết định dựa trên cơ sở khoa học.

## 3. Tầm quan trọng của vấn đề (Significance of the Study)

Việc giải quyết triệt để bài toán này mang lại các giá trị thực tiễn và học thuật sau:

1.  **Về mặt vận hành (Operational Efficiency):** Số hóa và tự động hóa toàn bộ vòng đời giải đấu, tối ưu hóa thời gian xử lý thủ tục cho Ban tổ chức, đồng thời đảm bảo tính minh bạch, chống gian lận trong thể thao thể thức đối kháng.
2.  **Về mặt trải nghiệm người dùng (UX):** Cung cấp cho khán giả một góc nhìn khách quan, khoa học thông qua các chỉ số dự báo từ AI, từ đó nâng cao tính tương tác và niềm tin vào giải đấu.
3.  **Về mặt học thuật và kỹ thuật:** Đề tài đóng vai trò là một case-study thực tế minh họa cách thức nhúng (embed) một pipeline Học máy dạng toán xác suất vào quy trình nghiệp vụ của một hệ thống doanh nghiệp (Enterprise System), thay vì chỉ dừng lại ở mức mô hình nghiên cứu độc lập trên môi trường thử nghiệm (Sandbox).
