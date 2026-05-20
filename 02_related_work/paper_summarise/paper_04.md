# Paper 04 Summary

## Citation

Tên bài: Reducing Career Path Anxiety among Vocational Students with an AI-Driven Career Guidance System Integrating Skills Mapping, Adaptive Mentoring, and Real-Time Labor Market Intelligence  
Tác giả: Andry Ananda Putra Tanggu Mara, Herman Dwi Surjono, Nurhening Yuniarti  
Năm: 2025  
Nguồn: Preprint / Computer Science and Mathematics - Artificial Intelligence and Machine Learning  
DOI/Link: https://doi.org/10.5281/zenodo.17355217

## Problem

Bài báo giải quyết vấn đề lo lắng khi lựa chọn nghề nghiệp của học sinh/sinh viên giáo dục nghề nghiệp. Nguyên nhân chính đến từ việc người học không chắc chắn về nhu cầu thị trường lao động, thiếu sự hướng dẫn từ mentor/counselor, và tồn tại khoảng cách giữa chương trình đào tạo với kỹ năng thực tế mà doanh nghiệp yêu cầu.

Các hệ thống định hướng nghề nghiệp trước đây thường chỉ tập trung vào matching kỹ năng hoặc cung cấp thông tin nghề nghiệp tĩnh, chưa chú trọng nhiều đến yếu tố tâm lý như career anxiety và chưa tích hợp dữ liệu thị trường lao động theo thời gian thực.

## Method

Bài báo đề xuất một hệ thống AI-driven career guidance system gồm ba module chính:

1. Skills Mapping Engine
   - Sử dụng supervised machine learning để phân tích năng lực học tập, chứng chỉ, hoạt động ngoại khóa và kinh nghiệm thực tập.
   - Mapping kỹ năng của học sinh/sinh viên với yêu cầu nghề nghiệp.

2. Adaptive Mentoring Module
   - Sử dụng AI chatbot để hỗ trợ tư vấn nghề nghiệp cá nhân hóa.
   - Kết hợp mentor matching để kết nối người học với mentor phù hợp.

3. Real-Time Labor Market Intelligence
   - Sử dụng Natural Language Processing để phân tích job postings và báo cáo xu hướng ngành.
   - Cập nhật thông tin kỹ năng, nghề nghiệp và nhu cầu thị trường theo thời gian thực.

Ngoài ra, hệ thống còn sử dụng:

- Random Forest Classifier để dự đoán career pathway phù hợp.
- K-Means clustering để nhóm sinh viên theo hồ sơ kỹ năng và mức độ lo lắng nghề nghiệp.
- Collaborative filtering để gợi ý roadmap kỹ năng.
- Content-based filtering để gợi ý công việc.
- Multilingual BERT để xử lý ngôn ngữ và chuẩn hóa mô tả kỹ năng.
- SHAP để giải thích lý do hệ thống đưa ra khuyến nghị.

## Dataset

Bài báo sử dụng dữ liệu từ học sinh/sinh viên giáo dục nghề nghiệp tại Indonesia.

Dữ liệu gồm:

- Hồ sơ học tập
- Chứng chỉ nghề nghiệp
- Kinh nghiệm thực tập
- Kết quả tự đánh giá kỹ năng
- Chỉ số career anxiety
- Dữ liệu tương tác với chatbot
- Dữ liệu mentoring
- Dữ liệu job postings từ thị trường lao động
- Báo cáo xu hướng ngành

Theo bài báo, hệ thống đã phân tích khoảng 500 job postings để cung cấp labor market intelligence. Nghiên cứu có sự tham gia của học sinh/sinh viên từ các trường nghề, counselor và industry mentor.

## Evaluation

Bài báo sử dụng mixed-methods design, kết hợp định lượng và định tính.

Các phương pháp đánh giá gồm:

- Pre-test và post-test để đo career anxiety trước và sau khi dùng hệ thống.
- Paired-sample t-test để kiểm tra mức giảm anxiety.
- Regression modeling để phân tích tác động của hệ thống.
- System analytics để đo mức độ tương tác của người dùng.
- Interview và focus group để thu thập phản hồi định tính.
- Đánh giá hiệu năng mô hình AI bằng:
  - Accuracy
  - Precision
  - Recall
  - F1-score
  - ROC-AUC
- Đánh giá chatbot bằng:
  - BLEU
  - ROUGE
