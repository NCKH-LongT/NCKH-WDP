# Paper 07 Summary

## Citation

* **Tên bài:** Advancing Manga Analysis: Comprehensive Segmentation Annotations for the Manga109 Dataset
* **Tác giả:** Zhendong Xie, et al.
* **Năm:** 2025
* **Nguồn:** CVPR 2025
* **DOI/Link:** Đang cập nhật (CVPR 2025 Proceedings)

## Problem

Các bộ dữ liệu manga hiện có (như Manga109 gốc) chủ yếu chỉ cung cấp thông tin dạng khung hình chữ nhật (bounding boxes), thiếu các mặt nạ (masks) phân đoạn chi tiết ở cấp độ pixel. Điều này gây khó khăn cho các mô hình AI trong việc nhận diện chính xác các thành phần phức tạp như:
* Nhân vật (gồm cả khuôn mặt và cơ thể).
* Bong bóng thoại và văn bản bên trong.
* Bố cục khung tranh (panels).

## Method

Bài báo đề xuất quy trình **"Human-in-the-loop" (con người trong vòng lặp)** để xây dựng bộ dữ liệu:



1. **Giai đoạn tiền xử lý:** Sử dụng các mô hình AI có sẵn để dự đoán phân đoạn sơ bộ.
2. **Giai đoạn con người:** Chuyên gia thực hiện sửa lỗi thủ công để đảm bảo độ chính xác tuyệt đối.
3. **Giai đoạn học máy:** Sử dụng dữ liệu đã chỉnh sửa để tinh chỉnh (fine-tune) mô hình **SAM (Segment Anything Model)**.
4. **Lặp lại:** Quá trình này được lặp đi lặp lại để mô hình ngày càng thông minh hơn.

## Dataset

* **Tên:** MangaSeg.
* **Quy mô:** Hơn 700.000 đối tượng được gắn nhãn mặt nạ trên 10.130 trang truyện.
* **Phạm vi:** Bao phủ đầy đủ các thành phần đặc trưng của manga (panel, thoại, văn bản, nhân vật).

## Evaluation

* **Chỉ số đo lường:** Sử dụng các tiêu chuẩn phổ biến trong Computer Vision như **mAP (mean Average Precision)** và **IoU (Intersection over Union)**.
* **Mục tiêu:** Đánh giá mức độ khớp (overlap) giữa dự đoán của AI và mặt nạ chuẩn do con người xác nhận.

## Results

* Thiết lập tiêu chuẩn mới (benchmark) cho phân đoạn đối tượng trong manga.
* Mô hình SAM sau khi fine-tune đạt độ chính xác cao, có khả năng tách lớp nhân vật và nội dung vượt xa các phương pháp truyền thống.

## Limitations

* Chi phí nhân lực để chỉnh sửa thủ công vẫn còn cao.
* Khả năng áp dụng với các phong cách nghệ thuật quá khác biệt hoặc các định dạng khác (như webtoon cuộn dọc) cần được kiểm chứng thêm.

## Relevance to our topic

Đây là bài báo nền tảng cung cấp bộ dữ liệu tiêu chuẩn và phương pháp luận quan trọng. Nó là kim chỉ nam cho việc xử lý dữ liệu manga bằng AI, giúp nhóm xây dựng cơ sở dữ liệu chất lượng cho các tác vụ nâng cao (như dịch truyện hoặc tạo chuyển động).

## Possible improvement

* **Tự động hóa:** Nghiên cứu các phương pháp Self-supervised learning để giảm sự can thiệp của con người.
* **Mở rộng:** Hợp nhất thêm dữ liệu từ các nền tảng truyện tranh kỹ thuật số (webtoon) để tăng tính ứng dụng thực tế.
* **Công cụ hóa:** Phát triển giao diện người dùng hỗ trợ họa sĩ/dịch giả sử dụng AI này để chỉnh sửa truyện nhanh hơn.