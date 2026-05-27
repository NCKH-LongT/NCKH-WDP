# Paper 11 Summary

## Citation

Tên bài: Dev2vec: Representing Domain Expertise of Developers in an Embedding Space  
Tác giả: Arghavan Moradi Dakhel, Michel C. Desmarais, Foutse Khomh  
Năm: 2023  
Nguồn: Information and Software Technology, Volume 159, Article 107218, Elsevier  
DOI/Link: https://doi.org/10.1016/j.infsof.2023.107218

## Problem

Bài báo giải quyết vấn đề tự động đánh giá chuyên môn kỹ thuật của developer dựa trên hoạt động của họ trên GitHub.

Trong các dự án phần mềm lớn, việc chọn đúng developer có chuyên môn phù hợp là rất quan trọng. Developer có thể cần được chọn để tham gia project, sửa bug, review code, hoặc ứng tuyển vào một job role. Tuy nhiên, việc đánh giá chuyên môn kỹ thuật của developer theo cách thủ công rất khó, đặc biệt khi có nhiều ứng viên hoặc nhiều developer cùng tham gia nhiều dự án khác nhau.

GitHub chứa rất nhiều dữ liệu hoạt động của developer như repository, issue, commit và API usage. Tuy nhiên, GitHub không được thiết kế để tìm kiếm hoặc phân loại chuyên gia theo domain expertise. Các phương pháp cũ thường dựa trên số commit, số dòng code, API frequency hoặc bag-of-words, nhưng những cách này dễ gặp vấn đề về dữ liệu thưa, số chiều lớn và thiếu khả năng hiểu ngữ nghĩa.

Vì vậy, bài báo đặt ra vấn đề: làm thế nào để biểu diễn domain expertise của developer bằng embedding vector, dựa trên hoạt động GitHub của họ trên nhiều software projects.

## Method

Bài báo đề xuất phương pháp **dev2vec**, sử dụng **doc2vec** để biểu diễn chuyên môn kỹ thuật của developer thành embedding vector.

Thay vì chỉ dùng một nguồn dữ liệu, bài báo khai thác ba nguồn thông tin từ GitHub:

1. **Repository information**

   Hệ thống lấy thông tin văn bản từ các repository mà developer từng đóng góp.

   Các thông tin gồm:
   - Repository name
   - Tags
   - Topics
   - README file

   Các thông tin này được gộp lại thành một document cho mỗi developer. Mục tiêu là biểu diễn lĩnh vực và công nghệ mà developer từng tham gia.

   Phiên bản này được gọi là:
   - dev2vec:Repos

2. **Issue resolving history**

   Hệ thống phân tích lịch sử developer tham gia xử lý issue.

   Một developer được xem là có liên quan đến issue nếu họ:
   - Được assign vào issue
   - Tạo issue
   - Tham gia discussion trong issue

   Nội dung title và body của các issue được gộp lại thành một document cho mỗi developer.

   Phiên bản này được gọi là:
   - dev2vec:Issues

3. **API calls in commits**

   Hệ thống phân tích danh sách API/library trong các source files mà developer đã thay đổi qua commit.

   Bài báo xử lý API calls từ nhiều ngôn ngữ lập trình như:
   - Java
   - JavaScript
   - Python
   - TypeScript
   - Go
   - Ruby
   - Kotlin
   - Dart
   - R
   - Rust
   - Scala
   - Và một số ngôn ngữ khác

   Phiên bản này được gọi là:
   - dev2vec:APIs

Ngoài ba mô hình riêng lẻ, bài báo còn kết hợp ba vector từ ba nguồn trên bằng cách concatenate, tạo thành mô hình:

- dev2vec:RIAs

Trong đó RIA là viết tắt của:

- Repository
- Issue
- API

Sau khi có embedding vector cho mỗi developer, bài báo dùng các vector này để phân loại developer vào các technical job roles.

Các classifier được sử dụng gồm:

- Support Vector Machine
- Random Forest
- Logistic Regression

## Dataset

Bài báo sử dụng dataset GitHub developers có nhãn job role từ nghiên cứu trước.

