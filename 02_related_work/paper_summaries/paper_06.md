# Paper 06 Summary

## Citation

Title:
Generating Manga From Illustrations via Mimicking Manga Creation Workflow

Authors:
Lvmin Zhang, Xinrui Wang, Qingnan Fan, Yi Ji, Chunping Liu

Year:
2021

Source:
IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR 2021)

DOI/Link:
https://doi.org/10.1109/CVPR46437.2021.00559
https://openaccess.thecvf.com/content/CVPR2021/html/Zhang_Generating_Manga_From_Illustrations_via_Mimicking_Manga_Creation_Workflow_CVPR_2021_paper.html

## Problem

Bài báo giải quyết vấn đề gì?
Bài báo giải quyết việc **tự động chuyển một minh họa số thành đầu ra theo phong cách manga** bằng cách mô phỏng quy trình sáng tác manga chuyên nghiệp.
Mục tiêu là autom hóa các bước chính như: **rút trích đường line**, **tạo screentone**, và **tạo texture**, để kết quả có thể dùng được trong workflow thực tế của manga artists.

## Method

Bài báo dùng phương pháp/model/hệ thống nào?
Bài báo đề xuất **một framework học dữ liệu (data‑driven)**, trong đó sinh manga được chia thành ba thành phần chính:
- Manga line drawing,
- Regular screentone,
- Irregular screen texture. 
Phương pháp được thiết kế dựa trên **workflow thực tế trong studio**, và được huấn luyện trên dữ liệu được annotate bởi artist, giúp các layer được sinh ra có thể **combine lại và chỉnh sửa tay** trong quy trình sản xuất thật.

## Dataset

Bài báo dùng dữ liệu gì?
Bài báo giới thiệu **một bộ dữ liệu quy mô lớn** được annotate bởi artist theo kiểu **human‑in‑the‑loop**.
Dataset bao gồm ba thành phần chính nêu trên, cho phép mô hình học cách sinh từng bước theo đúng thực tế sản xuất manga.

## Evaluation

Bài báo đánh giá bằng metric nào?
- Đánh giá bao gồm **perceptual user study** và **so sánh hình ảnh định tính**.
- Thay vì chỉ đo độ tương tự hình ảnh, bài báo nhấn mạnh liệu các layer được sinh ra có **dùng được trong workflow hàng ngày của manga artist** (dễ chỉnh sửa, kết hợp với các bước khác) hay không.

## Results

Kết quả chính là gì?
- Framework có thể sinh ra các layer (line, screentone, texture) có **giá trị thực tế cho artist**.
- Các layer này được báo cáo là **có thể dùng trong công việc hàng ngày** và đóng vai trò như **tài sản trung gian** trong quy trình sáng tác manga.

## Limitations

Hạn chế của bài báo là gì?
- Hiệu năng phụ thuộc nhiều vào **chất lượng và đa dạng** của bộ dữ liệu được annotate bởi artist.
- Phương pháp vẫn yêu cầu **một mức độ chỉnh sửa bằng tay**, và **khả năng tổng quát qua nhiều phong cách manga khác nhau** chưa được chứng minh đầy đủ.

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?
Bài báo **rất liên quan** vì nó **mô hình hóa rõ ràng quy trình sản xuất manga như một workflow** có thể chia thành các giai đoạn được hỗ trợ bởi hệ thống.
- Cung cấp **góc nhìn mạnh về workflow analysis** và **so sánh domain** (từ sáng tạo → editing → localization).
- Cho thấy cách **liên kết các bước sản xuất với module tính toán riêng**, rất phù hợp cho nhóm bạn phân tích **manga localization workflow** và thiết kế **kiến trúc hệ thống**.

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?
- Nhúng framework này vào **một hệ thống workflow lớn hơn** có **metadata management, versioning, và hỗ trợ chỉnh sửa cộng tác**.
- Mở rộng hướng **localization & publishing**:
  - Thêm **xử lý vùng text**,
  - **annotation support**,
  - **tích hợp với pipeline xuất bản** (publishing workflow) sau khi text được dịch và thay thế.