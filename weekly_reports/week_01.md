# Weekly Report - Week 01

## Group Information

Class: SE1823
Group: G06
Leader: Nguyen Tuan Tu
Members: Nguyen Tien Dat, Huynh Kha Tu, Nguyen Minh Huy

---

## Tasks Completed This Week

| Member | Task | Result |
|---|---|---|
| Nguyen Tuan Tu | Draft topic proposal, refine project scope, Search related papers and design initial workflow, use case structure | Completed |
| Nguyen Tien Dat | Search and collect related papers, Design initial workflow, use case structure | Completed |
| Huynh Kha Tu | Research AI models for speech bubble detection, segmentation and design initial workflow, use case structure | Completed |
| Nguyen Minh Huy | Search and collect related papers, Design initial workflow, use case structure | Completed |

---

## Git Commits

| Commit ID | Message | Author |
|---|---|---|
| a99bc67| topic: add manga localization proposal | Nguyen Tuan Tu |

---

## Current Problems

- Chưa có dataset speech bubble annotation hoàn chỉnh.
- Chưa xác định pipeline AI processing tối ưu.
- Chưa chọn framework backend chính thức giữa FastAPI và NestJS.

---

## Plan for Next Week

- Hoàn thành related work analysis.
- Xây dựng problem statement và research gap.
- Thiết kế system architecture.
- Chuẩn hóa use case và workflow.
- Khảo sát dataset và chuẩn bị preprocessing pipeline.

---

## Questions for Instructor

- Có cần tự annotate thêm dataset ngoài Manga109 không?
- Có thể sử dụng pretrained YOLO model cho evaluation không?
- Phần AI evaluation có bắt buộc so sánh nhiều model không?

### Answer
#### Có cần tự annotate thêm dataset ngoài Manga109 không?
Có thể cần annotate thêm một phần nhỏ nếu Manga109 hoặc dataset có sẵn chưa đủ nhãn speech bubble/mask phù hợp với mục tiêu của nhóm. Nhóm có thể dùng Manga109 làm dataset chính, sau đó tạo thêm custom annotations cho một số trang mẫu để phục vụ segmentation và evaluation.

#### Có thể sử dụng pretrained YOLO model cho evaluation không?
Có thể sử dụng pretrained YOLO model làm baseline hoặc làm mô hình khởi tạo. Tuy nhiên, nhóm nên fine-tune hoặc đánh giá lại trên dữ liệu manga/speech bubble để kết quả phù hợp với domain của đề tài.

#### Phần AI evaluation có bắt buộc so sánh nhiều model không?
Không nhất thiết phải so sánh quá nhiều model. Nhóm nên có ít nhất một baseline rõ ràng, ví dụ YOLO pretrained hoặc U-Net baseline, rồi so sánh với pipeline đề xuất. Nếu thời gian cho phép, có thể so sánh thêm YOLO và U-Net theo các metrics như Precision, Recall, mAP, IoU, Dice Score.

