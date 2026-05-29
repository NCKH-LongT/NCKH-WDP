# Paper 07 Summary

## Citation

**Tên bài:** Horse Racing Prediction Using Graph-Based Features  
**Tác giả:** Mehmet Akif Gulum  
**Năm:** 2018  
**Nguồn:** University of Louisville Master Thesis  
**DOI/Link:** https://ir.library.louisville.edu/etd/2953/  

## Problem

Bài nghiên cứu giải quyết bài toán dự đoán kết quả đua ngựa bằng cách khai thác quan hệ giữa các thực thể trong dữ liệu. Các phương pháp truyền thống thường chỉ dùng đặc trưng dạng bảng như tỷ lệ thắng, tuổi, cân nặng hoặc thành tích gần đây. Tuy nhiên, trong đua ngựa còn tồn tại nhiều mối quan hệ như ngựa từng gặp nhau, ngựa cùng tham gia giải, hoặc mối liên hệ giữa nài ngựa và ngựa. Bài nghiên cứu đặt vấn đề sử dụng graph-based features để cải thiện dự đoán.

## Method

Nghiên cứu xây dựng các đặc trưng dựa trên đồ thị, sau đó sử dụng **Artificial Neural Network** và **Logistic Regression** để huấn luyện và kiểm thử. Mô hình được so sánh giữa hai trường hợp: dùng đặc trưng thông thường và dùng thêm đặc trưng đồ thị. Cách tiếp cận này nhấn mạnh vai trò của feature engineering trong bài toán dự đoán đua ngựa.

## Dataset

Dữ liệu được thu thập từ một website đua ngựa trong giai đoạn **2015 đến 2017**. Bộ dữ liệu bao gồm thông tin cuộc đua, ngựa, kết quả và các quan hệ có thể chuyển thành đặc trưng đồ thị. Dữ liệu được xử lý để tạo tập huấn luyện và tập kiểm thử.

## Evaluation

Nghiên cứu đánh giá bằng cách so sánh hiệu quả của mô hình khi có và không có graph-based features. Các metric chính liên quan đến hiệu suất dự đoán phân loại, chẳng hạn accuracy hoặc các chỉ số đánh giá phân loại tương đương.

## Results

Kết quả cho thấy việc thêm graph-based features có thể cung cấp thông tin bổ sung cho mô hình dự đoán. Nghiên cứu nhấn mạnh rằng không chỉ dữ liệu cá nhân của ngựa mà cả quan hệ giữa các đối tượng trong hệ thống cũng có thể ảnh hưởng đến dự đoán. Đây là một hướng feature engineering có giá trị trong horse racing analytics.

## Limitations

Đây là luận văn thạc sĩ, phạm vi thực nghiệm có thể hẹp hơn so với các bài báo journal lớn. Việc xây dựng graph-based features phức tạp hơn so với feature dạng bảng. Ngoài ra, nếu hệ thống của nhóm chưa có nhiều dữ liệu quan hệ lịch sử, việc áp dụng graph features có thể khó trong giai đoạn đầu.

## Relevance to our topic

Bài nghiên cứu liên quan trực tiếp đến đề tài vì nhóm cũng cần xây dựng đặc trưng từ lịch sử thi đấu của ngựa, nài ngựa và cuộc đua. Ý tưởng graph-based features có thể giúp nhóm phát triển hệ thống AI nâng cao trong tương lai. Bài này cũng cho thấy feature engineering là yếu tố quan trọng, không chỉ chọn model.

## Possible improvement

Trong giai đoạn đầu, nhóm có thể dùng các đặc trưng đơn giản như win rate, recent form, average finish position và jockey win rate. Sau đó, nếu có đủ dữ liệu, nhóm có thể mở rộng bằng graph-based features để biểu diễn quan hệ giữa ngựa, nài ngựa, giải đấu và đối thủ từng gặp.
