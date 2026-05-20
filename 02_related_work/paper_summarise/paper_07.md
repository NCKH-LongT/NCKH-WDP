# Paper 07 Summary

## Citation

Tên bài: NLP-Driven Labor Market Intelligence via Skill Extraction, Demand Clustering, and Salary Regression  
Tác giả: Abdelhadi Sayed  
Năm: 2026  
Nguồn: Project Report, Arab International University, Faculty of Informatics and Communication Engineering  
DOI/Link: Not available

## Problem

Bài báo/đồ án giải quyết vấn đề thị trường lao động thay đổi nhanh, khiến sinh viên, người tìm việc và career counselors gặp khó khăn trong việc xác định kỹ năng đang được yêu cầu, mức lương kỳ vọng và xu hướng nghề nghiệp.

Các nền tảng tìm việc truyền thống thường chỉ hỗ trợ tìm kiếm bằng keyword, chưa cung cấp đủ phân tích về:

- Kỹ năng nào đang có nhu cầu cao.
- Kỹ năng nào thường xuất hiện cùng nhau.
- Mức lương thay đổi theo vị trí, kinh nghiệm và địa điểm.
- Xu hướng tăng/giảm của nhu cầu tuyển dụng.
- Gợi ý công việc cá nhân hóa dựa trên CV hoặc skill profile.

Vì vậy, bài này đề xuất một hệ thống Labor Market Intelligence dùng NLP và Machine Learning để chuyển dữ liệu job postings thô thành insight có thể sử dụng cho định hướng nghề nghiệp và phát triển kỹ năng.

## Method

Bài nghiên cứu đề xuất một hệ thống NLP-driven labor market intelligence gồm các thành phần chính:

1. Job Posting Aggregation
   - Thu thập job advertisements từ nhiều nguồn online.
   - Lưu trữ thông tin như job title, description, location, company và salary.

2. NLP Skill Extraction
   - Sử dụng Natural Language Processing để xử lý job descriptions.
   - Sử dụng Named Entity Recognition để trích xuất technical skills và soft skills.
   - Dùng transformer-based models như BERT để tăng khả năng hiểu ngữ cảnh trong mô tả công việc.

3. Skill Demand Clustering
   - Sử dụng HDBSCAN để nhóm các kỹ năng liên quan.
   - Phát hiện các skill clusters và demand patterns.
   - Xây dựng skill co-occurrence networks để hiểu kỹ năng nào thường đi cùng nhau.

4. Salary Regression
   - Sử dụng Random Forest Regression và Bayesian Regression.
   - Dự đoán mức lương dựa trên job title, location, experience level và required skills.
   - Cung cấp salary estimate kèm confidence interval.

5. Dashboard and Visualization
   - Xây dựng backend bằng Flask.
   - Xây dựng frontend dashboard bằng React.js.
   - Dùng MongoDB để lưu job postings, extracted skills, user profiles và analytics results.
   - Cung cấp heatmap, salary estimator, skill demand analytics và personalized job recommendation.

## Dataset

Bài nghiên cứu sử dụng nhiều dataset phục vụ cho từng phần của hệ thống:

1. Job Posting Corpus
   - Khoảng 50,000 job postings.
   - Nguồn gồm Kaggle job datasets, Indeed sample data và simulated postings.
   - Mỗi posting gồm job title, description, company, location, required skills và salary nếu có.

2. Skill Annotation Dataset
   - 5,000 job descriptions được annotate thủ công cho skill entities.
   - Annotation scheme gồm:
     - B-TECH
     - I-TECH
     - B-SOFT
     - I-SOFT
     - O
   - Inter-annotator agreement đạt 87%, Cohen's Kappa = 0.84.

3. Salary Benchmark Dataset
   - 10,000 job postings có salary ranges.
   - Cân bằng theo job families và geographic regions.
   - Dùng để huấn luyện và đánh giá salary regression models.

4. ESCO Taxonomy
   - Sử dụng ESCO v1.2 với hơn 13,000 skills.
   - Dùng để chuẩn hóa kỹ năng và kiểm tra kết quả clustering.

## Evaluation

Bài nghiên cứu đánh giá hệ thống theo nhiều nhóm tiêu chí:

1. Skill Extraction Evaluation
   - Sử dụng 5-fold cross-validation.
   - Đánh giá bằng Precision, Recall, F1-score ở token level và entity level.
   - So sánh BERT-based NER với spaCy NER và regex baseline.

2. Clustering Validation
   - Silhouette Score.
   - Davies-Bouldin Index.
   - Adjusted Rand Index khi so với ESCO taxonomy.
   - Stability testing khi thêm dữ liệu mới.

3. Salary Regression Testing
   - Hold-out test set 20%.
   - 10-fold cross-validation.
   - Metrics gồm:
     - R-squared
     - Mean Absolute Error
     - Root Mean Square Error
     - Mean Absolute Percentage Error
   - So sánh Random Forest, Bayesian Regression và Linear Regression baseline.

