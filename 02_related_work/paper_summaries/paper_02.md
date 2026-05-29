# Paper 02 Summary

## Citation

**Tên bài:** Still Searching for Positive Returns at the Track: Empirical Results from 2,000 Hong Kong Races  
**Tác giả:** Randall G. Chapman  
**Năm:** 2008  
**Nguồn:** Efficiency of Racetrack Betting Markets, World Scientific  
**DOI/Link:** https://doi.org/10.1142/9789812819192_0018  

## Problem

Bài báo tiếp tục nghiên cứu bài toán dự đoán kết quả đua ngựa và kiểm tra xem liệu mô hình dự đoán có thể tạo ra lợi nhuận trong thị trường cá cược hay không. Vấn đề chính là xác định liệu mô hình Multinomial Logit đã được đề xuất trước đó có còn hiệu quả khi áp dụng trên một thị trường khác, dữ liệu lớn hơn và nhiều yếu tố dự đoán phức tạp hơn hay không.

## Method

Bài báo mở rộng phương pháp **Multinomial Logit** của Bolton và Chapman. Tác giả sử dụng mô hình với khoảng **20 biến đầu vào** để dự đoán xác suất thắng của từng ngựa. Các biến này phản ánh nhiều yếu tố liên quan đến ngựa, nài ngựa, điều kiện cuộc đua và thông tin thị trường. Sau đó mô hình được dùng để tạo xác suất dự đoán và hỗ trợ chiến lược đặt cược đơn vị.

## Dataset

Bài báo sử dụng dữ liệu gồm **2,000 cuộc đua tại Hong Kong**. Đây là bộ dữ liệu lớn hơn đáng kể so với nghiên cứu gốc năm 1986. Dữ liệu bao gồm nhiều thông tin chi tiết về cuộc đua, ngựa, nài ngựa và kết quả thực tế.

## Evaluation

Tác giả đánh giá mô hình thông qua dự đoán trên holdout sample và khả năng tạo **positive returns** trong chiến lược cá cược win-betting. Việc đánh giá không chỉ dựa trên độ chính xác mà còn dựa trên hiệu quả thực tế khi áp dụng vào thị trường cá cược.

## Results

Kết quả cho thấy mô hình Multinomial Logit mở rộng có thể tạo ra kết quả dự đoán hữu ích trên dữ liệu Hong Kong. Bài báo cung cấp bằng chứng rằng mô hình dựa trên dữ liệu cơ bản có thể phát hiện cơ hội lợi nhuận trong một số trường hợp. Nghiên cứu cũng chứng minh rằng việc tăng số lượng biến và dùng dữ liệu lớn hơn giúp cải thiện khả năng dự đoán.

## Limitations

Dù sử dụng nhiều biến hơn, mô hình vẫn dựa trên giả định tuyến tính của Multinomial Logit. Nghiên cứu chủ yếu tập trung vào hiệu quả cá cược, chưa đề cập đến việc triển khai trong hệ thống quản lý giải đấu. Ngoài ra, mô hình có thể phụ thuộc mạnh vào đặc điểm của thị trường Hong Kong và khó áp dụng trực tiếp cho các thị trường khác nếu không hiệu chỉnh.

## Relevance to our topic

Bài báo liên quan cao đến đề tài vì cung cấp bằng chứng thực nghiệm trên bộ dữ liệu lớn về việc dự đoán xác suất thắng trong đua ngựa. Các biến đầu vào trong mô hình có thể gợi ý cho nhóm cách thiết kế feature engineering cho module AI. Nghiên cứu cũng giúp nhóm có cơ sở khi trình bày rằng dự đoán xác suất thắng là bài toán đã được nghiên cứu nghiêm túc.

## Possible improvement

Nhóm có thể cải tiến bằng cách dùng XGBoost để học các quan hệ phi tuyến giữa đặc trưng và kết quả. Nhóm cũng có thể chuyển mục tiêu từ tối ưu lợi nhuận cá cược sang hỗ trợ ra quyết định trong hệ thống quản lý giải đua ngựa. Ngoài ra, nhóm có thể thiết kế dashboard giải thích các yếu tố ảnh hưởng đến xác suất thắng để tăng tính minh bạch.
