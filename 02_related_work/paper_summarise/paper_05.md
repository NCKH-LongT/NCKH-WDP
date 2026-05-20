# Paper 05 Summary

## Citation

Tên bài: Personalized Learning Path Recommendation Based on Learner Profile and Knowledge Graph  
Tác giả: Xin Xie, Xiangyang Feng  
Năm: 2025  
Nguồn: Computing and Informatics, Vol. 44, 2025, pp. 983–1008  
DOI/Link: DOI: 10.31577/cai_2025_4_983

## Problem

Bài báo giải quyết vấn đề quá tải thông tin và tài nguyên học tập rời rạc trong các nền tảng E-learning. Nhiều nền tảng học trực tuyến chỉ cung cấp một lộ trình học cố định cho tất cả người học, trong khi mỗi người học có nền tảng kiến thức, nhu cầu học tập và phong cách học khác nhau.

Điều này khiến người học mất nhiều thời gian để chọn tài nguyên phù hợp, thiếu hướng dẫn cá nhân hóa, khó duy trì động lực và khó xây dựng hệ thống kiến thức mạch lạc.

## Method

Bài báo đề xuất phương pháp gợi ý learning path cá nhân hóa dựa trên Learner Profile và Knowledge Graph.

Phương pháp gồm các bước chính:

1. Xây dựng Learner Profile  
   Hồ sơ người học được mô hình hóa từ nhiều yếu tố:
   - Knowledge background
   - Learning needs
   - Learning styles
   - Learning history
   - Behavior data

2. Xác định Mastered Knowledge và Weak Knowledge  
   Hệ thống phân tích lịch sử làm bài tập của người học để xác định:
   - Kiến thức đã thành thạo
   - Kiến thức còn yếu

3. Xây dựng Knowledge Graph  
   Knowledge Graph biểu diễn các knowledge elements và quan hệ phụ thuộc giữa chúng. Trong bài báo, knowledge graph được xây dựng cho môn Data Structures.

4. Tạo hàm đánh giá learning path  
   Hệ thống tạo path evaluation function dựa trên learner profile. Các yếu tố được xét gồm:
   - Loại knowledge element
   - Độ khó
   - Thời gian học
   - PageRank của node trong knowledge graph
   - Độ dài learning path
   - Learning style
   - Learning need

5. Tìm learning path tối ưu  
   Bài báo sử dụng Ant Colony Optimization để tìm learning path phù hợp nhất trong knowledge graph. Thuật toán tìm kiếm các đường đi có điểm số cao nhất dựa trên profile của từng người học.

## Dataset

Bài báo sử dụng dữ liệu trong bối cảnh môn Data Structures cho sinh viên ngành Computer Science.

Dataset gồm:

- 418 entities trong knowledge graph
- 487 relationships giữa các knowledge elements
- Dữ liệu từ Wikipedia và tài liệu giáo trình
- Dữ liệu bài tập liên kết với knowledge elements
- Dữ liệu hành vi học tập trên hệ thống OJ
- Dữ liệu khảo sát từ sinh viên
- 129 bảng khảo sát hợp lệ
- Dữ liệu hành vi học tập cuối cùng từ 108 người học

Các dữ liệu hành vi gồm:

- Tần suất học algorithm knowledge
- Tần suất học application knowledge
- Tần suất học concept knowledge
- Tổng thời gian online
- Thời gian làm bài tập
- Số lần click navigation
- Số lần xem course outline
- Tần suất học leaf nodes

## Evaluation

Bài báo đánh giá hệ thống theo hai hướng chính:

1. External evaluation  
   Người học đánh giá mức độ hài lòng với learning path được hệ thống gợi ý. Thang đo gồm 5 mức:
   - 1: Very dissatisfied
   - 2: Dissatisfied
   - 3: Neutral
   - 4: Satisfied
   - 5: Very satisfied

2. Algorithm comparison  
   Thuật toán Ant Colony Optimization được so sánh với:
   - Depth-First Search
   - Dijkstra algorithm

Các tiêu chí đánh giá gồm:

- Path score
- Time cost
- Learning style accuracy
- Average satisfaction score

