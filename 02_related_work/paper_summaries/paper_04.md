# Paper 04 summary

## Citation

**Title:** U-Net: Convolutional Networks for Biomedical Image Segmentation

**Authors:**
- Olaf Ronneberger
- Philipp Fischer
- Thomas Brox

**Year:** 2015

**Source:** MICCAI 2015

**DOI/Link:** https://arxiv.org/abs/1505.04597

---

## Problem

Bài báo tập trung giải quyết bài toán **phân đoạn ảnh ở mức pixel**.

### Main Issues
- Cần phát hiện chính xác ranh giới của đối tượng
- Dữ liệu huấn luyện bị hạn chế
- Các phương pháp phân đoạn ảnh truyền thống chưa đủ chính xác

### Objective
- Tạo mặt nạ phân đoạn chính xác
- Hoạt động tốt với tập dữ liệu nhỏ

---

## Method

Bài báo đề xuất kiến trúc **U-Net**.

### Architecture Components
- Encoder (Contracting Path)
- Bottleneck
- Decoder (Expanding Path)
- Skip Connections

### Workflow
1. Ảnh đầu vào
2. Encoder trích xuất đặc trưng
3. Decoder thực hiện upsampling
4. Skip connections giữ lại thông tin không gian
5. Xuất ra segmentation mask

### Key Features
- Kiến trúc hình chữ U
- Skip connections giúp giữ chi tiết ảnh
- Có khả năng phân đoạn ảnh ở mức pixel

---

## Dataset

Bài báo sử dụng:
- Ảnh hiển vi sinh học
- Bộ dữ liệu phân đoạn tế bào

### Dataset Includes
- Ảnh hiển vi
- Segmentation masks

### Data Augmentation Methods
- Rotation
- Cropping
- Elastic deformation

---

## Evaluation

Mô hình được đánh giá bằng:
- Pixel Accuracy
- Segmentation Overlap
- Boundary Accuracy

### Results
- Đạt hiệu năng state-of-the-art trong ISBI Challenge
- Phân đoạn đường biên rất chính xác
- Hoạt động tốt dù dữ liệu huấn luyện hạn chế

---

## Main Contributions
- Đề xuất kiến trúc U-Net
- Giới thiệu skip connections
- Cải thiện đáng kể độ chính xác phân đoạn ảnh
- Trở thành nền tảng cho nhiều mô hình segmentation hiện đại

### Widely Applied In
- Medical Imaging
- Manga Segmentation
- OCR Preprocessing
- Object Segmentation