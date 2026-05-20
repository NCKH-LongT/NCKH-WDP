# Paper 09 Summary

## Citation

Tên bài:
U‑Net: Convolutional Networks for Biomedical Image Segmentation

Tác giả:
Olaf Ronneberger, Philipp Fischer, Thomas Brox

Năm:
2015

Nguồn:
MICCAI / Springer LNCS

Link arXiv:
https://arxiv.org/abs/1505.04597

## Problem

Bài báo giải quyết vấn đề gì?
Bài báo giải quyết bài toán **segmentation hình ảnh sinh học y tế** (biomedical image segmentation) khi dữ liệu huấn luyện rất ít, trong khi vẫn cần **độ chính xác pixel‑level cao** và **runtime nhanh**.

## Method

Bài báo dùng phương pháp/model/hệ thống nào?
Bài báo đề xuất kiến trúc **U‑Net**, là một **mạng fully convolutional** gồm:
- Contracting path (encoder) để bắt context,
- Expanding path (decoder) đối xứng để tái tạo vị trí pixel‑level,
và các **skip connections** giữa encoder và decoder để giữ lại thông tin không gian.
Mô hình được huấn luyện end‑to‑end với **data augmentation mạnh** nhằm khai thác hiệu quả số lượng ảnh được gán nhãn rất hạn chế.

## Dataset

Bài báo dùng dữ liệu gì?
Bài báo dùng dữ liệu **ảnh sinh học y tế**:
- Ảnh cấu trúc thần kinh trong ảnh hiển vi điện tử (neuronal structures in electron microscopic stacks).
- Ảnh hiển vi truyền sáng (cell tracking challenge, phase contrast và DIC).
Số lượng ảnh huấn luyện khá ít, nhưng U‑Net vẫn đạt kết quả vượt trội.

## Evaluation

Bài báo đánh giá bằng metric nào?
- Các metric segmentation chuẩn:
  - pixel‑wise accuracy,
  - IoU (Jaccard) hoặc Dice‑like scores.
- Thời gian inference: segmentation một ảnh 512×512 mất **dưới 1 giây** trên GPU hiện đại.

## Results

Kết quả chính là gì?
- U‑Net **thắng thách thức ISBI** cho segmentation cấu trúc thần kinh và **giành giải Cell Tracking Challenge 2015** trên các loại ảnh hiển vi truyền sáng.
- Mô hình có thể chạy end‑to‑end từ **rất ít ảnh training** và vẫn **vượt phương pháp sliding‑window CNN truyền thống**.

## Limitations

Hạn chế của bài báo là gì?
- Được thiết kế cho **domain y sinh**, nên ban đầu không được tối ưu cho các data domain khác (như manga, comic).
- Khi áp dụng sang domain mới (ví dụ manga), nhóm cần **finetune, thay đổi encoder (ResNet, v.v.), và điều chỉnh loss** (Dice, weighted cross‑entropy, v.v.) để phù hợp.

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?
- Bài báo cung cấp **kiến trúc U‑Net** rất phù hợp để tạo **mask pixel‑level cho bong bóng thoại** trong manga, đúng như pipeline bạn định dùng:
  - nhận diện vùng bong bóng → segmentation → làm trắng chữ → chỉnh sửa cộng tác.
- Đề tài nhóm “AI‑Assisted Manga Localization with Collaborative Workflow” có thể **dùng U‑Net làm backbone segmentation** cho speech balloons / text regions, rồi tích hợp với YOLO + OpenCV + workflow editor.

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?
- Finetune **U‑Net trên Manga109** hoặc dataset text‑segment riêng (như trong bài “Unconstrained Text Detection in Manga”) để xử lý text manga hiệu quả hơn. 
- Kết hợp **encoder khác (ResNet, EfficientNet, v.v.)** thay vì VGG nguyên gốc, để tăng độ chính xác và hiệu năng.
- Mở rộng thành **“manga‑specific U‑Net”** với:
  - loss function tùy chỉnh,
  - data augmentation hướng manga (bút nét, bong bóng, text dọc),
  - pipeline tích hợp với canvas cộng tác và hệ thống localization của nhóm.