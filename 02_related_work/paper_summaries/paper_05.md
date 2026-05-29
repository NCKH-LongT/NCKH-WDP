# Paper 05 Summary

## Citation

**Tên bài:** Horse Racing Prediction Using Artificial Neural Networks  
**Tác giả:** Elnaz Davoodi, Ali Reza Khanteymoori  
**Năm:** 2010  
**Nguồn:** Recent Advances in Neural Networks, Fuzzy Systems & Evolutionary Computing / ACM listing  
**DOI/Link:** https://dl.acm.org/doi/10.5555/1863431.1863457  

## Problem

Bài báo nghiên cứu việc áp dụng mạng nơ-ron nhân tạo vào dự đoán kết quả đua ngựa. Vấn đề chính là kết quả đua ngựa chịu ảnh hưởng bởi nhiều yếu tố phức tạp và phi tuyến, khiến các mô hình thống kê truyền thống khó đạt độ chính xác cao. Tác giả muốn kiểm tra liệu Artificial Neural Networks có thể học được các mẫu phức tạp trong dữ liệu đua ngựa hay không.

## Method

Bài báo sử dụng nhiều thuật toán mạng nơ-ron có giám sát, bao gồm Back-Propagation, Back-Propagation with Momentum, Quasi-Newton và Levenberg-Marquardt. Mạng nơ-ron được huấn luyện để dự đoán kết quả hoặc thời gian hoàn thành của ngựa dựa trên các đặc trưng đầu vào. Việc so sánh nhiều thuật toán giúp đánh giá thuật toán nào phù hợp hơn với bài toán đua ngựa.

## Dataset

Theo phần mô tả có sẵn, nghiên cứu áp dụng trên dữ liệu tại **AQUEDUCT Race Track, USA**. Một số nguồn tóm tắt liên quan đề cập bộ dữ liệu khoảng 100 cuộc đua. Dữ liệu bao gồm thông tin về ngựa, cuộc đua và kết quả thực tế dùng để huấn luyện và kiểm thử mạng nơ-ron.

## Evaluation

Bài báo đánh giá mô hình bằng độ chính xác dự đoán và thời gian huấn luyện. Các thuật toán neural network khác nhau được so sánh để xem thuật toán nào cho kết quả tốt hơn trong bài toán dự đoán đua ngựa.

## Results

Kết quả cho thấy mạng nơ-ron nhân tạo có thể tạo ra dự đoán chấp nhận được cho bài toán đua ngựa. Các thuật toán phức tạp hơn có thể cải thiện độ chính xác nhưng thường cần thời gian huấn luyện lớn hơn. Nghiên cứu cho thấy AI có khả năng mô hình hóa các mối quan hệ phi tuyến trong dữ liệu đua ngựa.

## Limitations

Hạn chế chính là kích thước dữ liệu không lớn, dễ gây overfitting khi dùng neural network. Mô hình neural network cũng khó giải thích hơn so với các mô hình tuyến tính. Ngoài ra, bài báo không tập trung vào việc tích hợp mô hình vào hệ thống quản lý thực tế.

## Relevance to our topic

Bài báo liên quan trực tiếp vì chứng minh khả năng sử dụng AI để dự đoán đua ngựa. Nó hỗ trợ nhóm trong việc giải thích vì sao sử dụng Machine Learning thay vì quy tắc thủ công. Các đặc trưng và cách đánh giá trong bài có thể tham khảo cho module dự đoán xác suất thắng của nhóm.

## Possible improvement

Nhóm có thể sử dụng XGBoost thay vì neural network để dễ huấn luyện hơn trên dữ liệu vừa và nhỏ. XGBoost cũng dễ kết hợp với feature importance để giải thích kết quả cho người dùng. Ngoài ra, nhóm có thể triển khai API dự đoán để tích hợp trực tiếp với hệ thống Web/Mobile.
