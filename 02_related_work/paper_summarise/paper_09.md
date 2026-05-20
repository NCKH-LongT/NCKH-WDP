# Paper 09 Summary

## Citation

Tên bài: Experiences and Insights from Using GitHub Classroom to Support Project-Based Courses  
Tác giả: Maria Augusta Nelson, Lesandro Ponciano  
Năm: 2021  
Nguồn: arXiv  
DOI/Link: https://arxiv.org/abs/2103.07242

## Problem

Bài báo giải quyết vấn đề quản lý và hỗ trợ các môn học project-based trong chương trình Software Engineering.

Trong các môn học theo hướng project-based learning, sinh viên thường làm việc theo nhóm, phát triển phần mềm theo từng giai đoạn, làm việc với giảng viên hướng dẫn và đôi khi có cả khách hàng thật. Tuy nhiên, nếu mỗi nhóm dùng một công cụ lưu trữ source code khác nhau, việc quản lý, theo dõi tiến độ, đánh giá đóng góp và lưu trữ project lâu dài trở nên khó khăn.

Các vấn đề chính gồm:

- Khó quản lý nhiều project sinh viên trong mỗi học kỳ.
- Mỗi nhóm có thể dùng repository tool khác nhau.
- Giảng viên khó theo dõi tiến độ và đóng góp của từng sinh viên.
- Project cần được lưu trữ lâu dài để khách hàng, giảng viên hoặc các nhóm sau tiếp tục phát triển.
- Chưa có hệ thống tập trung để tạo portfolio sinh viên và theo dõi sự phát triển kỹ năng qua nhiều học kỳ.

Vì vậy, bài báo đề xuất sử dụng GitHub Classroom theo cách có cấu trúc, chia sẻ và bền vững trong toàn bộ các môn học project-based của chương trình Software Engineering.

## Method

Bài báo trình bày một approach sử dụng GitHub Classroom trong các môn học project-based tại chương trình Software Engineering Undergraduate Program của PUC Minas, Brazil.

Cách triển khai chính gồm:

1. GitHub Classroom
   - Dùng để tạo classroom cho từng môn học.
   - Giảng viên tạo assignment.
   - Sinh viên hoặc nhóm sinh viên nhận assignment.
   - GitHub Classroom tự động tạo repository cho từng cá nhân hoặc nhóm.

2. GitHub Organization
   - Tất cả classroom của chương trình được liên kết với cùng một GitHub organization.
   - Organization đóng vai trò là nơi lưu trữ tập trung tất cả repository của sinh viên.
   - Repository vẫn tồn tại sau khi semester kết thúc.

3. Repository Template
   - Tạo template chuẩn cho repository.
   - Các nhóm phải tuân theo cấu trúc thư mục và file cơ bản.
   - Mục tiêu là giúp giảng viên dễ tìm tài liệu, source code, documentation và artifact cuối kỳ.

4. Project-Based Course Management
   - Áp dụng cho các môn học mà sinh viên phải phát triển phần mềm theo nhóm.
   - Một số project có real clients.
   - Một số project được nhóm sinh viên khóa sau tiếp tục phát triển.

5. Portfolio and Skill Monitoring
   - Repository được dùng để lưu lại quá trình làm việc của sinh viên.
   - Có thể dùng để tạo portfolio đã được giảng viên xác thực.
   - Có thể trích xuất metrics để theo dõi skill development, contribution và teamwork.

## Dataset

Bài báo báo cáo trải nghiệm triển khai tại chương trình Software Engineering Undergraduate Program của PUC Minas.

Dữ liệu và bối cảnh gồm:

- Khoảng 60 projects mỗi học kỳ.
- 287 sinh viên tham gia các môn project-based.
- 13 supervising professors.
- Pilot được triển khai trong học kỳ đầu năm 2020 ở một môn project-based.
- Học kỳ sau đó mở rộng cho cả 8 project-based courses.
- Survey được gửi cho 287 sinh viên.
- Nhận được 58 phản hồi, tương đương khoảng 20%.

Dữ liệu thu thập gồm:

- Professor perceptions.
- Student perceptions.
- Survey responses.
- Feedback về khó khăn, lợi ích và đề xuất.
- Quan sát việc sử dụng GitHub Classroom trong project-based courses.

## Evaluation

Bài báo không sử dụng metric AI/ML như accuracy hoặc F1-score. Thay vào đó, bài báo đánh giá dựa trên phản hồi của sinh viên và giảng viên sau quá trình triển khai.

Các phương pháp đánh giá gồm:

1. Professor Feedback
   - Họp với 13 supervising professors sau học kỳ.
   - Thu thập nhận xét về việc dùng GitHub Classroom trong quản lý project.

2. Student Survey
   - Gửi khảo sát cho 287 sinh viên.
   - Nhận 58 phản hồi.
   - Đánh giá trải nghiệm, mức độ hài lòng, khó khăn, lợi ích và đề xuất.

3. Descriptive Statistics
   - Tính tỷ lệ sinh viên đánh giá tích cực, tiêu cực hoặc trung lập.
   - Tính điểm trung bình trải nghiệm.
   - Phân tích mức độ commitment và interest của sinh viên.
   - Phân tích tài nguyên GitHub được sử dụng nhiều nhất.

