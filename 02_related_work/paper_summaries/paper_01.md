# Paper 01 Summary

## Citation

Tên bài:
Deep CNN-based Speech Balloon Detection and Segmentation for Comic Books

Tác giả:
David Dubray and Jochen Laubrock

Năm:
2019

Nguồn:
arXiv preprint (cs.CV) / 14th IAPR International Conference on Document Analysis and Recognition

DOI/Link:
https://doi.org/10.48550/arXiv.1902.08137

## Problem

Bài báo giải quyết vấn đề gì?
Bài báo giải quyết việc tự động phát hiện và phân đoạn (detection and segmentation) các bong bóng thoại trong truyện tranh, bao gồm cả phần thân bong bóng và đuôi hướng về nhân vật, đồng thời phân biệt bong bóng thoại với các ô chú thích (captions).

## Method

Bài báo dùng phương pháp/model/hệ thống nào?
Bài báo sử dụng một mạng Fully Convolutional Network (FCN) với kiến trúc U‑Net cho phần giải mã (decoder), kết hợp với encoder là VGG‑16 pre‑trained trên ImageNet. Mô hình được huấn luyện để phân đoạn bong bóng thoại pixel‑level.

## Dataset

Bài báo dùng dữ liệu gì?
- Graphic Narrative Corpus (GNC): khoảng 750 trang truyện tranh tiếng Anh với annotation bong bóng thoại.
- Ngoài ra, cũng đánh giá chéo trên bộ dữ liệu eBDtheque.

## Evaluation

Bài báo đánh giá bằng metric nào?
- Binary cross entropy loss
- Sorensen–Dice coefficient (Dice loss)
- Precision, Recall, F1‑score

## Results

Kết quả chính là gì?
- Mô hình đạt F1‑score vượt 0.94 trên GNC, thuộc state‑of‑the‑art.
- Mô hình xử lý tốt các đuôi bong bóng ngoằn ngoèo, bong bóng có góc cong hoặc “illusory contours” (bong bóng không có đường viền rõ ràng).
- Mô hình học được cách phân biệt bong bóng thoại với các ô chú thích (captions).

## Limitations

Hạn chế của bài báo là gì?
- Đôi khi nhận diện sai vùng có chữ rất lớn (ví dụ từ tượng thanh/onamatopoeia) hoặc bỏ sót bong bóng có hình dạng quá trừu tượng.
- Mô hình hoàn toàn thất bại khi dự đoán trên Manga109 do học đặc trưng văn hóa của truyện tranh phương Tây (chữ Latin, bong bóng bầu dục ngang), không phù hợp với manga Nhật (chữ dọc, bong bóng có kiểu hình khác).

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?
Bài báo có mức độ liên quan rất cao. Đề tài nhóm là Hệ thống quản lý localization manga tích hợp AI, trong đó các tác vụ cốt lõi là nhận diện, phân đoạn và làm trắng bong bóng thoại. Bài báo cung cấp kiến trúc U‑Net làm nền tảng cho việc tạo pixel‑level mask và trích xuất vùng bong bóng thoại (editable bubble region extraction), đúng như mô hình AI nhóm dự định dùng.

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng điểm nào?
- Chuyển domain sang manga: dùng Manga109 để train/finetune mô hình, khắc phục giới hạn không áp dụng được trên manga Nhật.
- Kết hợp object detection: dùng YOLO để sinh bounding box bong bóng trước, sau đó dùng U‑Net để segmentation, nhằm tăng độ chính xác.
- Tích hợp vào workflow cộng tác: đưa mô hình vào hệ thống biên tập cộng tác, kết hợp OpenCV để làm trắng chữ và thiết kế workflow Human‑in‑the‑loop để biên tập viên sửa chữa, duyệt và quản lý revision.