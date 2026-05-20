# Paper 08 Summary

## Citation

Tên bài: Job Description Parsing with Explainable Transformer Based Ensemble Models to Extract the Technical and Non-Technical Skills  
Tác giả: Abbas Akkasi  
Năm: 2024  
Nguồn: Natural Language Processing Journal, Volume 9, Article 100102, Elsevier  
DOI/Link: https://doi.org/10.1016/j.nlp.2024.100102

## Problem

Bài báo giải quyết vấn đề trích xuất kỹ năng từ job descriptions, đặc biệt là technical skills và non-technical skills.

Trong thị trường lao động hiện nay, yêu cầu kỹ năng thay đổi nhanh do sự phát triển của công nghệ và số hóa nền kinh tế. Job descriptions chứa nhiều thông tin quan trọng về kỹ năng mà ứng viên cần có, nhưng dữ liệu này thường ở dạng văn bản tự do, không có cấu trúc, gây khó khăn cho việc phân tích tự động.

Một vấn đề lớn khác là tồn tại khoảng cách giữa kỹ năng sinh viên học được trong hệ thống giáo dục và kỹ năng thực tế mà doanh nghiệp yêu cầu. Vì vậy, việc tự động trích xuất kỹ năng từ job descriptions là bước quan trọng để phân tích skill gap, hỗ trợ người học, người tìm việc và các tổ chức giáo dục cập nhật chương trình đào tạo.

## Method

Bài báo đề xuất một explainable ensemble learning model để trích xuất cả hard skills và soft skills từ job descriptions.

Mô hình kết hợp nhiều thành phần:

1. Conditional Random Fields
   - Dùng cho sequence labeling.
   - Sử dụng hand-crafted features.
   - Đóng vai trò baseline truyền thống.

2. BiLSTM
   - Dùng để học thông tin ngữ cảnh theo hai chiều trong câu.
   - Phù hợp với bài toán gán nhãn chuỗi.

3. BiLSTM + CRF
   - Kết hợp khả năng học biểu diễn của BiLSTM với khả năng modeling label dependencies của CRF.

4. CNN
   - Được dùng để trích xuất local features từ BERT embeddings.
   - Giúp mô hình nhận diện pattern cục bộ trong văn bản.

5. BERT Embeddings
   - Sử dụng BERT để tạo contextualized word embeddings.
   - Giúp mô hình hiểu ngữ cảnh của từ trong job descriptions.

6. Ensemble Model
   - Kết hợp output của nhiều extractors bằng majority voting.
   - Mục tiêu là tận dụng điểm mạnh của nhiều mô hình khác nhau.

7. Multi-task Learning
   - Huấn luyện các deep models trong cơ chế multi-task learning.
   - Giúp cải thiện performance và cân bằng precision-recall.

8. Explainability with LIME
   - Sử dụng Local Interpretable Model-Agnostic Explanations để giải thích quyết định của mô hình.
   - Giúp hiểu token nào ảnh hưởng đến dự đoán skill label.

## Dataset

Bài báo tự xây dựng dataset vì không có dataset chuẩn công khai cho bài toán skill extraction.

Dữ liệu được thu thập như sau:

- Scrape job descriptions từ Glassdoor, LinkedIn, Indeed và StepStone.
- Thu thập thêm web content bằng Google Search API.
- Tập trung vào 22 IT-related job roles có nhu cầu cao.

Các job roles gồm:

- Software Engineer
- UX Designer
- Database Administrator
- Business Analyst
- Data Scientist
- Java Developer
- System Engineer
- Cyber Security Specialist
- Machine Learning Engineer
- Mobile Applications Developer
- Data Analyst
- Data Engineer
- Backend Developer
- Frontend Developer
- Cloud Architect
- DevOps Engineer
- Network Engineer
- Blockchain Developer
- Big Data Architect
- Và một số vai trò IT khác

Thông tin dataset:

- Ban đầu thu thập 30,695 job descriptions và web documents.
- Sau khi loại bỏ dữ liệu trùng lặp và không đầy đủ, còn 22,874 documents.
- Dataset cuối cùng gồm 207,327 sentences.
- Danh sách ban đầu có 7,170 hard skills và 269 soft skills.
- Sau khi lọc thủ công, còn 2,043 hard skills liên quan đến IT.
- Dữ liệu được annotate theo IOB scheme:
  - B-SKILL
  - I-SKILL
  - B-H-SKILL
  - I-H-SKILL
  - B-S-SKILL
  - I-S-SKILL
  - OUT

## Evaluation

Bài báo đánh giá mô hình bằng các metrics phổ biến cho bài toán skill extraction / sequence labeling:

- Precision
- Recall
- F1-score

Bài báo đánh giá theo hai cách:

1. Tách riêng hard skills và soft skills
   - Đánh giá khả năng trích xuất technical skills và non-technical skills riêng biệt.

2. Gộp hard skills và soft skills thành SKILL
   - Đánh giá khả năng nhận diện skill nói chung.

Do không có test dataset công khai, bài báo dùng 5-fold cross-validation.

Ngoài ra, bài báo sử dụng:

- 5 × 2 cross-validation paired t-test để kiểm tra ý nghĩa thống kê giữa mô hình đề xuất và baseline tốt nhất.
- LIME để phân tích explainability của mô hình.

## Results