Thông tin dataset:

- Dataset ban đầu có 1662 developers.
- Các developer được phân loại vào 5 job roles:
  - Backend
  - Frontend
  - Mobile
  - DevOps
  - Data Scientist
- 20% developer có nhiều hơn một label.
- Bài báo chỉ giữ các developer có một domain expertise duy nhất.
- Sau khi lọc, còn 1340 developers.
- Trong đó, nhóm tác giả tìm được GitHub profile của 1272 developers.

Dữ liệu GitHub được thu thập gồm:

1. **Repository textual information**
   - Thu thập thông tin từ 58,000 repositories.
   - Mỗi developer có một document tổng hợp từ repository name, tags, topics và README.

2. **Issue resolving history**
   - Thu thập title và body của khoảng 60,000 issues.
   - Mỗi developer có một document tổng hợp từ các issue mà họ đã tạo, được assign hoặc tham gia discussion.

3. **API calls in commits**
   - Trích xuất source files từ khoảng 21 triệu commits.
   - API/library được lấy từ các source files sau khi commit được submit.
   - API được lọc để giảm nhiễu, ví dụ chỉ giữ API xuất hiện ít nhất 5 lần trong contribution.

## Evaluation

Bài báo đánh giá dev2vec thông qua bài toán phân loại technical job role của developer.

Mục tiêu đánh giá là kiểm tra xem embedding vector có thể biểu diễn domain expertise của developer tốt hay không.

Các mô hình được so sánh gồm:

- Baseline majority classifier
- State-of-the-art bag-of-words method, gọi là SOA:bow
- dev2vec:Repos
- dev2vec:Issues
- dev2vec:APIs
- dev2vec:RIAs

Các classifier được dùng:

- SVM
- Random Forest
- Logistic Regression

Do dữ liệu bị mất cân bằng giữa các role, bài báo dùng các metric:

- Macro-Weighted Precision
- Macro-Weighted Recall
- Macro-Weighted F1-score

Bài báo chia dữ liệu theo tỷ lệ:

- 80% train set
- 10% validation set
- 10% test set

## Results

Kết quả cho thấy dev2vec hiệu quả hơn baseline và phương pháp state-of-the-art dựa trên bag-of-words.

Một số kết quả chính:

1. **dev2vec cải thiện F1-score rõ rệt**

   Với Random Forest:
   - Baseline F1-score = 26.15%
   - SOA:bow F1-score = 42.35%
   - dev2vec:Repos F1-score = 60.02%
   - dev2vec:Issues F1-score = 63.08%
   - dev2vec:APIs F1-score = 55.51%

   Như vậy, dev2vec cải thiện F1-score từ 13.16% đến 20.73% so với state-of-the-art.

2. **Issue resolving history là nguồn dữ liệu tốt nhất**

   Trong ba nguồn Repository, Issue và API, mô hình dev2vec:Issues đạt kết quả tốt nhất.

   Điều này cho thấy lịch sử xử lý issue là nguồn dữ liệu rất giàu thông tin để biểu diễn chuyên môn kỹ thuật của developer.

3. **Repository information đứng thứ hai**

   dev2vec:Repos cũng đạt kết quả tốt, cho thấy README, repository name, tags và topics có thể phản ánh lĩnh vực kỹ thuật mà developer từng làm.

4. **API calls cũng có giá trị nhưng thấp hơn Issues và Repos**

   dev2vec:APIs vẫn tốt hơn bag-of-words, nhưng kết quả thấp hơn dev2vec:Issues và dev2vec:Repos.

5. **dev2vec:RIAs không luôn vượt dev2vec:Issues**

   Việc nối vector từ Repos, Issues và APIs giúp cải thiện ở một số role như Frontend và Data Scientist, nhưng nhìn chung kết quả không tốt hơn rõ rệt so với dev2vec:Issues.

6. **Một số role dễ phân loại hơn role khác**

   Data Scientist và Frontend thường được phân loại tốt hơn Backend và Mobile.

   Lý do là kỹ năng của Backend, Frontend và Mobile có thể giao nhau nhiều, khiến classifier khó phân biệt rõ.

