# Topic Proposal

## Vietnamese Title

Hệ thống quản lý SEAL Hackathon và hỗ trợ đánh giá source code bằng AI theo rubric động

## English Title

An IOM-based AI-assisted Source Code Evaluation Workflow for SEAL Hackathon Management Systems

## Application Domain

- Hackathon management
- Software engineering education
- AI-assisted source code evaluation
- Dynamic rubric-based judging

## Practical Problem

SEAL Hackathon có nhiều mùa thi như Fall, Spring, Summer. Mỗi mùa có chủ đề, track, vòng thi và tiêu chí chấm điểm khác nhau. Việc chấm điểm thủ công trong thời gian ngắn gây áp lực cho giám khảo, dễ thiếu nhất quán giữa các giám khảo và khó theo dõi bằng chứng kỹ thuật từ GitHub repository.

Các hệ thống autograder truyền thống chỉ kiểm tra test case nên không đủ cho hackathon, vì rubric còn bao gồm kiến trúc phần mềm, mức độ tích hợp AI, chất lượng sản phẩm, documentation, UX, demo và teamwork.

## Proposed Direction

Nhóm đề xuất workflow IOM để tích hợp LLM hiện có vào hệ thống MERN + React Native. AI nhận source code/diff từ GitHub, đề bài và rubric động từ database, sau đó tạo điểm gợi ý theo từng tiêu chí kèm evidence và feedback. Judge xem kết quả AI, accept hoặc override trước khi hệ thống tính điểm cuối và ranking.

## Why AI is Needed

AI hỗ trợ:

- Đọc nhanh source code/diff.
- Gợi ý điểm theo từng tiêu chí rubric.
- Tạo evidence từ code/repository.
- Tạo feedback ngắn cho judge.
- Phát hiện rủi ro kỹ thuật.
- Giảm thời gian chuẩn bị nhận xét cho judge.

## Important Boundary

Dự án **không xây dựng hoặc fine-tune model AI mới** trong MVP. Nghiên cứu tập trung vào workflow tích hợp AI, prompt, output format, human-in-the-loop và cách đánh giá hiệu quả.

## Expected Outputs

- IOM workflow cho AI-assisted source code evaluation.
- AI Evaluation API prototype.
- Judge scoring sheet có AI suggestion và override.
- Dataset thử nghiệm nhỏ.
- Metrics so sánh AI score/ranking với judge score/ranking.
