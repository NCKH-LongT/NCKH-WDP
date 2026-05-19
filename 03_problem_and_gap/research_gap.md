# Research Gap

Các nghiên cứu hiện tại chứng minh LLM có thể hỗ trợ chấm bài lập trình theo rubric, tạo feedback và giảm thời gian chấm. Tuy nhiên, phần lớn nghiên cứu tập trung vào programming assignments, chưa đi vào hackathon workflow thực tế.

Các khoảng trống chính:

1. Ít nghiên cứu kết hợp GitHub webhook/diff với dynamic rubric và AI grading.
2. Ít nghiên cứu đánh giá **ranking alignment** giữa AI và judge, trong khi hackathon cần leaderboard.
3. Rubric trong nhiều bài là cố định, trong khi hệ thống thật cần rubric động từ database.
4. Ít nghiên cứu có workflow đầy đủ: GitHub repo -> commit diff -> AI suggestion -> judge override -> final ranking.
5. Cần đánh giá cả hiệu quả hệ thống, không chỉ điểm AI.