## Limitations

Một số hạn chế của bài báo gồm:

1. Dataset chỉ gồm 5 technical job roles: Backend, Frontend, Mobile, DevOps và Data Scientist.
2. Phương pháp tập trung vào developer có dữ liệu GitHub đủ nhiều, nên có thể không phù hợp với người mới học hoặc sinh viên ít project.
3. Ground truth được lấy từ StackOverflow profile và liên kết với GitHub, nên có thể có sai lệch nếu profile không đầy đủ.
4. dev2vec:APIs giả định rằng nếu developer thay đổi một source file thì họ có kiến thức cơ bản về API/library trong file đó. Giả định này có thể gây nhiễu.
5. Repository information có thể bị trùng giữa nhiều developer cùng đóng góp vào một project, làm giảm khả năng phân biệt expertise cá nhân.
6. Phương pháp chưa phân tích sâu coding style, code quality, architecture hoặc clean code.
7. Chưa đánh giá soft skills như teamwork, communication hoặc leadership.
8. Chưa áp dụng trực tiếp cho sinh viên Software Engineering.
9. Chưa kết hợp với dữ liệu học tập như transcript, self-assessment hoặc roadmap progress.

## Relevance to our topic

Bài báo rất liên quan đến đề tài của nhóm, đặc biệt là câu hỏi nghiên cứu:

**How can AI identify a student's latent talent through their coding patterns?**

Bài báo chứng minh rằng có thể sử dụng dữ liệu hoạt động GitHub để biểu diễn chuyên môn kỹ thuật của developer dưới dạng embedding vector. Điều này rất gần với ý tưởng của nhóm: phân tích GitHub profile, repository, issue, commit và API usage để suy ra sinh viên có thiên hướng nghề nghiệp nào.

Các điểm liên quan trực tiếp gồm:

- Phân tích GitHub activity để suy ra technical expertise.
- Biểu diễn developer expertise bằng embedding vector.
- Sử dụng repository metadata, README, issue history và API calls.
- Phân loại developer theo technical job roles.
- Các role như Backend, Frontend, Mobile, DevOps và Data Scientist gần với career paths trong hệ thống của nhóm.
- Có thể dùng làm nền tảng cho module latent talent identification.

Trong hệ thống của nhóm, ý tưởng dev2vec có thể được áp dụng để xây dựng career tendency profile cho sinh viên, ví dụ:

- Backend-oriented
- Frontend/UI-oriented
- Mobile-oriented
- DevOps-oriented
- Data-oriented

Thay vì chỉ dựa vào kỹ năng sinh viên tự nhập, hệ thống có thể dùng bằng chứng thực tế từ GitHub để đưa ra nhận định nghề nghiệp có cơ sở hơn.

## Possible improvement

Dựa trên bài báo này, nhóm có thể cải tiến hoặc mở rộng theo các hướng sau:

1. Áp dụng ý tưởng dev2vec cho sinh viên Software Engineering thay vì professional developers.
2. Kết hợp GitHub activity với student profile, transcript và self-declared skills.
3. Phân tích README.md để trích xuất project objective, tech stack và domain của project.
4. Phân tích repository structure để biết sinh viên thiên về frontend, backend, mobile, DevOps hay data.
5. Phân tích commit history để đánh giá mức độ tham gia và sự phát triển kỹ năng theo thời gian.
6. Phân tích issue và pull request để đánh giá problem-solving, collaboration và project management ability.
7. Phân tích dependency files như package.json, pom.xml, requirements.txt hoặc Dockerfile để nhận diện framework và công nghệ.
8. Bổ sung explainability cho career recommendation, ví dụ: “Sinh viên được gợi ý Backend Developer vì repository có nhiều REST API, database integration và authentication modules.”
9. Mở rộng career roles cho phù hợp với sinh viên như Backend Developer, Frontend Developer, Mobile Developer, DevOps Engineer, Cloud Engineer, Data Engineer và AI Engineer.
10. Dùng kết quả latent talent identification để cá nhân hóa Dynamic Learning Roadmap.
