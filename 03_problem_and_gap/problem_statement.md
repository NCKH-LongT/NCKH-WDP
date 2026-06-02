# Phát biểu Vấn đề

## 1. Bối cảnh

Các cuộc thi học thuật — bao gồm hackathon, cuộc thi nghiên cứu và triển lãm dự án — đóng vai trò quan trọng trong giáo dục đại học, khuyến khích tinh thần đổi mới và kỹ năng ứng dụng của sinh viên. Tại Đại học FPT (Việt Nam), các cuộc thi này thường có hàng chục đội thi phân thành nhiều bảng, được điều phối bởi quản trị viên, mentor và giám khảo qua nhiều vòng thi kéo dài vài tuần.

## 2. Các Vấn đề Đã Xác định

### 2.1. Thực thi Timeline Không Chính xác

Các mốc cuộc thi — thời hạn nộp bài, chuyển tiếp vòng thi và cửa sổ thông báo — hiện được quản trị viên giám sát thủ công. Điều này dẫn đến sai lệch về thời gian và tạo cơ sở cho tranh cãi về sự công bằng khi deadline không được thực thi đúng giờ.

### 2.2. Chi phí Truyền thông Quá cao và Không Nhất quán

Quản trị viên phải soạn và gửi email thông báo cho từng mốc cuộc thi:

- **Thông báo vào chung kết**: thông báo cho các đội vào vòng tiếp theo
- **Nhắc deadline**: cảnh báo tất cả các đội về thời hạn nộp bài sắp đến
- **Cảnh báo chưa nộp bài**: thông báo cho đội chưa nộp trước một thời điểm quy định
- **Thông báo phân công mentor**: thông báo cho đội và mentor về cặp ghép của họ

Mỗi email hiện được viết tay với chất lượng, giọng điệu và độ đầy đủ thông tin khác nhau. Ở quy mô 30+ đội, quy trình này chiếm nhiều thời gian quản trị và tạo ra truyền thông không đồng nhất, dẫn đến nhầm lẫn và khiếu nại.

### 2.3. Chuẩn bị Giám khảo Tốn thời gian và Không Nhất quán

Trước mỗi buổi vấn đáp, từng giám khảo phải tự đọc báo cáo dự án và soạn câu hỏi phỏng vấn phù hợp. Quy trình này:

- Tốn nhiều thời gian (30–60 phút mỗi dự án với giám khảo có kinh nghiệm)
- Tạo ra câu hỏi có chất lượng rất khác nhau tùy thuộc kinh nghiệm và thời gian của từng giám khảo
- Có thể dẫn đến câu hỏi bề mặt hoặc chung chung nếu giám khảo thiếu thời gian chuẩn bị
- Tạo điều kiện đánh giá không bình đẳng giữa các giám khảo khác nhau trong cùng cuộc thi

### 2.4. Thiếu Nền tảng Tích hợp

Hiện nay, dữ liệu cuộc thi được quản lý trên các công cụ rời rạc: bảng tính, email và form nhập điểm riêng lẻ. Không có hệ thống thống nhất nào tích hợp đăng ký, quản lý bảng thi, phân công mentor, chấm điểm và truyền thông. Sự phân mảnh này dẫn đến:

- Lỗi đồng bộ dữ liệu
- Cập nhật trạng thái chậm cho thí sinh
- Khó theo dõi tiến độ chấm điểm của tất cả giám khảo
- Không có audit trail để giải quyết khiếu nại

## 3. Tác động của các Vấn đề

| Vấn đề | Tác động lên các bên liên quan |
|---|---|
| Thực thi deadline không chính xác | Lo ngại về công bằng, tranh cãi của thí sinh, gánh nặng quản lý |
| Soạn email thủ công | Chất lượng truyền thông không đồng nhất, bỏ lỡ thông báo, lãng phí thời gian nhân viên |
| Chuẩn bị giám khảo thủ công | Chất lượng đánh giá không đồng đều, bao phủ không đầy đủ các điểm trong bài review |
| Không có nền tảng tích hợp | Lỗi dữ liệu, phản hồi chậm, trải nghiệm thí sinh kém |

## 4. Tại sao Cần Giải pháp AI Có Hệ thống

Tự động hóa dựa trên quy tắc (nhắc lịch đơn giản, mẫu email cố định) chỉ giải quyết được một phần deadline và truyền thông, nhưng không thể:

- Sinh email phù hợp ngữ cảnh, cá nhân hóa cho từng đội/sự kiện cụ thể
- Tổng hợp câu hỏi phỏng vấn được điều chỉnh theo bài đánh giá cụ thể của từng đội
- Thích ứng nội dung truyền thông dựa trên trạng thái cuộc thi theo thời gian thực

Tích hợp AI dựa trên LLM là cần thiết để cung cấp khả năng lý luận và sinh nội dung cần thiết cho các tác vụ này.
