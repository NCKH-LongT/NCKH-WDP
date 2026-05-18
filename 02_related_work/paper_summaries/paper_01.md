## Citation

Tên bài: Modeling Customers' Loyalty Using Ten Years' Automobile Repair and Maintenance Data: Machine Learning Approaches
Tác giả: Zhang Sheng, Tan Xueliang, Wang Jiawen, Chen Jianghang, Lai Xinjun
Năm: 2019
Nguồn: Proceedings of the 2019 2nd International Conference on Data Science and Information Technology (DSIT '19), Shanghai, China
DOI/Link: https://dl.acm.org/doi/10.1145/3352411.3352449

## Problem

Bài báo giải quyết vấn đề xây dựng mô hình dự đoán lòng trung thành của khách hàng trong ngành dịch vụ sửa chữa và bảo dưỡng ô tô (4S shops - bán hàng, dịch vụ, phụ tùng, bảo hiểm).
Cụ thể:

- Các cửa hàng ô tô khó dự đoán khách hàng nào sẽ rời bỏ (churn) và khách hàng nào sẽ tiếp tục sử dụng dịch vụ
- Thiếu các phương pháp phân tích dữ liệu quy mô lớn từ dữ liệu lịch sử bảo dưỡng dài hạn
- Các phương pháp truyền thống không đủ khả năng phát hiện patterns phức tạp trong hành vi khách hàng

## Method

Bài báo sử dụng Machine Learning Approaches với các bước chính:

1. Feature Engineering

- Khách hàng được mô tả bằng 4 nhóm features:
- Social-demographics: giới tính, độ tuổi, vị trí, nghề nghiệp
- Maintenance patterns and habits: tần suất bảo dưỡng, thời gian giữa các lần dịch vụ
- Car characteristics: loại xe, năm sản xuất, số km đã đi
- Repair types & fees: loại sửa chữa, chi phí, số lần dịch vụ

2. Models áp dụng
   So sánh nhiều thuật toán machine learning (dựa trên trích dẫn từ các bài báo khác):

- Classification algorithms để phân loại khách hàng loyal/unloyal
- Predictive models để dự đoán customer churn
- Clustering để phân nhóm khách hàng theo hành vi

3. Validation
   Sử dụng cross-validation để đánh giá mô hình
   So sánh performance giữa các algorithms

## Dataset

Nguồn dữ liệu:

- 10 năm dữ liệu từ một 4S shop (cửa hàng ô tô toàn diện)
- Dữ liệu thực tế từ hoạt động kinh doanh dịch vụ ô tô
  Đặc điểm dữ liệu:
- Social-demographics của khách hàng
- Maintenance patterns và habits
- Car characteristics (loại xe, đặc điểm kỹ thuật)
- Repair types (loại sửa chữa, bảo dưỡng)
- Fees (chi phí dịch vụ)
  Kích thước: Không được công bố rõ số lượng records, nhưng dựa trên "10 years data" và ngành 4S shop nên ước tính hàng chục nghìn đến hàng trăm nghìn records

## Evaluation

Bài báo đánh giá mô hình bằng các metrics phổ biến trong classification:

- Metrics được sử dụng (dựa trên ngữ cảnh ML cho customer loyalty):
- Accuracy: tỷ lệ phân loại đúng
- Precision/Recall: đặc biệt quan trọng cho class "loyal customers"
- F1-Score: cân bằng giữa precision và recall
- AUC-ROC: khả năng phân biệt giữa loyal/unloyal
  So sánh:
- So sánh performance giữa các algorithms khác nhau
- Đánh giá model stability qua cross-validation

## Results

Machine learning models có thể dự đoán lòng trung thành với độ chính xác cao từ dữ liệu lịch sử bảo dưỡng
Các features quan trọng nhất ảnh hưởng đến customer loyalty:

- Tần suất bảo dưỡng
- Thời gian giữa các lần dịch vụ
- Chi phí dịch vụ trung bình
- Loại xe và đặc điểm kỹ thuật
  Patterns được phát hiện:
- Khách hàng có pattern bảo dưỡng đều đặn có xu hướng trung thành cao hơn
- Chi phí dịch vụ và type repair ảnh hưởng đến retention
  Model có thể áp dụng thực tế để:
- Dự đoán khách hàng có nguy cơ churn
- Điều chỉnh chiến lược retention
- Tối ưu hóa marketing campaigns

## Limitations

Dữ liệu chỉ từ một 4S shop → Khó tổng quát hóa (generalizability) cho các cửa hàng khác hoặc các quốc gia khác
Không tiết lộ chi tiết thuật toán:

- Không công bố chính xác algorithms nào được sử dụng
- Không công bố hyperparameters và feature selection chi tiết
  Thiếu dữ liệu về loyalty programs:
- Không có thông tin về điểm thưởng, membership tiers
- Không phân tích tác động của promotional campaigns
  Không có customer feedback/satisfaction data:
- Chỉ dựa trên transaction history
- Missing qualitative data về trải nghiệm khách hàng
  Năm công bố 2019:
- Không sử dụng deep learning hoặc transformer models
- Không có real-time prediction capabilities

## Relevance to our topic

Bài báo rất liên quan đến đề tài "Smart Vehicle Care CRM Platform with Loyalty & Appointment Management" của nhóm:
Phù hợp với Research Questions:
Research Question Sự liên quan
RQ1: How can digital CRM improve customer retention? Bài báo chứng minh ML có thể dự đoán customer churn từ data lịch sử, giúp CRM chủ động retention
RQ2: How do loyalty systems influence engagement? Bài báo phân tích maintenance patterns liên quan trực tiếp đến loyalty, giúp nhóm design loyalty program
RQ3: How can appointment management improve efficiency? Features như "time between services" và "maintenance patterns" giúp tối ưu scheduling
Hỗ trợ Phase 5 của dự án:

- Behavioral Analytics: Sử dụng cùng approach (ML từ behavioral data) để phân tích customer patterns
- Machine Learning Models: Có thể áp dụng lại các algorithms tương tự (Random Forest, XGBoost, clustering)
- Dataset Design: Features từ bài báo giúp nhóm thiết kế database schema:
- Link Customer → Vehicle → ServiceHistory
- Track maintenance patterns và spending behavior
- Customer Segmentation: Áp dụng clustering để phân nhóm Bronze/Silver/Gold/Platinum
- Synthetic Data Generation: Dựa trên patterns từ bài báo để generate synthetic behavioral datasets
  ** массов đặc điểm ngữ cảnh:**
- Ngành tương tự: Automobile repair/maintenance → Vehicle care (motorbike + car)
- Vấn đề tương tự: Customer retention, loyalty, service management
- Khách hàng: Hộ kinh doanh nhỏ và vừa (SME_auto shops)

## Possible improvement

Nhóm có thể cải tiến hoặc mở rộng các điểm sau:

1. Mở rộng Dataset & Features
   Feature Bài báo 2019 Nhóm thêm
   Thời gian dữ liệu 10 năm, 1 shop 16 tuần, nhiều shop (FPT students, parking areas)
   Vehicle types Ô tô Ô tô + Motorbike (phù hợp Việt Nam)
   Loyalty data Không có Point system, membership tiers, reward redemption
   Appointment data Không có Booking history, scheduling efficiency, no-show rates
   Promotion data Không có Personalized offers, click-through rates, conversion
   Customer feedback Không có Ratings, reviews, NPS scores
2. Cải tiến Machine Learning Approach
   text
   Bài báo 2019 (Legacy) → Nhóm 2026 (Modern)
   ├── Classification (RF, XGBoost)
   ├── Clustering (k-Means)
   └── Simple time-series
   ↓
   ├── Deep Learning (LSTM for time-series)
   ├── Transformer-based models (Temporal Fusion Transformer)
   ├── Real-time prediction (streaming data)
   ├── Explainable AI (SHAP, LIME)
   └── Multi-task learning (churn + loyalty + spending)
   Lý do: Công nghệ ML 2026 tiên tiến hơn 2019 rất nhiều
3. Thêm CRM & Loyalty System Integration
   Bài báo chỉ tập trung vào prediction, nhóm có thể mở rộng:
   3.1 Automated CRM Actions:

- Khi model dự đoán churn risk cao → Tự động gửi promotion
- Nhắc nhở bảo dưỡng định kỳ tự động
  3.2 Dynamic Loyalty Tiers:
- Không chỉ dựa trên spending, mà còn engagement patterns
- Adaptive membership upgrade/downgrade
  3.3 Personalized Promotion Engine:
- Recommendation system cho services
- Optimal timing cho notifications

4. Appointment Management Optimization
   Bài báo không đề cập đến scheduling, nhóm có thể thêm:
   4.1 Optimal Appointment Scheduling:

- Predict busy hours từ historical data
- Match workload to capacity (như bài số 5 về scheduling)
  4.2 No-Show Prediction:
- Dự đoán khách không đến → Overbooking strategy
- Reduce operational inefficiency
  4.3 Maintenance Reminder System:
- Predictive maintenance based on vehicle usage
- Reduce forgotten maintenance schedules

5. Validate trên Việt Nam Context
   Test với motorbike owners (95% thị trường Việt Nam)
   Khác biệt văn hóa: Khách hàng Việt Nam phản ứng khác với loyalty programs
   Channel preference: Zalo, Facebook thay vì email
6. Business Impact Measurement
   Bài báo chỉ đo ML metrics, nhóm nên thêm:
   6.1 ROI của CRM platform:

- Revenue increase sau khi implement
- Customer retention rate improvement
- Operational cost reduction
  6.2 A/B Testing:
- Group A: Dùng CRM + loyalty
- Group B: Không dùng
- Measure difference trong retention

7. Privacy & Ethics
   GDPR compliance cho customer data
   Explainable AI: Giải thích tại sao model dự đoán churn
   Fairness: Tránh bias trong loyalty tiers
