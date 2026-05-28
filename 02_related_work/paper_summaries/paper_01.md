---
title: "Advanced optimization-based weighted features for ensemble deep learning smart occupancy detection network for road traffic parking"
authors: "B. Padmavathi, Vanaja Selvaraj"
year: 2024
source: "Journal of Network and Computer Applications, Vol. 230"
doi: https://doi.org/10.1016/j.jnca.2024.103924

## Abstract / Summary
Đề xuất một mạng học sâu kết hợp (Ensemble Deep Networks - EDN) với tiền xử lý Multi-scale Retinex và tối ưu hóa Advanced Pelican Optimization Algorithm (APOA) để phát hiện chỗ đỗ trống theo thời gian thực.

## Problem
Phát hiện không gian đỗ xe trống trong khu vực đô thị đông đúc bằng giải pháp camera-based, nhằm giảm tắc nghẽn và thời gian tìm chỗ so với cảm biến từng ô (costly/per-slot sensors).

## Methods
- Pre-processing: Multi-scale Retinex image enhancement.
- Feature extraction: Residual Attention Network.
- Feature/parameter selection: Advanced Pelican Optimization Algorithm (APOA).
- Classifier: Ensemble Deep Networks (kết hợp DCRF và Extreme Deep Learning), kết hợp bằng trung bình dự đoán.

## Dataset
CNRPark + EXT (public parking image datasets).

## Evaluation metrics
- Accuracy, Precision, Matthews Correlation Coefficient (MCC).

## Key results
- Reported: Accuracy = 96.6%, Precision = 92.9%, MCC = 92.3% on the reported datasets.

## Limitations
- Mô hình phức tạp, có thể tiêu tốn nhiều tài nguyên tính toán; khả năng bị giảm hiệu năng trong điều kiện occlusion/ánh sáng xấu chưa được thử nghiệm đầy đủ.

## Relevance to our project
- Cung cấp phương pháp và cấu trúc mô hình mạnh cho phát hiện occupancy bằng camera; hữu ích để tham khảo cải tiến cho môi trường multi-level và tối ưu hoá cho edge/real-time.

## Suggested improvements / notes
- Kiểm thử trên dữ liệu thực tế địa phương và điều kiện ánh sáng xấu.
- Nghiên cứu phiên bản mô hình nhẹ cho triển khai Edge AI (pruning/quantization).
---