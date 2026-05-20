# Paper 02 Summary

## Citation

Tên bài:
Unconstrained Text Detection in Manga: a New Dataset and Baseline

Tác giả:
Julián Del Gobbo and Rosana Matuk Herrera

Năm:
2020

Nguồn:
arXiv preprint

DOI/Link:
https://arxiv.org/abs/2009.04042

## Problem

Bài báo giải quyết vấn đề gì?
Bài báo giải quyết bài toán phát hiện văn bản không bị giới hạn (unconstrained text) trong manga Nhật Bản ở mức pixel, bao gồm cả chữ trong và ngoài bong bóng thoại, chữ bị biến dạng, thay đổi kích thước, hoặc xen lẫn vào nền hình vẽ, vốn khó xử lý bằng bounding‑box truyền thống cho việc xóa chữ và inpainting.

## Method

Bài báo dùng phương pháp/model/hệ thống nào?
Bài báo sử dụng mạng neural sâu với kiến trúc U‑Net, dùng ResNet34 pre‑trained trên ImageNet làm encoder, và thực hiện **segmentation nhị phân** (binary segmentation) để phân loại mỗi pixel là văn bản hay nền, sử dụng **Dice loss** làm hàm mất mát.

## Dataset

Bài báo dùng dữ liệu gì?
- Nhóm tự tạo bộ dữ liệu mới bằng cách gán nhãn pixel‑level cho 450 hình ảnh (tương đương 900 trang manga) từ 45 tập truyện trong bộ dữ liệu Manga109. 
- Dữ liệu được chia thành 3 lớp: non‑text, easy text (chữ trong bong bóng thoại), và hard text (chữ ngoài bong bóng, onomatopoeia).

## Evaluation

Bài báo đánh giá bằng metric nào?
- Các metric pixel‑level: Precision, Recall, Pixel F1 (PF1), PSNR, DRD.
- Các metric theo connected component: Quantity/Quality Recall, Precision, Global F1 (GF1), với 2 chế độ: Normal (bình thường) và Relaxed (nới lỏng ranh giới bằng erode/dilate).

## Results

Kết quả chính là gì?
- Mô hình ResNet34‑U‑Net vượt các phương pháp trước (BCDU‑net, HRNet, SickZil‑Machine), đạt PF1 ≈ 79.36 và GF1 ≈ 84.92 ở chế độ Normal.
- Mô hình phát hiện rất tốt các text dễ (trong bong bóng thoại) với số false positive rất thấp.

## Limitations

Hạn chế của bài báo là gì?
- Mô hình vẫn có thể bỏ sót một số “hard texts” như từ tượng thanh hoặc chữ cách điệu cao nằm ngoài bong bóng thoại.

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?
Bài báo có độ liên quan cực kỳ cao. Bài báo giải quyết đúng hạn chế của Paper 01 (thất bại trên Manga109) và cung cấp **baseline mạnh cho U‑Net khi áp dụng trực tiếp lên manga**, bao gồm **dataset text‑mask riêng trên Manga109**. Nhóm đang dùng Manga109 và U‑Net để sinh pixel‑level mask phục vụ bubble whitening và editable bubble region, nên bài báo này là nền tảng lý tưởng cho pipeline AI‑assisted localization.

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?
- Kết hợp với YOLO: dùng YOLO để khoanh vùng bong bóng thoại trước (bounding box), rồi chỉ chạy U‑Net trên vùng được cắt, nhằm giảm sai sót với hard text.
- Tự động hóa bằng OpenCV: dùng output mask từ U‑Net để làm trắng chữ và xử lý inpainting tự động, không chỉ dừng ở detection/segmentation.
- Tích hợp Human‑in‑the‑loop: thiết kế workflow biên tập cộng tác cho phép editor/assistant sửa trực tiếp mask trên giao diện, khắc phục các lỗi còn sót của U‑Net.