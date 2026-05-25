# Research Gap

Các nghiên cứu hiện tại như TA Buddy, JorGPT, StepGrade và CodEv cho thấy LLM có thể hỗ trợ chấm bài lập trình, tạo feedback và giảm thời gian chấm. Tuy nhiên, phần lớn các nghiên cứu này tập trung vào **programming assignments trong lớp học**, không phải workflow hackathon thật.

Trong bối cảnh SEAL Hackathon, việc đánh giá có nhiều đặc điểm khác biệt:

1. Mỗi mùa thi có chủ đề khác nhau.
2. Mỗi vòng thi có rubric khác nhau.
3. Mỗi track/bảng có thể có đề bài hoặc chủ đề riêng.
4. Bài nộp nằm trên GitHub repository, không chỉ là một file code đơn lẻ.
5. Hệ thống cần theo dõi commit, diff, README, demo, slide và final submission.
6. Judge cần xem AI suggestion nhưng vẫn giữ quyền chấm cuối.
7. Kết quả không chỉ là điểm mà còn là ranking, finalist selection và awards.

Khoảng trống chính là: hiện chưa có nhiều nghiên cứu mô tả cách áp dụng workflow AI grading theo dạng **Input–Output–Method** vào một hệ thống quản lý hackathon có GitHub tracking, dynamic rubric, judge accept/override và ranking comparison.

Do đó, nghiên cứu này tập trung vào việc thiết kế và đánh giá một workflow IOM để tích hợp LLM hiện có vào hệ thống SEAL Hackathon, thay vì xây dựng hoặc fine-tune một model AI mới.

## Research Gap Statement

Existing AI-assisted grading studies demonstrate the potential of LLMs for programming assignment assessment. However, limited attention has been given to adapting these methods into hackathon workflows that require GitHub-based submissions, dynamic round-specific rubrics, human judge override, and ranking-oriented evaluation. This project addresses this gap by proposing an IOM-based AI-assisted source code evaluation workflow for SEAL Hackathon management systems.