## Results

Kết quả cho thấy phương pháp đề xuất đạt hiệu quả tốt trong việc tạo learning path cá nhân hóa.

Một số kết quả chính:

- Accuracy của learning style theo chiều Perceive Information đạt 91.16%.
- Accuracy của learning style theo chiều Organize Information đạt 86.51%.
- Total Accuracy đạt 77.21%.
- Average satisfaction score đạt 3.65/5.
- Ant Colony Optimization cho path score tương đương DFS nhưng thời gian xử lý tốt hơn.
- Dijkstra có thời gian chạy nhanh nhưng kết quả không ổn định và đôi khi không tìm được path phù hợp.
- ACO có thể tìm learning path tối ưu trong khoảng 10 giây, hiệu quả hơn DFS về mặt thời gian.

Bài báo cũng trình bày giao diện hệ thống, gồm profile page để hiển thị learner profile và learning page để người học chọn weak knowledge points, xem learning path và hỏi hệ thống về kiến thức đang học.

## Limitations

Một số hạn chế của bài báo gồm:

1. Hệ thống mới được thử nghiệm trên một môn học cụ thể là Data Structures.
2. Knowledge graph cần được xây dựng thủ công hoặc bán tự động từ tài liệu học tập.
3. Dữ liệu hành vi học tập còn giới hạn ở một nhóm sinh viên nhất định.
4. Learner profile chưa được cập nhật động ở mức sâu.
5. Hệ thống chưa mở rộng sang nhiều lĩnh vực học tập hoặc nhiều career path khác nhau.
6. Đánh giá chủ yếu dựa trên satisfaction score và so sánh thuật toán, chưa đánh giá dài hạn về kết quả học tập thực tế.
7. Chưa tích hợp dữ liệu thị trường lao động hoặc yêu cầu kỹ năng từ doanh nghiệp.

## Relevance to our topic

Bài báo liên quan trực tiếp đến đề tài của nhóm vì đề tài của nhóm cũng có module Dynamic Learning Roadmap cho sinh viên ngành Software Engineering.

Các điểm liên quan gồm:

- Gợi ý learning path cá nhân hóa
- Xây dựng learner profile
- Phân tích kiến thức/kỹ năng đã có và còn thiếu
- Sử dụng knowledge graph để biểu diễn quan hệ giữa các kỹ năng hoặc knowledge nodes
- Tạo learning path dựa trên nhu cầu và năng lực cá nhân
- Có thể áp dụng vào Skill Tree hoặc Roadmap trong hệ thống của nhóm

Bài báo đặc biệt hữu ích cho phần Dynamic Roadmap của nhóm. Thay vì chỉ tạo roadmap tĩnh, nhóm có thể tham khảo cách bài báo sử dụng learner profile, weak knowledge và knowledge graph để tạo lộ trình học phù hợp với từng sinh viên.

## Possible improvement

Dựa trên bài báo này, nhóm có thể cải tiến hoặc mở rộng theo các hướng sau:

1. Thay knowledge graph môn Data Structures bằng Software Engineering Skill Graph.
2. Mỗi node trong graph có thể là một kỹ năng như Git, REST API, Docker, SQL, React, Spring Boot, CI/CD hoặc Cloud Deployment.
3. Kết hợp learner profile với target career role, ví dụ Backend Developer, DevOps Engineer hoặc Data Engineer.
4. Sử dụng Skill Gap Analysis để xác định mastered skills và weak/missing skills.
5. Tạo Dynamic Learning Roadmap dựa trên skill graph, current skills và career goal.
6. Tích hợp dữ liệu job market từ LinkedIn hoặc TopCV để cập nhật trọng số ưu tiên cho các kỹ năng đang có nhu cầu cao.
7. Bổ sung curated resources cho từng skill node.
8. Cho phép sinh viên đánh dấu completed nodes để cập nhật learner profile theo thời gian thực.
9. Kết hợp AI Virtual Mentor để giải thích vì sao hệ thống đề xuất một learning path cụ thể.
10. Đánh giá roadmap bằng expert rating, user satisfaction, progress completion rate và recommendation relevance.
