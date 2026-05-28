# Topic Proposal

## Vietnamese Title

AI hỗ trợ đánh giá và xếp hạng source code theo rubric động trong cuộc thi lập trình

## English Title

AI-assisted Source Code Evaluation and Ranking Based on Dynamic Rubrics in Programming Competitions

## Application Context

Bối cảnh ứng dụng là hệ thống **SEAL Hackathon Management**, nhưng phạm vi nghiên cứu khoa học chỉ tập trung vào **module AI hỗ trợ đánh giá source code theo rubric**.

Dự án ứng dụng vẫn bao gồm đầy đủ các module vận hành như event, track, round, team, GitHub repository, submission, judge scoring, ranking và prize. Tuy nhiên, bài báo không nghiên cứu toàn bộ hệ thống quản lý Hackathon, mà chỉ nghiên cứu workflow AI-assisted evaluation bên trong hệ thống đó.

## Practical Problem

Trong các cuộc thi lập trình/Hackathon, giám khảo cần đánh giá nhiều bài nộp trong thời gian ngắn. Việc chấm source code không chỉ dựa vào test case, mà còn phải xem xét:

- mức độ hoàn thiện chức năng;
- chất lượng source code;
- kiến trúc phần mềm;
- mức độ tích hợp AI hoặc công nghệ theo chủ đề cuộc thi;
- README/documentation;
- bằng chứng từ GitHub repository.

Rubric có thể thay đổi theo mùa thi, vòng thi hoặc track. Vì vậy, hệ thống cần hỗ trợ **dynamic rubric** thay vì hard-code tiêu chí.

## Proposed Direction

Nhóm đề xuất một workflow để AI hỗ trợ giám khảo đánh giá source code.

```text
Input:
Problem statement
+ source code/GitHub diff hoặc final source snapshot
+ dynamic rubric
+ README/setup guide
+ optional execution results
+ commit metadata

Method:
Structured AI prompting
+ rubric-based criterion evaluation
+ judge accept/override

Output:
AI suggested score theo từng criterion
+ evidence
+ feedback
+ confidence
+ risks
+ suggested judge questions
+ needsHumanReview
```

AI chỉ đóng vai trò **trợ lý đánh giá**. Điểm cuối cùng vẫn do giám khảo quyết định.

## Why AI is Needed

AI hỗ trợ:

- Đọc nhanh source code hoặc commit diff.
- Gợi ý điểm theo từng tiêu chí rubric.
- Trích xuất evidence từ code/repository.
- Tạo feedback ngắn gọn cho judge.
- Phát hiện rủi ro kỹ thuật cần xem xét.
- Gợi ý câu hỏi phản biện cho judge.
- Giảm thời gian chuẩn bị nhận xét khi chấm nhiều đội.

## Important Boundary

Nghiên cứu không tập trung vào toàn bộ app quản lý Hackathon. App là bối cảnh triển khai. Phần nghiên cứu chỉ tập trung vào module AI-assisted source code evaluation và cách đánh giá hiệu quả của workflow này.

## Expected Research Outputs

- Workflow cho AI-assisted source code evaluation.
- Prompt template theo rubric động.
- Output schema cho AI suggested score, evidence, feedback.
- Mapping giữa AI review và DB/prototype.
- Evaluation plan: score alignment, ranking similarity, override rate, time reduction.
