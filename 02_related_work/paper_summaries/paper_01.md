# Tóm tắt Bài báo 01

## Trích dẫn

Tên bài: Smart Event Management System Using Machine Learning
Tác giả: TBD
Năm: 2023
Nguồn: International Conference on Information Technology and Management
DOI/Link: TBD

## Vấn đề

Quản lý sự kiện theo cách thủ công kém hiệu quả, dễ mắc lỗi và thiếu khả năng ra quyết định thông minh theo thời gian thực cho việc lập lịch, phân bổ nguồn lực và phân tích hành vi người tham gia. Các hệ thống quản lý sự kiện truyền thống hoàn toàn phụ thuộc vào cấu hình thủ công và không cung cấp hỗ trợ ra quyết định tự động.

## Phương pháp

Bài báo đề xuất hệ thống quản lý sự kiện dựa trên ML với các thành phần:
- Mô hình phân loại (Random Forest, Gradient Boosting) để dự đoán loại sự kiện và phân bổ nguồn lực
- Phân tích hành vi người tham gia dựa trên dữ liệu lịch sử tham gia
- Kết hợp lập lịch rule-based với gợi ý ML để tối ưu timeline sự kiện

## Dữ liệu

Log sự kiện từ các sự kiện học thuật và doanh nghiệp. Phiếu phản hồi người tham gia và dữ liệu đăng ký. Áp dụng phân chia train/test trên dữ liệu lịch sử sự kiện.

## Đánh giá

- Độ chính xác của gợi ý tối ưu lịch
- Khảo sát mức độ hài lòng người dùng (thang Likert 5 điểm)
- Giảm thời gian so với quy trình lập lịch thủ công

## Kết quả

Hệ thống đạt độ chính xác trên 85% trong các gợi ý lịch. Thời gian lập kế hoạch giảm khoảng 40% so với thủ công. Mức độ hài lòng của ban tổ chức: 4,2/5.

## Hạn chế

- Không tích hợp LLM cho tự động hóa truyền thông
- Chỉ tập trung vào tối ưu hóa lịch, không sinh email thông báo hay hỗ trợ chuẩn bị giám khảo
- Dataset nhỏ từ môi trường có kiểm soát; khả năng tổng quát hóa sang bối cảnh cuộc thi học thuật còn hạn chế
- Không đề cập đến luồng chuẩn bị phỏng vấn, cross-judging hay quản lý đa bảng thi

## Liên quan đến đề tài

Bài báo chứng minh AI có thể mang lại hiệu quả đo lường được trong quản lý sự kiện. Bài xác nhận không gian vấn đề của chúng tôi (quản lý thủ công kém hiệu quả) và cung cấp kiến trúc miền tương đồng. Phương pháp đánh giá (thời gian tiết kiệm, mức độ hài lòng) áp dụng trực tiếp cho đánh giá hệ thống của chúng tôi. Công trình của chúng tôi mở rộng bằng cách thêm sinh email bằng LLM, tự động hóa truyền thông và hỗ trợ chuẩn bị giám khảo.

## Cải tiến Đề xuất

- Tích hợp LLM để sinh truyền thông phù hợp ngữ cảnh, tự động ở từng mốc sự kiện
- Thêm luồng chấm điểm và đánh giá 2 vòng đặc thù cho cuộc thi học thuật
- Mở rộng sang cấu trúc cuộc thi học thuật đa bảng với cross-judging và chọn đội vào chung kết
