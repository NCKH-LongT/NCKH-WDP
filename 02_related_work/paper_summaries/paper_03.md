## Citation

Tên bài: Modeling Customers' Loyalty Using Ten Years' Automobile Repair and Maintenance Data: Machine Learning Approaches
Tác giả: Zhang Sheng, Tan Xueliang, Wang Jiawen, Chen Jianghang, Lai Xinjun
Năm: 2019
Nguồn: Proceedings of the 2019 2nd International Conference on Data Science and Information Technology (DSIT '19), Shanghai, China
DOI/Link: https://dl.acm.org/doi/10.1145/3352411.3352449

## Problem

Bài báo giải quyết bài toán dự đoán lòng trung thành của khách hàng trong ngành dịch vụ sửa chữa và bảo dưỡng ô tô (4S shops).
Cụ thể:

- Các cửa hàng ô tô khó dự đoán khách hàng nào sẽ rời bỏ (churn) và khách hàng nào sẽ tiếp tục sử dụng dịch vụ.
- Thiếu phương pháp phân tích dữ liệu quy mô lớn từ lịch sử bảo dưỡng dài hạn.
- Các phương pháp truyền thống không đủ khả năng phát hiện các patterns phức tạp trong hành vi khách hàng.

## Method

Bài báo sử dụng phương pháp machine learning với các bước chính:

1. Feature Engineering

- Mô tả khách hàng bằng 4 nhóm đặc trưng:
  - Social-demographics: giới tính, độ tuổi, vị trí, nghề nghiệp
  - Maintenance patterns and habits: tần suất bảo dưỡng, thời gian giữa các lần dịch vụ
  - Car characteristics: loại xe, năm sản xuất, số km đã đi
  - Repair types & fees: loại sửa chữa, chi phí, số lần dịch vụ

2. Models áp dụng

- Classification algorithms để phân loại khách hàng loyal/unloyal.
- Predictive models để dự đoán customer churn.
- Clustering để phân nhóm khách hàng theo hành vi.

3. Validation

- Sử dụng cross-validation để đánh giá mô hình.
- So sánh performance giữa các thuật toán khác nhau.

## Dataset

Nguồn dữ liệu:

- 10 năm dữ liệu từ một 4S shop (cửa hàng ô tô toàn diện).
- Dữ liệu thực tế từ hoạt động kinh doanh dịch vụ ô tô.

Đặc điểm dữ liệu:

- Social-demographics của khách hàng.
- Maintenance patterns và habits.
- Car characteristics (loại xe, đặc điểm kỹ thuật).
- Repair types (loại sửa chữa, bảo dưỡng).
- Fees (chi phí dịch vụ).

Kích thước: không được công bố rõ số lượng records, nhưng dựa trên "10 years data" và ngành 4S shop nên ước tính hàng chục nghìn đến hàng trăm nghìn records.

## Evaluation

Bài báo đánh giá mô hình bằng các metrics phổ biến trong classification:

- Accuracy: tỷ lệ phân loại đúng.
- Precision / Recall: đặc biệt quan trọng cho class "loyal customers".
- F1-Score: cân bằng giữa precision và recall.
- AUC-ROC: khả năng phân biệt giữa loyal và unloyal.

So sánh đánh giá:

- So sánh performance giữa các thuật toán khác nhau.
- Đánh giá sự ổn định của model qua cross-validation.

## Results

1. Machine learning models có thể dự đoán lòng trung thành với độ chính xác cao từ dữ liệu lịch sử bảo dưỡng.
2. Các features quan trọng nhất ảnh hưởng đến customer loyalty:

- Tần suất bảo dưỡng.
- Thời gian giữa các lần dịch vụ.
- Chi phí dịch vụ trung bình.
- Loại xe và đặc điểm kỹ thuật.

3. Patterns được phát hiện:

- Khách hàng có pattern bảo dưỡng đều đặn có xu hướng trung thành cao hơn.
- Chi phí dịch vụ và loại sửa chữa ảnh hưởng đến retention.

4. Ứng dụng thực tế:

- Dự đoán khách hàng có nguy cơ churn.
- Điều chỉnh chiến lược retention.
- Tối ưu hóa marketing campaigns.

## Limitations

- Dữ liệu chỉ từ một 4S shop → khó tổng quát hóa cho các cửa hàng khác hoặc các quốc gia khác.
- Không tiết lộ chi tiết thuật toán: không công bố chính xác algorithms, hyperparameters và feature selection chi tiết.
- Thiếu dữ liệu về loyalty programs: không có thông tin về điểm thưởng, membership tiers và tác động của promotional campaigns.
- Không có customer feedback / satisfaction data: chỉ dựa trên transaction history, thiếu qualitative data về trải nghiệm khách hàng.
- Khung thời gian 2019: không sử dụng deep learning hiện đại hoặc transformer models, không có real-time prediction capabilities.

## Relevance to our topic

Bài báo rất liên quan đến đề tài "Smart Vehicle Care CRM Platform with Loyalty & Appointment Management" của nhóm.

Sự liên quan với Research Questions:

- RQ1: How can digital CRM improve customer retention?
  - Bài báo chứng minh ML có thể dự đoán customer churn từ dữ liệu lịch sử, giúp CRM chủ động retention.
- RQ2: How do loyalty systems influence engagement?
  - Bài báo phân tích maintenance patterns liên quan trực tiếp đến loyalty, hỗ trợ thiết kế loyalty program.
- RQ3: How can appointment management improve efficiency?
  - Các features như "time between services" và "maintenance patterns" giúp tối ưu scheduling.

Hỗ trợ Phase 5 của dự án:

- Behavioral Analytics: dùng cách tiếp cận ML từ behavioral data để phân tích patterns khách hàng.
- Machine Learning Models: có thể áp dụng các thuật toán tương tự như Random Forest, XGBoost, clustering.
- Dataset Design: features từ bài báo giúp nhóm thiết kế database schema:
  - Link Customer → Vehicle → ServiceHistory.
  - Track maintenance patterns và spending behavior.
- Customer Segmentation: áp dụng clustering để phân nhóm Bronze / Silver / Gold / Platinum.
- Synthetic Data Generation: dựa trên patterns từ bài báo để tạo dữ liệu synthetic behavioral.

Đặc điểm ngữ cảnh tương tự:

- Ngành: Automobile repair/maintenance → Vehicle care (ô tô + xe máy).
- Vấn đề: Customer retention, loyalty, service management.
- Khách hàng: hộ kinh doanh nhỏ và vừa (SME auto shops).

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng các điểm sau:

1. Mở rộng Dataset & Features

- Thời gian dữ liệu: 10 năm, 1 shop → 16 tuần, nhiều shop (FPT students, parking areas).
- Vehicle types: ô tô → ô tô + xe máy (phù hợp Việt Nam).
- Loyalty data: không có → point system, membership tiers, reward redemption.
- Appointment data: không có → booking history, scheduling efficiency, no-show rates.
- Promotion data: không có → personalized offers, click-through rates, conversion.
- Customer feedback: không có → ratings, reviews, NPS scores.

2. Cải tiến Machine Learning Approach
   Bài báo 2019 (legacy) → nhóm 2026 (modern):

- Classification (RF, XGBoost) → Deep Learning (LSTM cho time-series).
- Clustering (k-Means) → Transformer-based models (Temporal Fusion Transformer).
- Simple time-series → Real-time prediction (streaming data).
- Thêm Explainable AI (SHAP, LIME).
- Multi-task learning (churn + loyalty + spending).

3. Thêm CRM & Loyalty System Integration
   Bài báo chỉ tập trung vào prediction; nhóm có thể mở rộng:

- Automated CRM Actions: khi model dự đoán churn risk cao → tự động gửi promotion và nhắc nhở bảo dưỡng định kỳ.
- Dynamic Loyalty Tiers: không chỉ dựa trên spending mà còn engagement patterns, adaptive membership upgrade/downgrade.
- Personalized Promotion Engine: recommendation system cho services, optimal timing cho notifications.

4. Appointment Management Optimization
   Bài báo không đề cập đến scheduling; nhóm có thể thêm:

- Optimal Appointment Scheduling: dự đoán giờ cao điểm từ historical data và cân bằng workload với capacity.
- No-Show Prediction: dự đoán khách không đến → áp dụng chiến lược overbooking để giảm inefficiency.
- Maintenance Reminder System: predictive maintenance dựa trên vehicle usage, giảm quên lịch bảo dưỡng.

5. Validate trên Việt Nam Context

- Thử nghiệm với owner xe máy (95% thị trường Việt Nam).
- Khác biệt văn hóa: khách hàng Việt Nam phản ứng khác với loyalty programs.
- Channel preference: Zalo, Facebook thay vì email.

6. Business Impact Measurement
   Bài báo chỉ đo metrics ML; nhóm nên thêm:

- ROI của CRM platform: revenue increase, customer retention rate improvement, operational cost reduction.
- A/B Testing: Group A dùng CRM + loyalty, Group B không dùng, đo sự khác biệt trong retention.

7. Privacy & Ethics

- GDPR compliance cho customer data.
- Explainable AI: giải thích tại sao model dự đoán churn.
- Fairness: tránh bias trong loyalty tiers.
