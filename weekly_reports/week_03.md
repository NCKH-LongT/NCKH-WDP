# Weekly Report - Week 03

## Group Information

- **Class**: SE1823
- **Group**: G03
- **Leader**: Bùi Đức Anh
- **Members**: Lương Khánh Toàn, Lê Văn Kiên, Nguyễn Khánh Hưng, Tăng Thùy Thụy

## Tasks Completed This Week

| Member                    | Task                                                                                                                                                                                                                               | Result                                                                                                                                                                                                                                 |
| :------------------------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bùi Đức Anh**           | Đọc sâu và viết báo cáo tóm tắt bài báo về Domain ứng dụng hệ thống định hướng học thuật (Hệ thống Wahrini 2026). Sửa đổi file đề xuất đề tài.                                                                                     | Hoàn thành file tóm tắt tại `02_related_work/paper_summaries/paper_02.md`.                                                                                                                                                             |
| **Lương Khánh Toàn**      | Đọc sâu và phân tích kỹ thuật trích xuất mã nguồn trong bài báo nền tảng Dev2vec (Moradi Dakhel 2023).                                                                                                                             | Hoàn thành file tóm tắt chi tiết phục vụ tính năng phân loại thiên hướng lập trình.                                                                                                                                                    |
| **Lê Văn Kiên**           | Đọc sâu và phân tích cấu trúc API calls, Issues level của bài báo Dev2vec (Moradi Dakhel 2023).                                                                                                                                    | Hoàn thành file tóm tắt làm cơ sở thiết kế module phân tích thói quen phát triển phần mềm.                                                                                                                                             |
| **Nguyễn Khánh Hưng**     | Đọc sâu và tóm tắt bài báo về kỹ thuật phân tích khoảng trống kỹ năng bằng AI (SkillGap AI - Syed Khizer 2026).                                                                                                                    | Hoàn thành file tóm tắt phục vụ module đối chiếu tín hiệu kỹ năng.                                                                                                                                                                     |
| **Tăng Thùy Thụy**        | Đọc sâu bài báo nghiên cứu ứng dụng Domain hệ thống tư vấn; thực hiện review chéo cấu trúc Markdown các file tóm tắt của thành viên.                                                                                               | Đóng gói toàn bộ cấu trúc thư mục tóm tắt đạt chuẩn hiển thị đồng bộ.                                                                                                                                                                  |
| **Cả nhóm (All members)** | Tổ chức họp nhóm thảo luận định hướng Scope Chatbot AI mới (thu hẹp, tập trung đọc file cấu hình repo); Đồng bộ code từ GitHub và giải quyết xung đột (Merge Conflict) thành công trên file `01_topic_proposal/topic_proposal.md`. | Đồng bộ 100% dữ liệu Git ở máy cục bộ của các thành viên. Thống nhất xong giải pháp loại bỏ cào dữ liệu thị trường, dồn lực thiết kế module Chatbot định hướng dựa trên trích xuất file cấu hình (`package.json`, `requirements.txt`). |

## Git Commits

| Commit ID | Message                                                                   | Author      |
| :-------- | :------------------------------------------------------------------------ | :---------- |
| 2b4f486   | fix: resolve merge conflict in topic_proposal.md and update project scope | Bùi Đức Anh |

## Current Problems

- Việc đọc hiểu sâu các mô hình toán học toán nhúng văn bản (Doc2Vec/Sentence Transformers) trong bài báo nền tảng `dev2vec` có nhiều thuật ngữ học thuật phức tạp, nhóm mất khá nhiều thời gian để thảo luận thống nhất cách ứng dụng vào module Chatbot.
- Gặp sự cố xung đột code (Merge Conflict) khi thực hiện `git pull` do nhiều thành viên cùng chỉnh sửa file đề xuất đề tài, tuy nhiên nhóm đã phối hợp dùng VS Code xử lý an toàn.

## Plan for Next Week

- Bắt đầu Bước 4 theo lộ trình môn học: Ghép nối dữ liệu từ các file tóm tắt riêng lẻ của tuần này để xây dựng bảng Ma trận tổng quan văn liệu tổng hợp tại `02_related_work/literature_review_matrix.md`.
- Chuẩn bị phác thảo chi tiết phần "Research Gap" và "Problem Statement" dựa trên các cải tiến của Chatbot (đọc cấu hình, check coding convention, clean code) so với các hệ thống cũ.

## Questions for Instructor

- Trong bài báo Dev2vec gốc, họ sử dụng mô hình Doc2vec truyền thống trên các trường văn bản của mã nguồn. Nhóm em đối với tính năng Chatbot AI này có thể nâng cấp sử dụng kỹ thuật Embedding của các LLM hiện đại (như Gemini Embedding API) để trích xuất ngữ nghĩa tốt hơn và tạo sinh guideline khuyên học chi tiết hơn không ạ?