- Đánh giá sự hài lòng của người dùng bằng Likert scale.

## Results

Kết quả cho thấy hệ thống AI-driven career guidance có tác động tích cực đến cả năng lực định hướng nghề nghiệp và tâm lý của người học.

Một số kết quả chính:

- Career anxiety giảm đáng kể sau khi sử dụng hệ thống.
- Skills mapping module đạt accuracy khoảng 87%.
- Mô hình đạt Precision = 0.85, Recall = 0.83, F1-score = 0.84.
- ROC-AUC đạt 0.89.
- Chatbot đạt BLEU score = 0.71.
- Hệ thống hỗ trợ hơn 2,400 lượt tương tác chatbot.
- 78% học sinh/sinh viên báo cáo rằng họ tự tin hơn trong việc lập kế hoạch nghề nghiệp.
- 65% người dùng thực hiện lại skill-gap analysis hơn ba lần.
- Labor market analytics xử lý khoảng 500 job postings để cung cấp insight về thị trường lao động.

Kết quả định tính cũng cho thấy sinh viên cảm thấy tự tin hơn, hiểu rõ hơn về skill gap và có định hướng nghề nghiệp thực tế hơn.

## Limitations

Bài báo nêu một số hạn chế:

1. Mẫu nghiên cứu còn giới hạn ở một số trường nghề tại Indonesia, nên khả năng khái quát hóa chưa cao.
2. Thời gian đánh giá ngắn, chủ yếu đo tác động trong vài tuần hoặc vài tháng.
3. Chưa đánh giá dài hạn về kết quả việc làm thực tế, career persistence hoặc career adaptability.
4. Hệ thống có nguy cơ tồn tại algorithmic bias nếu dữ liệu thị trường lao động phản ánh các bất bình đẳng sẵn có.
5. Cần cải thiện thêm yếu tố trust, transparency và ethical safeguards.
6. Việc triển khai ở trường thiếu hạ tầng số hoặc internet yếu có thể gặp khó khăn.
7. Sự kết hợp giữa AI mentoring và human mentorship chưa được khai thác đầy đủ.

## Relevance to our topic

Bài báo rất liên quan đến đề tài của nhóm vì hệ thống trong bài có nhiều thành phần giống với nền tảng mà nhóm đang đề xuất.

Các điểm liên quan trực tiếp gồm:

- AI-based career guidance system
- Skill mapping / skill gap analysis
- Adaptive mentoring bằng AI chatbot
- Career roadmap cá nhân hóa
- Real-time labor market intelligence
- Phân tích job postings bằng NLP
- Recommendation system cho career path
- Tích hợp counselor và industry mentor
- Dashboard và báo cáo kỹ năng cho người học

Đặc biệt, bài báo có module skills mapping, adaptive mentoring và labor market intelligence, rất gần với các module của đề tài nhóm như AI Virtual Mentor, Dynamic Roadmap, Skill Gap Analysis và Market Pulse.

## Possible improvement

Dựa trên bài báo này, nhóm có thể cải tiến hoặc mở rộng theo các hướng sau:

1. Tập trung riêng vào sinh viên ngành Software Engineering thay vì vocational students nói chung.
2. Xây dựng career paths cụ thể cho ngành phần mềm như Backend Developer, Frontend Developer, DevOps Engineer, Data Engineer, Mobile Developer hoặc Cloud Engineer.
3. Tích hợp GitHub repository analysis để đánh giá kỹ năng thực tế từ project cá nhân.
4. Sử dụng README.md analysis để tự động trích xuất tech stack và mục tiêu dự án.
5. Kết hợp dữ liệu job postings từ LinkedIn, TopCV hoặc các trang tuyển dụng IT tại Việt Nam.
6. Tạo Dynamic Learning Roadmap dựa trên skill gap, career goal và xu hướng thị trường.
7. Cho phép Academic Counselor và Industry Mentor review hoặc điều chỉnh roadmap.
8. Đánh giá hệ thống bằng cả recommendation relevance, user satisfaction, expert rating và response time.
9. Bổ sung e-portfolio URL để hỗ trợ sinh viên trình bày năng lực với nhà tuyển dụng.
10. Nghiên cứu dài hạn hơn về mức độ cải thiện readiness khi sinh viên sử dụng roadmap trong nhiều học kỳ.
