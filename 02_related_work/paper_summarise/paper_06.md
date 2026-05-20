# Paper 06 Summary

## Citation

Tên bài: Skillmatch.ai: Applying a Skills First Framework to Matching Algorithms – Enhancing Role Recommendations through Comprehensive Occupational Similarity Analysis  
Tác giả: Hanna Helmich Borchgrevink Pedersen  
Năm: 2024  
Nguồn: Master’s Work Project, Nova School of Business and Economics  
DOI/Link: https://github.com/victorbjorsvik/workproject_matching_algo

## Problem

Bài nghiên cứu giải quyết vấn đề các phương pháp tuyển dụng và gợi ý nghề nghiệp truyền thống thường dựa quá nhiều vào bằng cấp, chức danh công việc hoặc kinh nghiệm trước đó, thay vì đánh giá trực tiếp kỹ năng thực tế của ứng viên.

Điều này có thể dẫn đến:

- Bỏ sót ứng viên có kỹ năng phù hợp nhưng không có bằng cấp truyền thống.
- Khó xác định mức độ phù hợp giữa kỹ năng cá nhân và yêu cầu công việc.
- Khó hỗ trợ chuyển đổi vai trò nghề nghiệp dựa trên kỹ năng.
- Thiếu công cụ thực tế để triển khai skills-first hiring và career development.

Bài nghiên cứu đặt trọng tâm vào việc xây dựng một hệ sinh thái ứng dụng AI giúp matching giữa ứng viên và công việc, đồng thời hỗ trợ role recommendation dựa trên skill similarity.

## Method

Bài nghiên cứu đề xuất Skillmatch.ai, một hệ sinh thái ứng dụng AI theo hướng skills-first.

Các phương pháp chính gồm:

1. Skills-first matching framework
   - Ưu tiên kỹ năng và năng lực thay vì bằng cấp hoặc job title.
   - So sánh kỹ năng của ứng viên với yêu cầu công việc.

2. CV-job matching model
   - Trích xuất nội dung từ CV dạng PDF.
   - Trích xuất kỹ năng từ CV và job description.
   - Biểu diễn kỹ năng bằng embedding model.
   - Tính similarity score để xếp hạng ứng viên phù hợp với job description.

3. NLP-based skill extraction
   - Sử dụng spaCy Entity Ruler.
   - Dùng custom skill pattern file để nhận diện kỹ năng công nghệ.
   - Trích xuất kỹ năng từ CV và job descriptions.

4. Embedding and semantic similarity
   - Sử dụng sentence transformer, đặc biệt là all-mpnet-base-v2 và all-MiniLM-L6-v2.
   - So sánh semantic similarity bằng cosine similarity.
   - Thử nghiệm hai cách biểu diễn kỹ năng:
     - Bag-of-Skills
     - Skill-by-Skill

5. Synthetic data generation
   - Do khó tiếp cận dữ liệu CV thật vì vấn đề riêng tư và GDPR, bài nghiên cứu dùng synthetic data.
   - Sử dụng OpenAI GPT-4o-Mini để tạo CV giả lập từ job descriptions.
   - Dùng nhãn binary: good fit và bad fit.

6. Role recommendation model
   - Sử dụng dữ liệu O\*NET.
   - So sánh vai trò nghề nghiệp dựa trên skills, knowledge, abilities, tasks và detailed work activities.
   - Dùng similarity analysis và network analysis để tìm các occupation có liên quan.

7. Web application ecosystem
   - Xây dựng Skillmatch.ai web app gồm các chức năng:
     - CV screening
     - Tailored interview questions
     - Bespoke rejection letters
     - Role similarity / role recommendation

## Dataset

Bài nghiên cứu sử dụng nhiều nguồn dữ liệu khác nhau:

1. Kaggle Survey Dataset 2022
   - Gồm 23,998 rows và 296 columns.
   - Chứa thông tin về vai trò công việc, kỹ năng, công cụ, ngành nghề và nền tảng học vấn.
   - Sau khi cleaning còn khoảng 9,000 observations.
   - Dùng để phân tích skill overlap giữa các tech roles.

2. O\*NET Dataset
   - Dùng để lấy dữ liệu về occupational skills, tasks, knowledge, abilities, work activities và role descriptions.
   - Dùng để xây dựng role similarity model và role recommendation.

3. Job descriptions
   - 100 job descriptions trong lĩnh vực công nghệ.
   - Được dùng để tạo synthetic CV data.

4. Synthetic CV dataset
   - Tạo bằng OpenAI GPT-4o-Mini.
   - Dataset cuối cùng gồm 100 job descriptions, mỗi job có 6 CV.
   - Tổng cộng 600 job description–CV pairs.
   - Nhãn binary gồm:
     - 1 = good fit
     - 0 = bad fit

## Evaluation

Bài nghiên cứu đánh giá mô hình bằng nhiều cách:

1. Similarity analysis
   - Cosine similarity
   - Euclidean distance
   - Skill overlap giữa các vai trò công nghệ.

