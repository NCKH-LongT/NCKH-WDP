# Paper 10 Summary

## Citation

- **Tên bài**: MangaUB: A Manga Understanding Benchmark for Large Multimodal Models
- **Tác giả**: Hikaru Ikuta, Leslie Wöhler, and Kiyoharu Aizawa
- **Năm**: 2024
- **Nguồn**: The University of Tokyo
- **DOI/Link**: arXiv: 2407.19034v1

## Problem

- Các mô hình đa phương thức lớn (LMMs) hiện nay dù mạnh mẽ nhưng thiếu khả năng hiểu sâu về Manga — một phương tiện có ngôn ngữ thị giác riêng biệt, bao gồm bố cục khung, chữ tượng thanh và cách đọc từ phải sang trái.

- Bài báo giải quyết việc thiếu hụt một hệ thống đánh giá (benchmark) chuẩn hóa để phân tích khả năng "hiểu" Manga của các mô hình này.

## Method

- Các tác giả đề xuất **MangaUB**, một benchmark chia thành 4 nhóm tác vụ dựa trên hai trục: độ phức tạp (**Nhận diện** vs. **Hiểu**) và phạm vi (**Đơn khung** vs. **Đa khung**).

- Họ sử dụng phương pháp đánh giá **CircularEval** để chống nhạy cảm với thứ tự lựa chọn và **Ensemble Accuracy** cho các tác vụ khó với nhiều lựa chọn.

## Dataset

- Dữ liệu chính được lấy từ **Manga109**.

- Bổ sung **2.967 chú giải (annotations) mới** từ các chuyên gia.

- Tích hợp dữ liệu từ **COO Dataset** cho từ tượng thanh và **KangaiSet** cho cảm xúc nhân vật.

## Evaluation

- **Metric chính**: **CircularEval** — độ chính xác dựa trên việc hoán vị lựa chọn để đo lường độ nhạy với câu hỏi.

- **Metric phụ**: **Ensemble Accuracy** — lấy kết quả phổ biến nhất từ nhiều lượt thử cho các câu hỏi có hơn bốn lựa chọn.

## Results

- **Nhận diện đơn khung**: LMMs đạt hiệu suất cao trong việc nhận diện các yếu tố cơ bản như vị trí, thời gian, thời tiết và đếm nhân vật.

- **Hiểu sâu & Đa khung**: Các mô hình gặp khó khăn lớn trong việc hiểu cảm xúc, logic xâu chuỗi giữa các khung và hiểu từ tượng thanh trực tiếp từ hình ảnh.

- **Prompt Sensitivity**: GPT-4o và các model khác rất nhạy cảm với thứ tự các lựa chọn trong câu hỏi, dẫn đến sự dao động lớn về kết quả.

## Limitations

- **Khả năng OCR**: Các mô hình mã nguồn mở hiện tại chưa thực hiện tốt việc tự nhận diện và đọc từ tượng thanh tiếng Nhật trong ảnh.

- **Hiểu ngữ cảnh**: Khó khăn trong việc so sánh nội dung giữa các khung hình để suy luận tình tiết (**Visual Cloze**).

- **CircularEval**: Có hạn chế khi áp dụng cho các tác vụ quá khó, nơi các model có thể "đoán" bằng cách chọn một chỉ mục cố định.

## Relevance to our topic

- Bài báo cung cấp bộ tiêu chuẩn (benchmark) quan trọng để đánh giá các mô hình AI trong việc hiểu hình ảnh phức tạp và logic trình tự.

- Nhấn mạnh tầm quan trọng của việc hiểu **logic không gian và trình tự (multi-panel)** — yếu tố cốt lõi trong các dự án phát triển ứng dụng phân tích dữ liệu hình ảnh hoặc đọc hiểu tài liệu trực quan của nhóm.

## Possible improvement

- **Cải tiến OCR**: Tích hợp các module nhận diện văn bản chuyên dụng cho tiếng Nhật để hỗ trợ LMM trong việc đọc hiểu từ tượng thanh/hội thoại trong tranh.

- **Xử lý đa khung**: Phát triển các kỹ thuật tiền xử lý giúp LMM tập trung so sánh sự khác biệt giữa các khung thay vì xử lý toàn bộ trang như một ảnh đơn nhất.

- **Giảm Prompt Sensitivity**: Xây dựng cấu trúc prompt chuẩn hóa hoặc sử dụng các kỹ thuật suy luận như Chain-of-Thought để giảm sự phụ thuộc của AI vào thứ tự đáp án.
