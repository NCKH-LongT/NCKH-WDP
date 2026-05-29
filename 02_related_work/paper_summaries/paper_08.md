# Paper 08 Summary

## Citation

**Tên bài:** Optimal Model of Horse Racing Competition Decision Management Based on Association Rules and Neural Network  
**Tác giả:** Zhang S.  
**Năm:** 2022  
**Nguồn:** Scientific Programming  
**DOI/Link:** https://doi.org/10.1155/2022/4240244  

## Problem

Bài báo giải quyết vấn đề tối ưu hóa quản lý quyết định trong thi đấu đua ngựa. Trong bối cảnh đua ngựa, dữ liệu về cuộc đua, vận động viên, ngựa và kết quả có thể rất phức tạp. Các phương pháp truyền thống khó đáp ứng nhu cầu dự đoán và hỗ trợ quyết định. Vì vậy, bài báo đề xuất kết hợp data mining và neural network để xây dựng mô hình hỗ trợ quản lý quyết định.

## Method

Bài báo sử dụng **Association Rules** kết hợp với **Neural Network**. Association Rules được dùng để phát hiện các quan hệ tiềm ẩn giữa các yếu tố trong dữ liệu đua ngựa. Neural Network được dùng cho bài toán phân loại hoặc dự đoán dựa trên các mẫu đã học. Bài báo cũng đề cập đến việc xây dựng mô hình theo cấu trúc B/S để phục vụ quản lý quyết định.

## Dataset

Dữ liệu được mô tả là dữ liệu liên quan đến thi đấu đua ngựa, bao gồm các thông tin phục vụ phân tích và dự đoán. Bài báo tập trung vào cấu trúc mô hình và quy trình dự đoán hơn là công bố một bộ dữ liệu mở chi tiết. Dữ liệu có thể bao gồm hồ sơ cuộc đua, đặc điểm ngựa, thông tin thi đấu và kết quả.

## Evaluation

Mô hình được đánh giá thông qua hiệu quả dự đoán và khả năng hỗ trợ quyết định trong quản lý thi đấu. Các chỉ số có thể bao gồm accuracy, error rate hoặc mức cải thiện so với phương pháp truyền thống. Trọng tâm đánh giá là khả năng ứng dụng của association rules và neural network trong hệ thống quản lý.

## Results

Bài báo cho thấy association rules và neural network có thể hỗ trợ tốt cho bài toán dự đoán và ra quyết định trong đua ngựa. Việc kết hợp khai phá luật và học máy giúp mô hình khai thác được cả quan hệ dữ liệu và khả năng dự đoán phi tuyến. Đây là minh chứng cho tiềm năng ứng dụng AI trong quản lý thi đấu đua ngựa.

## Limitations

Một hạn chế là bài báo có thể khó tái lập nếu không có đầy đủ dataset và thông số huấn luyện. Neural network cũng có thể khó giải thích đối với người dùng quản lý. Ngoài ra, bài báo chưa tập trung sâu vào các chức năng hệ thống như ví điện tử, đăng ký giải đấu, trọng tài và cá cược ảo.

## Relevance to our topic

Bài báo liên quan rất gần với đề tài vì không chỉ nói về dự đoán kết quả mà còn đề cập đến **decision management** trong đua ngựa. Điều này phù hợp với hệ thống của nhóm, vốn bao gồm quản lý giải đấu, quản lý cuộc đua, trọng tài, kết quả và AI prediction. Đây là bài tốt để đưa vào phần domain application.

## Possible improvement

Nhóm có thể cải tiến bằng cách xây dựng hệ thống thực tế rõ ràng hơn với các vai trò người dùng cụ thể. Về AI, nhóm có thể dùng XGBoost để tăng khả năng giải thích thông qua feature importance. Nhóm cũng có thể kết hợp AI prediction với dashboard quản trị để hỗ trợ ban tổ chức ra quyết định.
