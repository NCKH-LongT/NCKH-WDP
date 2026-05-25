# Paper List

## Directly Related / Comic & Manga Analysis

### Paper 01
Dubray, D., & Laubrock, J. (2019).
**Deep CNN-based Speech Balloon Detection and Segmentation for Comic Books.**

- Domain: Comic Speech Balloon Segmentation
- Main Method: U-Net + VGG-16 Encoder
- Contribution:
  - Phát hiện và phân đoạn speech bubble bằng Deep CNN
  - Đạt độ chính xác cao trên comic books phương Tây
- Limitation:
  - Hiệu quả thấp trên manga Nhật Bản do khác biệt layout và phong cách vẽ

---

### Paper 02
Del Gobbo, J., & Herrera, R. M. (2020).
**Unconstrained Text Detection in Manga: a New Dataset and Baseline.**

- Domain: Manga Text Detection
- Main Method: U-Net + ResNet34 Encoder
- Contribution:
  - Đề xuất dataset text detection cho manga
  - Cung cấp baseline segmentation cho manga text
- Limitation:
  - Khó xử lý hard texts và onomatopoeia ngoài speech bubble

---

### Paper 03
Juithealien (2024).
**Manga Speech Bubble Segmentation.**

- Domain: Manga Speech Bubble Segmentation
- Main Method: YOLO11n Instance Segmentation
- Contribution:
  - Segmentation speech bubble theo thời gian thực
  - Độ chính xác rất cao trên Manga109-based Dataset
- Limitation:
  - Chưa tích hợp OCR hoặc translation workflow

---

### Paper 06
Zhang, L., et al. (2021).
**Generating Manga From Illustrations via Mimicking Manga Creation Workflow.**

- Domain: Manga Workflow & Generation
- Main Method: Data-driven Workflow Framework
- Contribution:
  - Mô phỏng quy trình tạo manga thực tế
  - Tự động hóa line art, screentone và texture
- Limitation:
  - Vẫn cần artist chỉnh sửa thủ công

---

### Paper 07
Xie, Z., et al. (2025).
**Advancing Manga Analysis: Comprehensive Segmentation Annotations for the Manga109 Dataset.**

- Domain: Manga Segmentation
- Main Method: SAM Fine-tuned + Human-in-the-loop
- Contribution:
  - Dataset segmentation manga quy mô lớn
  - Áp dụng cơ chế human-in-the-loop
- Limitation:
  - Chi phí annotate và sửa lỗi cao

---

## Domain Application / Workflow & Production

### Paper 05
Mihara, T., et al. (2014).
**A Manga Creator Support Tool Based on a Manga Production Process Model — Improving Productivity by Metadata.**

- Domain: Manga Production Workflow
- Main Method: Metadata-based Management System
- Contribution:
  - Quản lý workflow sản xuất manga bằng metadata
  - Hỗ trợ cộng tác nhóm sản xuất
- Limitation:
  - Chưa tích hợp AI hoặc automation

---

### Paper 10
Hikaru Ikuta, Leslie Wöhler, and Kiyoharu Aizawa (2024).
**MangaUB: A Manga Understanding Benchmark for Large Multimodal Models**

- Domain: Manga Understanding Benchmark
- Main Method: Benchmark for Large Multimodal Models (LMMs)
- Contribution:
  - Benchmark đánh giá khả năng hiểu manga của AI multimodal
  - Bao gồm nhiều tác vụ như character understanding và scene reasoning
- Limitation:
  - Tập trung benchmark hơn là production workflow

---

## AI Model / Method

### Paper 04
Ronneberger, O., Fischer, P., & Brox, T. (2015).
**U-Net: Convolutional Networks for Biomedical Image Segmentation.**

- Domain: Biomedical Image Segmentation
- Main Method: U-Net Architecture
- Contribution:
  - Đề xuất kiến trúc U-Net cho image segmentation
  - Giới thiệu skip connections giúp giữ thông tin không gian
  - Hoạt động tốt với lượng dữ liệu huấn luyện nhỏ
- Limitation:
  - Không được thiết kế riêng cho manga hoặc comic domain

### Paper 08
Xie, M., & Wong, T.-T. (2016).
**Boundary-Aware Texture Region Segmentation for Manga Digitization.**

- Domain: Manga Digitization
- Main Method: Boundary-Aware Texture Segmentation
- Contribution:
  - Tách texture, screentone và vùng trắng hiệu quả
  - Hỗ trợ số hóa manga chất lượng cao
- Limitation:
  - Dựa trên thuật toán truyền thống
  - Cần tinh chỉnh thủ công

---

### Paper 09
Ronneberger, O., et al. (2015).
**U-Net: Convolutional Networks for Biomedical Image Segmentation.**

- Domain: Biomedical Image Segmentation
- Main Method: U-Net
- Contribution:
  - Đề xuất kiến trúc U-Net với skip connections
  - Trở thành backbone phổ biến cho segmentation
- Limitation:
  - Không thiết kế riêng cho manga domain