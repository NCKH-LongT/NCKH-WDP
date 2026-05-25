# Weekly Report - Week 02

## Group Information

Class: SE1823
Group: G06
Leader: Nguyen Tuan Tu
Members: Nguyen Tien Dat, Huynh Kha Tu, Nguyen Minh Huy

---

## Tasks Completed This Week

| Member | Task | Result |
|---|---|---|
| Nguyen Tuan Tu | Review topic scope, update related work structure, create literature review matrix, and refine AI-assisted localization workflow direction | Completed |
| Nguyen Tien Dat | Search and summarize papers related to manga text detection, speech bubble segmentation, and Manga109-based datasets | Completed |
| Huynh Kha Tu | Research AI methods for segmentation including U-Net, YOLO instance segmentation, SAM-based annotation, and preprocessing methods | Completed |
| Nguyen Minh Huy | Collect domain application papers, analyze manga production workflow, and support comparison of paper limitations and relevance | Completed |

---

## Git Commits

| Commit ID | Message | Author |
|---|---|---|
| 2d645fb | docs: add week 01 report | Nguyen Tuan Tu |
| adee1ee | review: add 2 directly related papers | Nguyen Tuan Tu |
| fd4773a | review: add 2 directly related papers | Nguyen Tuan Tu |
| c2cab96 | review: add a AI/model paper | Nguyen Tuan Tu |
| 33ca56a | review: add a domain application paper | Nguyen Tuan Tu |
| da30501 | review: add search keywords file | Nguyen Tuan Tu |
| 6fa5cde | review: add a AI/model papers | Nguyen Tuan Tu |
| 614e524 | review: add paper list file | Nguyen Tuan Tu |
| 11d4637 | review: add a Literature review matrix file | Nguyen Tuan Tu |
| ea11da2 | review: add a domain application paper | Nguyen Tuan Tu |
| 468c39a | fix: update paper list file | Nguyen Tuan Tu |

---
## Current Problems

- Một số paper liên quan chỉ tập trung vào detection hoặc segmentation, trong khi đề tài của nhóm còn yêu cầu workflow quản lý localization tích hợp.
- Hướng dataset vẫn cần được làm rõ giữa Manga109, Manga109-based speech bubble annotations và custom annotations của nhóm.
- Thiết kế AI pipeline vẫn chưa được chốt, đặc biệt là thứ tự xử lý và vai trò của YOLO, U-Net, OpenCV và human-in-the-loop correction.
- Các chỉ số đánh giá hiệu quả workflow vẫn cần kế hoạch đo lường rõ ràng, ví dụ như task completion time và user satisfaction.
- Kiến trúc hệ thống và use case cần được liên kết trực tiếp hơn với research gap đã tìm ra từ related work.

---

## Plan for Next Week

- Hoàn thiện problem statement và research gap dựa trên literature review matrix.
- Thiết kế system architecture cho hệ thống AI-assisted manga localization management.
- Xác định AI processing pipeline bao gồm detection, segmentation, bubble whitening, manual correction và editorial approval.
- Tạo use case descriptions chi tiết cho các vai trò assistant, editor, mangaka và admin.
- Chuẩn bị workflow diagrams và data flow diagrams ban đầu.
- Quyết định dataset và annotation strategy cho các thí nghiệm speech bubble detection và segmentation.
- Soạn evaluation plan cho cả AI performance và workflow usability.

---

## Questions for Instructor

- Dự án nên ưu tiên workflow evaluation, AI model performance evaluation hay cân bằng cả hai?
- Có được phép sử dụng pretrained YOLO hoặc public Manga109-based segmentation models làm baseline không?
- Nhóm có cần xây dựng annotation tool hoàn chỉnh hay chỉ cần manual correction interface ở mức prototype?
- Final literature review section cần khoảng bao nhiêu related papers?
- Research gap nên tập trung vào AI-assisted manga localization workflow thay vì chỉ speech bubble segmentation accuracy đúng không?
