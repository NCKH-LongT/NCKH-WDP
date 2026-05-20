# Paper 10 Summary

## Citation

Tên bài: Applying GitHub Services to Support Teaching-learning Strategies in Computer Science Courses  
Tác giả: Manel Mena, Javier Criado, Isabel M. del Águila, Joaquín Cañadas, Luis Iribarne  
Năm: 2022  
Nguồn: Proceedings of the 14th International Conference on Computer Supported Education (CSEDU 2022), Volume 1, pp. 289–296  
DOI/Link: https://doi.org/10.5220/0011071000003182

## Problem

Bài báo giải quyết vấn đề sinh viên ngành Computer Science cần được học cả lý thuyết và thực hành bằng các công cụ gần với môi trường công nghiệp thực tế. Trong nhiều môn học, sinh viên học các khái niệm lý thuyết nhưng chưa có nhiều cơ hội áp dụng chúng vào quy trình phát triển phần mềm thực tế như quản lý mã nguồn, làm việc nhóm, quản lý task, kiểm thử tự động, CI/CD và phản hồi liên tục.

Các Learning Management Systems truyền thống như Moodle, Canvas hoặc Blackboard hỗ trợ quản lý môn học, phân phối tài liệu và giao tiếp giữa giảng viên với sinh viên, nhưng chưa thật sự thúc đẩy cộng tác phần mềm và quy trình làm việc giống ngành công nghiệp.

Vì vậy, bài báo đề xuất sử dụng các dịch vụ của GitHub để hỗ trợ teaching-learning strategies trong các môn Computer Science.

## Method

Bài báo trình bày các chiến lược sử dụng GitHub trong 5 môn học thuộc lĩnh vực Computer Science tại University of Almería.

Các nhóm chức năng chính của GitHub được áp dụng gồm:

1. Supporting Shareable Material
   - Sử dụng repositories để chia sẻ tài liệu môn học.
   - Dùng public hoặc private repositories tùy theo nhu cầu.
   - Sử dụng GitHub Pages để xuất bản tài nguyên học tập dạng website tĩnh.

2. Project Management
   - Sử dụng GitHub Projects để tạo Kanban board.
   - Quản lý tasks, issues, milestones, priority và assignment.
   - Theo dõi tiến độ làm bài tập hoặc project của sinh viên.

3. Collaborative Working
   - Hỗ trợ sinh viên làm việc nhóm thông qua repositories.
   - Sử dụng forks, branches, pull requests và merging.
   - Theo dõi đóng góp của từng thành viên.

4. Guidelines and Patterns
   - Cung cấp templates, incomplete solutions hoặc example repositories.
   - Dùng CI/CD và automated testing để kiểm tra bài làm.
   - Cung cấp feedback tự động giúp sinh viên sửa lỗi sớm.

5. Support Teaching Tools
   - Nhóm tác giả phát triển công cụ ITSI-GITSI để tự động tạo và quản lý GitHub repositories.
   - Công cụ hỗ trợ:
     - Tạo repositories hàng loạt.
     - Tạo issues và milestones.
     - Tính điểm dựa trên issues đã hoàn thành.
     - Cập nhật file Markdown để ghi nhận điểm.
     - Xóa nhiều repositories nhanh chóng.

## Dataset

Bài báo không sử dụng dataset theo nghĩa AI/ML. Thay vào đó, dữ liệu nghiên cứu là trải nghiệm triển khai GitHub trong 5 môn học Computer Science tại University of Almería.

Các môn học gồm:

1. Software Engineering
   - Áp dụng project management, autograding, teamwork collaboration và CI/CD.

2. Software Engineering Tools and Methods
   - Áp dụng project management, teamwork collaboration và CI/CD.

3. Rapid Application Development
   - Áp dụng project management, autograding, teamwork collaboration, CI/CD và course material.

4. Software Engineering Processes II
   - Áp dụng project management, teamwork collaboration và course material.

5. Programming
   - Áp dụng project management, teamwork collaboration và course material.

Một kết quả cụ thể được báo cáo trong môn Software Engineering:

- Tổng số sinh viên: 165
- Số sinh viên vượt qua toàn bộ tests: 107, tương đương 65%
- Trong số 107 sinh viên vượt qua tests, 63 sinh viên vượt qua final exam
- Tỷ lệ này tương đương 58% trong nhóm đã pass tests và 38% tổng số sinh viên

## Evaluation

Bài báo đánh giá dựa trên báo cáo triển khai thực tế trong nhiều môn học, không dùng các metric AI/ML như accuracy hoặc F1-score.

Các hình thức đánh giá gồm:

1. Quan sát việc áp dụng GitHub services trong từng môn học
   - Xem GitHub hỗ trợ quản lý project, teamwork, CI/CD, feedback và sharing material như thế nào.

2. Phân tích kết quả học tập trong môn Software Engineering
   - Theo dõi số sinh viên hoàn thành automated tests.
   - So sánh với số sinh viên vượt qua final exam.