Kết quả cho thấy ensemble model đạt hiệu quả tốt hơn các baseline như CRF, BiLSTM và BiLSTM+CRF.

Khi đánh giá hard skills và soft skills riêng biệt:

- CRF đạt F1 = 0.37 cho soft skills và F1 = 0.43 cho hard skills.
- BiLSTM+CRF_2 đạt F1 = 0.63 cho soft skills và F1 = 0.68 cho hard skills.
- Ensemble Model đạt F1 = 0.66 cho soft skills và F1 = 0.71 cho hard skills.
- Ensemble Model với Multi-task Learning đạt:
  - Soft skills F1 = 0.67
  - Hard skills F1 = 0.72

Khi gộp hard skills và soft skills thành một nhãn SKILL:

- CRF đạt F1 = 0.45.
- BiLSTM+CRF_2 đạt F1 = 0.67.
- Ensemble Model đạt F1 = 0.72.
- Ensemble Model với Multi-task Learning đạt F1 = 0.74.

Bài báo cũng cho thấy:

- Deep learning models vượt trội hơn CRF truyền thống.
- Ensemble learning giúp cải thiện precision và recall.
- Multi-task learning giúp tăng nhẹ hiệu quả so với ensemble thông thường.
- Mô hình trích xuất hard skills tốt hơn soft skills do dữ liệu hard skills nhiều hơn và dễ nhận diện hơn.
- 5 × 2cv paired t-test cho thấy cải thiện của mô hình đề xuất có ý nghĩa thống kê.
- LIME cho thấy mô hình đưa ra quyết định dựa trên các từ xung quanh skill terms, giúp tăng khả năng giải thích.

## Limitations

Một số hạn chế của bài báo gồm:

1. Dataset được xây dựng riêng, chưa phải benchmark chuẩn công khai.
2. Dữ liệu tập trung vào English job descriptions, chưa đánh giá trên ngôn ngữ khác.
3. Mô hình trích xuất soft skills kém hơn hard skills.
4. Dataset có sự mất cân bằng giữa hard skills và soft skills.
5. Mô hình còn gặp khó khăn với multi-word skills hoặc kỹ năng có cụm từ dài.
6. CRF với hand-crafted features có hiệu quả thấp nếu không có feature engineering tốt.
7. BERT embeddings được dùng nhưng không nhất thiết được fine-tune sâu cho từng domain.
8. LIME chỉ giải thích cục bộ cho từng dự đoán, chưa cung cấp cái nhìn toàn cục về mô hình.
9. Việc annotation skill cần nhiều công sức và có thể phụ thuộc vào chuyên gia.

## Relevance to our topic

Bài báo rất liên quan đến đề tài của nhóm ở phần AI Method và Market Pulse.

Trong đề tài của nhóm, hệ thống cần thu thập job postings từ các nền tảng như LinkedIn hoặc TopCV, sau đó phân tích keyword frequency và xu hướng kỹ năng. Bài này cung cấp một phương pháp mạnh hơn keyword frequency thông thường bằng cách dùng BERT, BiLSTM, CRF, CNN và ensemble learning để trích xuất technical và non-technical skills từ job descriptions.

Các điểm liên quan gồm:

- Skill extraction từ job descriptions.
- Phân biệt technical skills và soft skills.
- Sử dụng BERT để hiểu ngữ cảnh trong job postings.
- Hỗ trợ phân tích skill demand trong thị trường việc làm.
- Có thể dùng cho Skill Gap Analysis bằng cách so sánh kỹ năng sinh viên với kỹ năng doanh nghiệp yêu cầu.
- Có thể hỗ trợ Dynamic Roadmap bằng cách xác định kỹ năng nào cần ưu tiên học.
- Có explainability bằng LIME, giúp giải thích vì sao một từ/cụm từ được nhận diện là skill.

## Possible improvement

Dựa trên bài báo này, nhóm có thể áp dụng hoặc cải tiến theo các hướng sau:

1. Ở giai đoạn đầu, nhóm có thể dùng keyword extraction đơn giản cho Market Pulse, sau đó nâng cấp lên BERT-based skill extraction.
2. Xây dựng skill taxonomy riêng cho Software Engineering gồm Backend, Frontend, Mobile, DevOps, Cloud, Data Engineering và AI Engineering.
3. Tách technical skills và soft skills để báo cáo skill gap rõ hơn.
4. Áp dụng BERT hoặc transformer model để trích xuất kỹ năng từ job postings trên LinkedIn hoặc TopCV.
5. Dùng kết quả skill extraction để cập nhật Dynamic Learning Roadmap theo real-time job trends.
6. Tích hợp GitHub README analysis để so sánh kỹ năng trong project cá nhân với kỹ năng được trích xuất từ job market.
7. Thêm explainability cho Skill Gap Analysis, ví dụ: “Docker được đề xuất vì xuất hiện nhiều trong job descriptions DevOps.”
8. Ưu tiên các kỹ năng có tần suất cao và có liên quan trực tiếp đến target career role.
9. Kết hợp hard skills và soft skills trong roadmap, ví dụ technical skill như Spring Boot và soft skill như teamwork hoặc communication.
10. Tạo dashboard hiển thị skill demand theo từng role cụ thể như Backend Developer, DevOps Engineer, Cloud Architect hoặc Data Engineer.
