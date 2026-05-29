# Paper 06 Summary

## Citation

**Tên bài:** A Case Study Using Neural Networks Algorithms: Horse Racing Predictions in Jamaica  
**Tác giả:** Jannet Williams, Yan Li  
**Năm:** 2008  
**Nguồn:** Proceedings of the International Conference on Artificial Intelligence (ICAI 2008)  
**DOI/Link:** https://www.semanticscholar.org/paper/A-Case-Study-Using-Neural-Networks-Algorithms%3A-In-Williams-Li/f311a14dd57644579be3465824d0fff5a4e7ce15  

## Problem

Bài báo giải quyết bài toán dự đoán kết quả đua ngựa tại Jamaica bằng các thuật toán mạng nơ-ron. Đua ngựa có nhiều yếu tố ảnh hưởng như phong độ ngựa, năng lực nài ngựa, khoảng cách đua và điều kiện thi đấu, khiến việc dự đoán bằng cảm tính không ổn định. Nghiên cứu muốn kiểm tra xem các thuật toán neural network có thể hỗ trợ dự đoán kết quả hiệu quả hơn hay không.

## Method

Bài báo sử dụng các thuật toán mạng nơ-ron có giám sát. Theo phần tóm tắt, nghiên cứu so sánh các thuật toán như Backpropagation, Quasi-Newton và các biến thể neural network khác. Mục tiêu là huấn luyện mô hình dựa trên dữ liệu đua trong quá khứ để dự đoán kết quả cho các cuộc đua mới.

## Dataset

Nghiên cứu sử dụng dữ liệu đua ngựa tại Jamaica. Theo thông tin từ các nguồn học thuật, dữ liệu gồm khoảng **143 cuộc đua** trong giai đoạn từ tháng 1 đến tháng 6 năm 2007, với khoảng cách đua từ 1 đến 3 km. Dữ liệu gồm thông tin cuộc đua và kết quả thực tế.

## Evaluation

Bài báo đánh giá bằng **prediction accuracy**. Các thuật toán neural network được so sánh với nhau để xác định thuật toán nào cho kết quả tốt hơn trong bối cảnh dữ liệu Jamaica.

## Results

Kết quả cho thấy các thuật toán neural network có thể tạo ra dự đoán ở mức chấp nhận được. Một số nguồn tóm tắt cho biết độ chính xác khoảng 74%, trong đó Backpropagation có thể hoạt động tốt hơn nhẹ so với một số phương pháp khác. Điều này cho thấy neural network có tiềm năng trong dự đoán kết quả đua ngựa.

## Limitations

Bộ dữ liệu tương đối nhỏ và chỉ đến từ một khu vực cụ thể, vì vậy khả năng tổng quát hóa còn hạn chế. Neural network cần dữ liệu đủ lớn để hoạt động ổn định, nếu không dễ bị overfitting. Bài báo cũng chưa đề cập đến việc giải thích kết quả dự đoán cho người dùng cuối.

## Relevance to our topic

Bài báo liên quan cao vì cùng dùng AI để dự đoán kết quả đua ngựa. Nó cung cấp cơ sở tham khảo cho việc sử dụng các đặc trưng lịch sử và đánh giá mô hình bằng accuracy. Nhóm có thể dùng bài này để chứng minh rằng dự đoán đua ngựa bằng AI là hướng nghiên cứu có nền tảng.

## Possible improvement

Nhóm có thể mở rộng bằng cách dùng XGBoost, Random Forest hoặc mô hình ensemble thay cho neural network nếu dữ liệu không quá lớn. Ngoài ra, nhóm có thể bổ sung cơ chế hiển thị xác suất thắng và tích hợp vào hệ thống quản lý giải đua ngựa, thay vì chỉ làm nghiên cứu dự đoán độc lập.