3. Phân tích tính phù hợp của từng GitHub feature với từng môn học
   - GitHub Projects cho Kanban/task management.
   - GitHub Issues cho tracking và feedback.
   - Pull Requests cho contribution và review.
   - CI/CD cho automated validation.
   - GitHub repositories cho version control và teamwork.

## Results

Bài báo cho thấy GitHub services có thể hỗ trợ hiệu quả nhiều chiến lược dạy và học trong Computer Science courses.

Các kết quả chính:

- GitHub giúp sinh viên tiếp cận workflow gần với môi trường phát triển phần mềm thực tế.
- GitHub hỗ trợ quản lý tài liệu học tập, project, issues, milestones và teamwork.
- GitHub Projects có thể dùng như Kanban board để quản lý task và theo dõi tiến độ.
- Pull requests, branches, forks và commits giúp sinh viên học cách cộng tác trong phát triển phần mềm.
- CI/CD và automated testing giúp cung cấp feedback sớm cho sinh viên.
- GitHub repositories có thể trở thành nơi lưu trữ bài làm, project và quá trình phát triển của sinh viên.
- Công cụ ITSI-GITSI giúp giảm công việc lặp lại cho giảng viên khi tạo repositories, issues và milestones.
- Trong môn Software Engineering, 65% sinh viên vượt qua toàn bộ automated tests, cho thấy automated validation có thể hỗ trợ cải thiện kỹ năng modeling và thực hành.

Bài báo kết luận rằng các chiến lược sử dụng GitHub giúp thống nhất teaching-learning strategies trong chương trình Computer Science và có tiềm năng mở rộng sang các môn học tương tự.

## Limitations

Một số hạn chế của bài báo gồm:

1. Bài báo là báo cáo triển khai thực tế, chưa phải nghiên cứu thực nghiệm có đối chứng đầy đủ.
2. Kết quả chủ yếu dựa trên quan sát và kinh nghiệm áp dụng trong các môn học.
3. Chưa có khảo sát chi tiết về mức độ hài lòng của sinh viên.
4. Chưa có phân tích dài hạn về tác động của GitHub đến năng lực nghề nghiệp sau khi tốt nghiệp.
5. Việc sử dụng GitHub hiệu quả phụ thuộc vào mức độ quen thuộc của sinh viên và giảng viên với Git/GitHub.
6. Một số chiến lược vẫn đang trong quá trình đánh giá và hoàn thiện.
7. Chưa có methodology chuẩn áp dụng chung cho mọi môn học.
8. Một số tính năng như GitHub Actions, autograding và tooling support cần tiếp tục được cải tiến.

## Relevance to our topic

Bài báo liên quan đến đề tài của nhóm ở phần Application Domain, đặc biệt là Software Engineering Education và E-Portfolio Management.

Trong đề tài của nhóm, hệ thống cần hỗ trợ sinh viên Software Engineering xây dựng portfolio, đồng bộ GitHub repositories, phân tích README.md, trích xuất tech stack và tạo shareable e-portfolio URL. Bài báo này cung cấp cơ sở thực tế rằng GitHub có thể được dùng như một nền tảng hỗ trợ dạy học, làm project, teamwork, version control và theo dõi quá trình phát triển kỹ năng.

Các điểm liên quan gồm:

- GitHub giúp sinh viên làm việc theo quy trình gần với ngành công nghiệp.
- GitHub repositories có thể lưu lại quá trình làm project của sinh viên.
- GitHub Issues, Projects và Pull Requests có thể phản ánh teamwork, contribution và task management.
- GitHub có thể hỗ trợ đánh giá kỹ năng thông qua commits, issues, tests và project history.
- Automated testing và CI/CD có thể cung cấp feedback cho sinh viên.
- GitHub data có thể được dùng làm đầu vào cho e-portfolio hoặc skill assessment.

Bài báo giúp củng cố ý tưởng rằng hệ thống của nhóm không nên chỉ hiển thị repository, mà có thể phân tích sâu hơn quá trình làm việc và kỹ năng thể hiện qua GitHub.

## Possible improvement

Dựa trên bài báo này, nhóm có thể áp dụng hoặc cải tiến theo các hướng sau:

1. Tích hợp GitHub OAuth để sinh viên liên kết tài khoản GitHub với hệ thống.
2. Đồng bộ repositories, commits, README.md, issues và pull requests.
3. Sử dụng README.md để AI tự động tóm tắt project objective và tech stack.
4. Dùng commit history và repository structure để đánh giá mức độ hoàn thiện của project.
5. Phân tích issues và pull requests để nhận diện teamwork, collaboration và project management skills.
6. Gợi ý sinh viên cải thiện project documentation, branch strategy và README quality.
7. Kết hợp GitHub data với Skill Gap Analysis để xác định kỹ năng đã thể hiện qua project và kỹ năng còn thiếu.
8. Dùng GitHub project history để tạo e-portfolio đáng tin cậy hơn thay vì portfolio nhập tay.
9. Cho phép mentor hoặc counselor xem portfolio và đưa ra feedback.
10. Bổ sung module đánh giá project bằng checklist hoặc AI-based rubric dựa trên repository data.
