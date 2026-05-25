# Paper 03 Summary

## Citation

**Title:** Manga Speech Bubble Segmentation

**Author:**
- Juithealien

**Year:** 2024

**Source:** Hugging Face

**DOI/Link:** https://huggingface.co/juithealien/manga109-segmentation-bubble

---

## Problem

Bài báo tập trung giải quyết bài toán **phát hiện và phân đoạn bong bóng hội thoại tự động trong ảnh manga**.

### Main Challenges
- Bong bóng hội thoại có nhiều hình dạng và kích thước khác nhau
- Trang manga có bố cục phức tạp
- Văn bản và nền có thể chồng lấp lên nhau
- Cần phân đoạn chính xác để phục vụ OCR và dịch manga

---

## Method

Bài báo sử dụng:
- YOLO11n Instance Segmentation

### System Workflow
1. Ảnh manga đầu vào
2. Trích xuất đặc trưng bằng CNN backbone
3. YOLO detection head phát hiện speech bubbles
4. Nhánh segmentation tạo segmentation masks
5. Xuất bounding boxes và segmentation masks

### Main Architecture
- YOLO Backbone
- Detection Head
- Instance Segmentation Mask Branch

---

## Dataset

Bài báo sử dụng:
- Manga109-based Dataset

### Dataset Includes
- Trang manga
- Chú thích speech bubble
- Pixel-level segmentation masks

### Characteristics
- Ảnh manga trắng đen
- Nhiều phong cách vẽ manga khác nhau
- Speech bubbles đã được gán nhãn

---

## Evaluation

Mô hình được đánh giá bằng các chỉ số sau:

| Metric      | Box    | Mask   |
|--------------|--------|--------|
| Precision    | 97.55% | 97.66% |
| Recall       | 97.03% | 97.15% |
| mAP@50       | 99.10% | 99.13% |
| mAP@50-95    | 96.67% | 94.69% |

---

## Results Show
- Độ chính xác rất cao
- Segmentation masks ổn định
- Hoạt động tốt trên nhiều phong cách manga khác nhau

---

## Main Contributions
- Phát triển hệ thống phân đoạn speech bubble cho manga
- Ứng dụng YOLO cho instance segmentation
- Đạt độ chính xác phát hiện cao
- Hỗ trợ OCR và quy trình dịch manga
- Tối ưu cho suy luận thời gian thực (real-time inference)