2. Binary classification metrics
   - Precision
   - Recall
   - F1-score

3. Ranking metrics
   - Precision@K
   - Mean Reciprocal Rank
   - Mean Average Precision

4. Processing time
   - Đánh giá khả năng mở rộng và tốc độ xử lý.

5. Mean Similarity Score Difference
   - Đo khả năng phân biệt giữa good-fit và bad-fit candidates.

6. Benchmarking model components
   - So sánh Bag-of-Skills và Skill-by-Skill.
   - So sánh các embedding models:
     - all-mpnet-base-v2
     - all-MiniLM-L6-v2
     - NV-Embed-v2
     - SFR-Embedding
   - So sánh Bi-Encoder và Cross-Encoder.

## Results

Bài nghiên cứu cho thấy skills-first matching có tiềm năng hỗ trợ tuyển dụng và định hướng nghề nghiệp dựa trên kỹ năng.

Một số kết quả chính:

- Skill overlap giữa các vai trò công nghệ khá cao, hỗ trợ khả năng chuyển đổi vai trò dựa trên kỹ năng.
- Skill-by-Skill representation đạt F1-score 0.7471, tốt hơn Bag-of-Skills với F1-score 0.62.
- Threshold cosine similarity 0.4 cho Skill-by-Skill đạt hiệu quả tốt nhất.
- all-MiniLM-L6-v2 được xem là lựa chọn tối ưu vì cân bằng tốt giữa hiệu năng và tốc độ xử lý.
- NV-Embed-v2 đạt F1-score cao nhất trong một thử nghiệm nhưng thời gian xử lý quá lớn, không phù hợp cho triển khai thực tế.
- Bi-Encoder được chọn thay vì Cross-Encoder vì tốc độ nhanh hơn nhiều trong khi hiệu năng gần tương đương.
- Role-to-role model đạt Precision@10 = 0.65, Precision@20 = 0.49, MRR = 0.85 và MAP khoảng 0.53 khi benchmark với O\*NET.
- Web application Skillmatch.ai chứng minh khả năng triển khai thực tế của hệ thống skills-first.

## Limitations

Một số hạn chế của bài nghiên cứu gồm:

1. Thiếu real-world labelled dataset để đánh giá mô hình trong điều kiện thực tế.
2. Synthetic data có thể không phản ánh đầy đủ sự phức tạp của CV và job descriptions thật.
3. Skill extraction phụ thuộc vào custom pattern file, nên có thể bỏ sót kỹ năng mới hoặc cách viết khác nhau.
4. Embedding models chưa được fine-tune riêng cho domain tuyển dụng hoặc career development.
5. Mô hình chưa có explainability rõ ràng cho từng recommendation.
6. Một số similarity score có thể bị ảnh hưởng bởi cách embedding biểu diễn kỹ năng.
7. Role recommendation còn phụ thuộc nhiều vào dữ liệu O\*NET và chưa có expert validation đầy đủ.
8. Việc triển khai thực tế cần xử lý thêm các vấn đề về privacy, bias, fairness và GDPR.

## Relevance to our topic

Bài này liên quan đến đề tài của nhóm ở khía cạnh AI method và technical approach.

Các điểm liên quan gồm:

- Skill mapping
- Skill-based recommendation
- Semantic similarity
- Embedding-based matching
- Career role recommendation
- Role transition based on skill overlap
- Skill gap identification
- AI-based career development
- CV/GitHub/profile analysis cho định hướng nghề nghiệp

Đề tài của nhóm cũng cần phân tích kỹ năng hiện tại của sinh viên và mapping với target career role như Backend Developer, DevOps Engineer, Data Engineer hoặc Mobile Developer. Vì vậy, phương pháp skills-first matching, embedding model và similarity analysis trong bài này có thể dùng làm cơ sở cho module Skill Gap Analysis và Dynamic Roadmap.

## Possible improvement

Dựa trên bài nghiên cứu này, nhóm có thể cải tiến theo các hướng sau:

1. Thay CV-job matching bằng student profile–career role matching.
2. Sử dụng GitHub repositories và README.md để trích xuất kỹ năng thực tế của sinh viên.
3. Kết hợp skills-first matching với Software Engineering Skill Tree.
4. Tạo skill gap report bằng cách so sánh current skills với required skills của target career role.
5. Dùng embedding model để so sánh semantic similarity giữa kỹ năng sinh viên và yêu cầu công việc.
6. Bổ sung explanation cho từng recommendation, ví dụ: “Bạn phù hợp với Backend Developer vì đã có Java, SQL, REST API.”
7. Kết hợp dữ liệu job postings từ LinkedIn hoặc TopCV để cập nhật skill demand.
8. Tạo Dynamic Learning Roadmap dựa trên missing skills thay vì chỉ xếp hạng career role.
9. Bổ sung đánh giá từ Academic Counselor hoặc Industry Mentor để tăng độ tin cậy.
10. Đánh giá hệ thống bằng Precision@K, expert rating, user satisfaction và response time.
