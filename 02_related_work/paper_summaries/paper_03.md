# Paper 03 Summary

## Citation
- **Tên bài:** OpenAlex: A fully open catalog of the world's scholarly system
- **Tác giả:** Priem, J., Piwowar, H., & Orr, R.
- **Năm:** 2022
- **Nguồn:** Scientometrics
- **DOI/Link:** https://doi.org/10.1007/s11192-022-04438-2

## Problem
Bài báo giải quyết vấn đề độc quyền dữ liệu học thuật của các ông lớn như Web of Science hay Scopus (chi phí bản quyền rất cao, không có API miễn phí cho cộng đồng). Các hệ thống phân tích xu hướng quy mô nhỏ hoặc các dự án sinh viên thường thiếu một nguồn dữ liệu metadata mở, có cấu trúc chuẩn hóa và miễn phí để kết nối.

## Method
Tác giả giới thiệu hệ thống **OpenAlex** - một cơ sở dữ liệu mở thay thế cho Microsoft Academic Graph (MAG). Hệ thống sử dụng các thuật toán so khớp thực thể (Entity Alignment) và phân loại dựa trên luật (Rule-based) để tự động chuẩn hóa metadata từ các nguồn xuất bản công khai, liên kết các thực thể bao gồm: Bài báo (Works), Tác giả (Authors), Nơi xuất bản (Venues/Journals), và Khái niệm (Concepts).

## Dataset
Toàn bộ kho dữ liệu mở toàn cầu của OpenAlex chứa hơn 250 triệu bài báo khoa học, 119 triệu tác giả, và được cập nhật liên tục qua hệ thống API REST công khai.

## Evaluation
- Đánh giá độ phủ dữ liệu (Data Coverage %): So sánh số lượng đầu mục bài báo với Scopus và Web of Science.
- Hiệu năng API: Đo lường thời gian phản hồi (API Response Time) và tỷ lệ lỗi khi chịu tải cao.

## Results
OpenAlex đạt độ chính xác tương đương >95% so với Scopus về mặt phân loại thực thể học thuật, đồng thời cung cấp API miễn phí với tốc độ phản hồi dưới 200ms, trở thành nguồn cung cấp dữ liệu lớn hàng đầu cho các ứng dụng phân tích trắc lượng thư mục (Bibliometrics).

## Limitations
Hệ thống chỉ cung cấp dữ liệu thô (Raw Metadata) qua API và phân loại khái niệm ở mức cơ bản, không tích hợp sẵn các bộ lọc AI dự báo xu hướng tương lai hay các công cụ dashboard trực quan hóa động cho người dùng cuối.

## Relevance to our topic
Bài báo này giải quyết trực tiếp cấu phần hạ tầng dữ liệu của hệ thống theo dõi xu hướng xuất bản tạp chí khoa học. Nó đóng vai trò là tài liệu hướng dẫn thiết kế database schema cho nhóm (User, Research Paper, Journal, Author, Keyword) và cách cấu hình, kết nối với "External academic APIs".

## Possible improvement
Nhóm sẽ ứng dụng OpenAlex làm nguồn dữ liệu chính cho hệ thống. Điểm cải tiến của nhóm là xây dựng thêm lớp giao diện Web (Dashboard) và tích hợp các bộ lọc xu hướng bằng AI mà bản thân API của OpenAlex chưa hỗ trợ, biến dữ liệu thô từ OpenAlex thành các biểu đồ trực quan, dễ hiểu cho Sinh viên và Giảng viên.