## Results

Kết quả cho thấy việc dùng GitHub Classroom trong project-based courses mang lại phản hồi tích cực.

Một số kết quả chính:

- 44/58 sinh viên, tương đương 75.86%, cho rằng trải nghiệm là tích cực.
- 3/58 sinh viên, tương đương 5.17%, cho rằng trải nghiệm là tiêu cực.
- 11/58 sinh viên, tương đương 18.97%, có ý kiến trung lập.
- 42/58 sinh viên, tương đương 72.41%, cho rằng làm việc nhóm bằng GitHub repository là satisfactory.
- 12/58 sinh viên, tương đương 20.69%, cho rằng GitHub làm tăng độ phức tạp trong teamwork và project dynamics.
- Điểm trung bình trải nghiệm là 4.3/5.
- 76.9% sinh viên tự đánh giá là well committed hoặc fully committed.
- 54.2% sinh viên thể hiện well interested hoặc fully interested trong việc học GitHub.
- 79% sinh viên cho rằng shared repository trong organization là lợi ích chính.
- 39.65% sinh viên cho rằng khó khăn lớn nhất là thiếu kiến thức kỹ thuật về GitHub.
- 79% sinh viên đề xuất tiếp tục sử dụng approach này trong các học kỳ sau.

Từ phản hồi của giảng viên, bài báo cũng chỉ ra rằng họ muốn học thêm về công cụ để sử dụng nhiều tính năng hơn, đặc biệt là hỗ trợ chấm điểm, feedback và trích xuất metrics từ activity log của sinh viên.

## Limitations

Một số hạn chế của bài báo gồm:

1. Đây là báo cáo trải nghiệm triển khai, chưa phải nghiên cứu thực nghiệm quy mô lớn.
2. Survey chỉ nhận được 58/287 phản hồi, khoảng 20%, nên có thể tồn tại response bias.
3. Bài báo chủ yếu dựa trên perception của sinh viên và giảng viên, chưa đánh giá trực tiếp kết quả học tập.
4. Chưa có bộ metrics chuẩn để đo skill development, contribution quality hoặc teamwork.
5. Sinh viên vẫn gặp khó khăn do thiếu kiến thức kỹ thuật về GitHub.
6. GitHub Classroom cần được kết hợp với training và hướng dẫn rõ ràng.
7. Chưa khai thác đầy đủ các công cụ tích hợp như bots, CI/CD, quality assurance hoặc deployment tools.
8. Chưa có đánh giá dài hạn về portfolio sinh viên sau khi tốt nghiệp hoặc khi ứng tuyển việc làm.

## Relevance to our topic

Bài báo rất liên quan đến đề tài của nhóm ở phần Software Engineering Education và E-Portfolio Management.

Trong đề tài của nhóm, hệ thống cần cho phép sinh viên liên kết GitHub account, đồng bộ repository, phân tích README.md, tóm tắt project objective, trích xuất tech stack và tạo shareable e-portfolio URL. Bài báo này cung cấp cơ sở thực tế cho việc sử dụng GitHub như một môi trường học tập và portfolio trong chương trình Software Engineering.

Các điểm liên quan gồm:

- GitHub Classroom hỗ trợ project-based learning trong Software Engineering.
- Repository có thể lưu lại quá trình làm project của sinh viên.
- GitHub organization giúp quản lý project tập trung và lâu dài.
- Repository có thể trở thành portfolio đã được giảng viên xác thực.
- Activity log có thể dùng để trích xuất metrics về skill development và teamwork.
- GitHub giúp sinh viên làm quen với workflow công nghiệp như version control, collaboration, configuration management và continuous integration.
- Portfolio có thể phản ánh kỹ năng đã có và kỹ năng cần phát triển tiếp.

Bài báo hỗ trợ mạnh cho module E-Portfolio Management và định hướng dùng GitHub data để đánh giá kỹ năng sinh viên.

## Possible improvement

Dựa trên bài báo này, nhóm có thể áp dụng hoặc cải tiến theo các hướng sau:

1. Sử dụng GitHub repositories như nguồn dữ liệu chính cho e-portfolio của sinh viên.
2. Tự động đồng bộ public repositories từ GitHub account của sinh viên.
3. Phân tích README.md để trích xuất project objective, tech stack, domain và kết quả project.
4. Tạo AI-generated summary cho từng repository để đưa vào portfolio.
5. Phân loại project theo target career role như Backend Developer, Mobile Developer, DevOps Engineer hoặc Data Engineer.
6. Dùng activity log như commit history, pull requests, issues và branches để đánh giá quá trình học tập và teamwork.
7. Cho phép Academic Counselor hoặc Industry Mentor review portfolio và đưa ra nhận xét.
8. Gợi ý sinh viên cải thiện README, project structure, documentation và deployment.
9. Tạo verified portfolio URL để sinh viên gửi cho nhà tuyển dụng.
10. Kết hợp portfolio với Skill Gap Analysis để chỉ ra kỹ năng đã thể hiện qua project và kỹ năng còn thiếu.
