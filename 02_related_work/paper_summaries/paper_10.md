# Paper 10 Summary

## Citation

**Tên bài:** Horse Race Results Prediction Using Machine Learning Algorithms With Feature Selection  
**Tác giả:** Meenakshi Gupta, Latika Singh  
**Năm:** 2023  
**Nguồn:** International Journal of Intelligent Systems and Applications in Engineering  
**DOI/Link:** https://ijisae.org/index.php/IJISAE/article/view/3565  

## Problem

Bài báo giải quyết bài toán dự đoán kết quả đua ngựa bằng nhiều thuật toán Machine Learning. Kết quả đua ngựa phụ thuộc vào nhiều yếu tố khác nhau, nên việc chọn đúng đặc trưng và mô hình phù hợp là rất quan trọng. Bài báo tập trung vào việc so sánh nhiều thuật toán học máy và áp dụng feature selection để cải thiện hiệu quả dự đoán.

## Method

Bài báo sử dụng nhiều mô hình Machine Learning như **K-Nearest Neighbors**, **Linear Regression**, **Random Forest**, **Gaussian Naive Bayes**, **AdaBoost** và **Bagging**. Ngoài ra, bài báo áp dụng các kỹ thuật feature selection như Information Gain và Chi-square filtering để chọn ra các thuộc tính quan trọng nhất. Cách tiếp cận này giúp giảm nhiễu và cải thiện chất lượng mô hình.

## Dataset

Theo phần mô tả của bài, dataset liên quan đến dữ liệu đua ngựa với nhiều thuộc tính như kết quả thi đấu trước đó, thống kê ngựa, thống kê người tham gia và thông tin cuộc đua. Một số nguồn mô tả dataset có hàng nghìn dòng và nhiều thuộc tính, phục vụ cho việc so sánh các thuật toán Machine Learning.

## Evaluation

Bài báo đánh giá các mô hình bằng các chỉ số phân loại như accuracy và các metric liên quan đến hiệu quả dự đoán. Việc so sánh nhiều thuật toán giúp xác định mô hình nào phù hợp hơn với dữ liệu đua ngựa khi có hoặc không có feature selection.

## Results

Kết quả cho thấy Machine Learning có thể được sử dụng để dự đoán kết quả đua ngựa, và feature selection có vai trò quan trọng trong việc cải thiện mô hình. Các mô hình ensemble như Random Forest, AdaBoost hoặc Bagging thường có lợi thế vì có thể xử lý nhiều đặc trưng và quan hệ phức tạp trong dữ liệu.

## Limitations

Bài báo tập trung vào so sánh thuật toán, nhưng chưa đi sâu vào việc tích hợp mô hình vào một hệ thống quản lý giải đấu hoàn chỉnh. Ngoài ra, khả năng giải thích của một số mô hình ensemble có thể khó đối với người dùng phổ thông. Dataset cũng cần được chuẩn hóa nếu áp dụng cho bối cảnh giải đua khác.

## Relevance to our topic

Bài báo rất liên quan vì đề tài của nhóm cũng dự kiến dùng Machine Learning để dự đoán xác suất chiến thắng. Các thuật toán trong bài có thể dùng làm baseline để so sánh với XGBoost. Phần feature selection cũng giúp nhóm xác định những thuộc tính quan trọng như phong độ ngựa, thành tích nài ngựa, số lần tham gia và lịch sử kết quả.

## Possible improvement

Nhóm có thể dùng XGBoost làm mô hình chính và so sánh với Random Forest hoặc Logistic Regression như baseline. Ngoài ra, nhóm có thể không chỉ dự đoán nhãn thắng/thua mà còn chuẩn hóa thành xác suất chiến thắng của từng ngựa trong cuộc đua. Điểm cải tiến quan trọng là tích hợp kết quả dự đoán vào hệ thống Web/Mobile, dashboard và module cá cược ảo.
