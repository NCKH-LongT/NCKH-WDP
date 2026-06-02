# Tóm tắt Bài báo 06

## Trích dẫn

Tên bài: Research Supervisor Recommendation System Based on Topic Conformity
Tác giả: TBD
Năm: 2023
Nguồn: Research Conference (Education / Software Engineering Education)
DOI/Link: TBD

## Vấn đề

Trong giáo dục đại học, việc ghép sinh viên với giảng viên hướng dẫn nghiên cứu phù hợp thường được thực hiện thủ công hoặc dựa trên mạng lưới quen biết không chính thức. Điều này dẫn đến phân công không tối ưu, trong đó chuyên môn của giảng viên hướng dẫn không phù hợp với chủ đề nghiên cứu của sinh viên, hoặc giảng viên bị quá tải trong khi người khác lại rảnh.

## Phương pháp

Hệ thống sử dụng:

- Véc tơ hóa TF-IDF mô tả đề tài sinh viên và hồ sơ nghiên cứu giảng viên (danh sách công bố, từ khóa chuyên môn)
- Cosine similarity để ghép đề tài với giảng viên hướng dẫn
- Cân bằng tải dựa trên rule-based (giới hạn tối đa số sinh viên mỗi giảng viên hướng dẫn)
- Danh sách gợi ý có xếp hạng hiển thị cho sinh viên và quản lý bộ môn

## Dữ liệu

Dữ liệu lịch sử từ một trường đại học: bài nộp đề tài sinh viên (N=200+), danh sách công bố và lĩnh vực chuyên môn của giảng viên, lịch sử phân công.

## Đánh giá

- Precision, Recall, F1-score về độ chính xác gợi ý (dùng phân công lịch sử làm ground truth)
- So sánh với phân công thủ công (đánh giá hội đồng chuyên gia)
- Khảo sát mức độ hài lòng sinh viên và giảng viên hướng dẫn

## Kết quả

- Precision: 81% cho gợi ý top-1
- Recall: 74% ở top-3 gợi ý
- Tỷ lệ lỗi phân công thủ công (không khớp chuyên môn) giảm 35%
- Giảng viên hướng dẫn thấy gợi ý "có thể chấp nhận" trong 78% trường hợp

## Hạn chế

- TF-IDF không nắm bắt được similarity ngữ nghĩa (vấn đề đồng nghĩa/diễn đạt lại)
- Không tích hợp dữ liệu tải công việc động
- Không có vòng lặp phản hồi để cải thiện gợi ý theo thời gian
- Chỉ ghép dựa trên văn bản đề tài; không dùng chỉ số trích dẫn hay lịch sử cộng tác

## Liên quan đến đề tài

Bài báo liên quan đến module phân công mentor của chúng tôi. Hệ thống của chúng tôi cần ghép mentor với bảng thi dựa trên chuyên môn và tình trạng sẵn sàng, xác thực qua email domain FPT. Bài báo cung cấp: (1) phương pháp ghép baseline (TF-IDF + cosine) có thể tham khảo hoặc cải tiến; (2) phương pháp đánh giá sử dụng precision/recall cho độ chính xác ghép cặp; (3) bằng chứng rằng người dùng đánh giá cao phân công tự động. Hệ thống của chúng tôi khác ở chỗ phân công cả bảng thi thay vì từng cặp sinh viên-giảng viên.

## Cải tiến Đề xuất

- Thay TF-IDF bằng semantic embeddings (ví dụ: Sentence-BERT) để ghép ngữ nghĩa tốt hơn
- Tích hợp dữ liệu tình trạng sẵn sàng và tải công việc thời gian thực của giảng viên
- Trong bối cảnh cuộc thi: mở rộng sang phân công mentor-bảng thi có xác thực email domain FPT
- Thêm giải thích: hiển thị lý do một mentor được gợi ý cho bảng thi cụ thể
