# Paper 04 Summary

## Citation

**Tên bài:** Horse Racing Prediction at the Champ De Mars using a Weighted Probabilistic Approach  
**Tác giả:** Sameerchand Pudaruth, N. Medard, Z. B. Dookhun  
**Năm:** 2013  
**Nguồn:** International Journal of Computer Applications  
**DOI/Link:** https://ijcaonline.org/archives/volume72/number5/12493-9048/  

## Problem

Bài báo giải quyết bài toán dự đoán ngựa chiến thắng tại trường đua Champ De Mars ở Mauritius. Tác giả nhận thấy nhiều người chơi thường dựa vào lời khuyên từ báo chí, truyền hình hoặc cảm tính, nhưng các nguồn này không đủ chính xác. Do đó, bài báo hướng đến việc xây dựng một phương pháp dự đoán có hệ thống dựa trên các yếu tố ảnh hưởng đến kết quả cuộc đua.

## Method

Bài báo sử dụng **Weighted Probabilistic Approach**. Mỗi yếu tố ảnh hưởng đến kết quả cuộc đua được gán trọng số, sau đó tổng hợp các trọng số để đưa ra dự đoán. Các yếu tố có thể bao gồm phong độ của ngựa, năng lực nài ngựa, thành tích trước đây, sự yêu thích của thị trường và các yếu tố đặc thù của cuộc đua. Cách tiếp cận này dễ hiểu và phù hợp với bài toán khi dữ liệu không quá lớn.

## Dataset

Nghiên cứu sử dụng dữ liệu của mùa giải đua ngựa năm 2010 tại Champ De Mars. Theo mô tả của nguồn IJCA, kết quả của **240 cuộc đua** được sử dụng để xác định mức độ ảnh hưởng của từng yếu tố đến khả năng chiến thắng của ngựa.

## Evaluation

Bài báo đánh giá bằng tỷ lệ dự đoán đúng người thắng. Theo trang tóm tắt của IJCA, hệ thống đạt khoảng **58% accuracy**, tương đương trung bình 4.7 trên 8 người thắng được dự đoán đúng, và vượt qua các tipster chuyên nghiệp tại Mauritius trong so sánh được nêu.

## Results

Kết quả cho thấy phương pháp trọng số xác suất có thể đưa ra dự đoán tốt hơn so với một số nguồn dự đoán truyền thống. Bài báo chứng minh rằng việc lựa chọn và gán trọng số cho các yếu tố liên quan đến ngựa và cuộc đua có thể hỗ trợ dự đoán kết quả một cách thực tế.

## Limitations

Phương pháp phụ thuộc nhiều vào cách gán trọng số thủ công. Nếu trọng số không phù hợp, mô hình dễ bị sai lệch. Ngoài ra, mô hình không tự học phức tạp như các thuật toán Machine Learning hiện đại. Kết quả cũng có thể chỉ phù hợp với trường đua Champ De Mars và mùa giải được nghiên cứu.

## Relevance to our topic

Bài báo liên quan trực tiếp đến đề tài vì cũng dự đoán kết quả đua ngựa dựa trên nhiều đặc trưng. Các yếu tố như phong độ ngựa, năng lực nài ngựa và lịch sử thi đấu có thể được dùng làm feature cho hệ thống AI của nhóm. Bài báo cũng giúp nhóm có ví dụ cụ thể về cách đánh giá mô hình bằng accuracy.

## Possible improvement

Nhóm có thể cải tiến bằng cách thay phương pháp gán trọng số thủ công bằng XGBoost để mô hình tự học tầm quan trọng của từng đặc trưng. Ngoài ra, nhóm có thể hiển thị xác suất thắng thay vì chỉ dự đoán một ngựa thắng, giúp người dùng hiểu rõ mức độ tự tin của mô hình.