4. API Performance Testing
   - Load testing với 100 concurrent users.
   - Đo response time cho search, prediction và analytics endpoints.

5. Recommendation Evaluation
   - Precision@10.
   - Recall@10.

## Results

Kết quả cho thấy hệ thống đạt hiệu quả tốt trên nhiều thành phần.

Một số kết quả chính:

- Skill extraction bằng BERT NER đạt:
  - Precision = 91.2%
  - Recall = 87.6%
  - F1-score = 89.3%
  - Entity-level F1 = 88.1%

- BERT NER vượt spaCy baseline:
  - spaCy F1 = 73.7%
  - Regex baseline entity-level F1 = 62.4%

- Skill clustering bằng HDBSCAN đạt:
  - Silhouette Score = 0.42
  - Davies-Bouldin Index = 0.87
  - ESCO alignment ARI = 0.73
  - Noise point ratio = 12.4%

- Salary prediction bằng Random Forest đạt:
  - R² = 92.7%
  - MAE = $6,245
  - RMSE = $8,910
  - MAPE = 11.3%

- Bayesian Regression đạt R² = 88.4%.

- API performance đạt yêu cầu:
  - Search p95 latency = 320 ms
  - Prediction p95 latency = 180 ms
  - Analytics p95 latency = 450 ms
  - Hệ thống xử lý được 250 concurrent users.

- CV parsing đạt skill extraction F1 = 84.2%.

- Recommendation đạt:
  - Precision@10 = 76.8%
  - Recall@10 = 68.3%

## Limitations

Một số hạn chế của bài nghiên cứu gồm:

1. Dữ liệu job postings chủ yếu là static datasets, chưa tích hợp trực tiếp real-time job board APIs.
2. Salary information chỉ xuất hiện trong khoảng 35% job postings, có thể gây selection bias.
3. Soft skill extraction khó hơn technical skill extraction, F1 thấp hơn.
4. Hệ thống hiện tập trung vào English-language job postings.
5. CV upload có vấn đề về privacy vì người dùng phải chia sẻ dữ liệu cá nhân.
6. BERT inference còn tốn tài nguyên tính toán nếu triển khai real-time trên quy mô lớn.
7. Clustering bằng HDBSCAN cần thêm phương pháp tự động đặt tên cluster dễ hiểu hơn.
8. Hệ thống có nguy cơ model drift vì thị trường lao động thay đổi nhanh.
9. Chưa có kết nối trực tiếp với learning platforms để đề xuất khóa học xử lý skill gaps.

## Relevance to our topic

Bài này rất liên quan đến đề tài của nhóm, đặc biệt là module Market Pulse và Skill Gap Analysis.

Các điểm liên quan gồm:

- Phân tích job postings bằng NLP.
- Trích xuất kỹ năng từ mô tả công việc.
- Phân tích demand trends của kỹ năng.
- Nhóm các kỹ năng liên quan bằng clustering.
- Dự đoán salary dựa trên job title, location, experience và required skills.
- Hiển thị dashboard với heatmap, trend chart và skill demand analytics.
- Upload CV để trích xuất kỹ năng và đưa ra personalized job recommendation.

Trong đề tài của nhóm, Market Pulse cần scrape dữ liệu từ LinkedIn hoặc TopCV, phân tích keyword frequency và hiển thị interactive trend charts. Bài này cung cấp hướng triển khai sâu hơn bằng NLP, BERT, HDBSCAN, salary regression và dashboard visualization.

## Possible improvement

Dựa trên bài nghiên cứu này, nhóm có thể cải tiến hoặc áp dụng theo các hướng sau:

1. Thay job seeker chung bằng Software Engineering students.
2. Thu thập job postings từ LinkedIn, TopCV hoặc các nền tảng tuyển dụng IT tại Việt Nam.
3. Dùng NLP để trích xuất required skills cho từng target career role như Backend Developer, DevOps Engineer, Data Engineer hoặc Mobile Developer.
4. Kết hợp job market skill demand với Dynamic Learning Roadmap để ưu tiên kỹ năng đang có nhu cầu cao.
5. Dùng keyword frequency analysis đơn giản ở bản đầu, sau đó mở rộng sang BERT-based skill extraction.
6. Tạo Skill Gap Analysis bằng cách so sánh current skills của sinh viên với extracted skills từ job postings.
7. Hiển thị trend charts cho các kỹ năng như Docker, Kubernetes, React, Spring Boot, AWS, SQL, Python.
8. Tích hợp GitHub portfolio analysis để so sánh kỹ năng trong project cá nhân với kỹ năng thị trường yêu cầu.
9. Bổ sung explainable recommendation, ví dụ: “Docker được ưu tiên vì xuất hiện trong 42% job postings DevOps.”
10. Mở rộng hệ thống để đề xuất learning resources hoặc courses nhằm lấp skill gap.
