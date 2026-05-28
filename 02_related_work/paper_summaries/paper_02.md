# Paper 02 Summary

## Citation
- **Tên bài:** Sentiment Analysis of Hotel Reviews Using Machine Learning Techniques
- **Tác giả:** Sarah Anis, Sally Saad, & Mostafa Aref
- **Năm:** 2021
- **Nguồn:** Springer Nature Switzerland (Advanced Intelligent Systems and Computing)
- **DOI/Link:** Trong drive

## Problem
Bài báo giải quyết bài toán tự động nhận diện và phân loại ý kiến khách hàng từ các nguồn đánh giá khách sạn trực tuyến. Khó khăn lớn nhất trong dữ liệu văn bản phản hồi là sự xuất hiện xen kẽ giữa các câu khách quan (chỉ nêu sự thật, mốc thời gian, thông số thực tế) và câu chủ quan (thể hiện thái độ, cảm xúc khen/chê). Việc giữ lại các câu khách quan trong quá trình huấn luyện làm nhiễu thông tin và giảm đáng kể độ chính xác của các mô hình phân loại truyền thống.

## Method
Nghiên cứu đề xuất một quy trình xử lý văn bản gồm 2 giai đoạn độc lập (Pipeline):
1. **Sentiment Detection (Subjectivity Detection):** Áp dụng thuật toán phân cụm mờ Fuzzy C-means (FCM) để phân tách văn bản thành các câu Khách quan (Objective) và Chủ quan (Subjective). Các câu khách quan bị loại bỏ hoàn toàn nhằm mục đích khử nhiễu dữ liệu.
2. **Sentiment Classification:** Đưa tập từ vựng chủ quan sau khi làm sạch qua mô hình Word2Vec để chuyển đổi thành các vector đặc trưng liên tục 100 chiều. Sau đó, sử dụng 5 thuật toán học máy giám sát gồm: Support Vector Machine (SVM), Naïve Bayes (NB), K-Nearest Neighbor (KNN), Logistic Regression (LR), và Random Forest (RF) để phân loại phân cực cảm xúc (Tích cực / Tiêu cực).
- **Ensemble Learning:** Thử nghiệm một mô hình biểu quyết kết hợp (Ensemble) tích hợp cả 5 bộ phân loại trên để đối chiếu và nâng cao hiệu năng.

## Rubric / Criteria
Tiêu chí phân loại của hệ thống dựa trên 2 tầng bộ lọc rõ ràng:
- Tầng 1: Tính chủ quan (Subjective Expressions - mang cảm xúc, quan điểm) vs. Tính khách quan (Objective Expressions - mang tính sự thật, dữ liệu đo lường được).
- Tầng 2: Phân cực cảm xúc Tích cực (Positive) vs. Tiêu cực (Negative).

## Dataset / Context
- **Dữ liệu:** Sử dụng tập dữ liệu gồm 38,932 bài đánh giá của một khách sạn đơn lẻ đã được gán nhãn sẵn từ nền tảng Kaggle (bao gồm 26,521 mẫu tích cực và 12,411 mẫu tiêu cực). Sau bước lọc câu khách quan bằng Fuzzy C-means, hệ thống giữ lại 37,827 bài đánh giá có tính chủ quan cao để tiến hành huấn luyện.

## Evaluation
Hiệu năng phân loại của các thuật toán được đánh giá thực nghiệm dựa trên các chỉ số tiêu chuẩn của học máy: Độ chính xác tổng thể (Accuracy), Precision, Recall, và F-score.

## Results
- **Thuật toán đơn lẻ xuất sắc nhất:** Support Vector Machine (SVM) đạt kết quả vượt trội với Accuracy = 86.3%, Precision = 0.875, Recall = 0.938, và F-score = 0.859. Mô hình Logistic Regression bám sát phía sau với Accuracy = 85.9%.
- **Thuật toán thấp nhất:** Naïve Bayes có kết quả kém nhất với Accuracy = 71.8%.
- **Mô hình kết hợp (Ensemble):** Đạt Accuracy = 86.2%. Trong nghiên cứu này, mô hình Ensemble cho độ ổn định rất cao nhưng không vượt qua được thuật toán SVM đơn lẻ tốt nhất.

## Limitations
- Hệ thống chỉ thực hiện phân loại cảm xúc ở cấp độ toàn văn bản (Document-level Sentiment Polarity), chưa bóc tách sâu xuống cấp độ khía cạnh chi tiết (Aspect-Based Sentiment Analysis). Một bài đánh giá chứa các ý kiến hỗn hợp (ví dụ: khen phòng ngủ nhưng chê thái độ phục vụ) sẽ khiến mô hình gặp khó khăn khi gán nhãn tổng thể.
- Các thuật toán học máy truyền thống (SVM, KNN) kết hợp Word2Vec được công bố trong nghiên cứu (2021) hiện tại có phần cũ kỹ, chưa tận dụng sức mạnh của các mạng Transformer (BERT) hoặc các mô hình ngôn ngữ lớn (LLM) hiện đại.

## Relevance to our topic
- **Mức độ liên quan:** Trung bình.
- **Lý do:** Bài báo đóng vai trò làm tài liệu tham khảo nền tảng về mặt nghiệp vụ miền ứng dụng (Domain/Application Reference) cho module xử lý và phân tích phản hồi của khách hàng thuộc dự án **SmartStay AI**. 

## Possible improvement for our system
- **Áp dụng vào SmartStay AI:** Kế thừa quy trình xử lý ngôn ngữ tự nhiên (NLP Pipeline) được mô tả trong bài báo: chuẩn hóa từ viết tắt (Apostrophe lookup), tách từ (Tokenization), loại bỏ từ dừng (Stopwords), và xóa ký tự đặc biệt để làm sạch dữ liệu review thô thu thập từ khách hàng.
- **Nâng cấp giải pháp hệ thống:** Khắc phục triệt để giới hạn của bài báo. Thay vì sử dụng các thuật toán học máy truyền thống không thể bóc tách chi tiết, hệ thống SmartStay AI sẽ thiết lập cấu trúc Prompt chuyên sâu kết hợp với OpenAI API / Gemini API để thực hiện **Aspect-Based Sentiment Analysis**. Điều này giúp dashboard của quản lý khách sạn có thể chỉ ra chính xác tỷ lệ phân cực cảm xúc của khách theo từng khía cạnh như "Vệ sinh phòng", "Giá cả", hay "Thái độ nhân viên" như yêu cầu trong tài liệu SRS.