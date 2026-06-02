# Tóm tắt Bài báo 02

## Trích dẫn

Tên bài: Aduvia: A Multi-Purpose AI-Powered Learning Management System (LMS)
Tác giả: TBD
Năm: 2025
Nguồn: NILES 2025 Conference (New Trends in Information and Communications Technology Applications)
DOI/Link: TBD

## Vấn đề

Các Hệ thống Quản lý Học tập (LMS) truyền thống chỉ cung cấp các chức năng quản lý khóa học và bài kiểm tra cơ bản, thiếu khả năng tự động hóa thông minh. Giảng viên tốn nhiều thời gian cho các tác vụ lặp đi lặp lại (tạo bài kiểm tra, trả lời câu hỏi thường gặp, chấm bài). Sinh viên thiếu phản hồi cá nhân hóa và hỗ trợ theo thời gian thực.

## Phương pháp

Aduvia tích hợp nhiều module AI vào một LMS:

- Chatbot dựa trên LLM (GPT hoặc tương tự) để tự động trả lời câu hỏi của sinh viên
- Sinh câu hỏi quiz tự động từ tài liệu khóa học (phân tích slide và PDF)
- Engine gợi ý tài liệu học tập cá nhân hóa
- Hỗ trợ chấm điểm bán tự động cho câu trả lời ngắn

## Dữ liệu

Dữ liệu sử dụng LMS từ một cơ sở giáo dục trong một học kỳ. Nội dung khóa học (slide, đề cương) được dùng làm đầu vào cho các module sinh AI. Giảng viên chuyên gia làm người đánh giá chất lượng nội dung AI tạo ra.

## Đánh giá

- Mức độ hài lòng của sinh viên và giảng viên (thang Likert 5 điểm)
- Tỷ lệ hoàn thành tác vụ và thời gian tiết kiệm cho giảng viên
- Độ chính xác của quiz AI trong việc căn chỉnh với mục tiêu học tập
- Chất lượng phản hồi chatbot do sinh viên đánh giá

## Kết quả

- Giảng viên báo cáo giảm 35% thời gian tạo bài kiểm tra
- Quiz do AI tạo đạt 78% độ chính xác trong căn chỉnh với mục tiêu học tập
- Mức độ hài lòng với chatbot: 4,1/5
- Điểm SUS tổng thể: 71 (trên mức trung bình)

## Hạn chế

- Tập trung vào quản lý học tập, không phải cuộc thi hay quản lý sự kiện
- Không có module cụ thể cho chấm điểm bảng thi, luồng phỏng vấn hay quy trình cuộc thi
- Rủi ro AI hallucination trong nội dung được tạo ra đã được ghi nhận
- Không có luồng làm việc đa vai trò (ví dụ: thông báo phân công mentor, quản lý bảng thi)

## Liên quan đến đề tài

Aduvia là mô hình kiến trúc gần nhất với hệ thống ACMS-AI đề xuất của chúng tôi. Bài báo chứng minh tính khả thi và giá trị của việc tích hợp nhiều tính năng AI vào một nền tảng quản lý đặc thù theo lĩnh vực. Khung đánh giá (điểm chuyên gia, tiết kiệm thời gian, điểm SUS) áp dụng trực tiếp cho thiết kế đánh giá của chúng tôi. Hạn chế được ghi nhận là không có luồng cuộc thi chính xác là khoảng trống mà công trình của chúng tôi lấp đầy.

## Cải tiến Đề xuất

- Mở rộng nền tảng quản lý AI sang bối cảnh cuộc thi / hackathon
- Thêm sinh email thông báo bằng LLM cho các mốc cuộc thi
- Thêm module sinh câu hỏi phỏng vấn từ bài đánh giá cho đánh giá cạnh tranh
- Tích hợp luồng chấm điểm đa bảng và chọn đội vào chung kết
