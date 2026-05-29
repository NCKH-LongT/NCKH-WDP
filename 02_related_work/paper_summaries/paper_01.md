# Paper 01 Summary

## Citation

**Tên bài:** Searching for Positive Returns at the Track: A Multinomial Logit Model for Handicapping Horse Races  
**Tác giả:** Ruth N. Bolton, Randall G. Chapman  
**Năm:** 1986  
**Nguồn:** Management Science  
**DOI/Link:** https://doi.org/10.1287/mnsc.32.8.1040

## Problem

Bài báo giải quyết bài toán dự đoán xác suất chiến thắng của từng con ngựa trong một cuộc đua. Trước đó, việc dự đoán kết quả đua ngựa thường dựa vào kinh nghiệm cá nhân, cảm tính hoặc các thống kê đơn giản. Điều này làm cho người phân tích khó đánh giá khách quan khả năng thắng của từng ngựa. Bài báo đặt ra vấn đề xây dựng một mô hình định lượng để khai thác dữ liệu trước cuộc đua và tìm kiếm cơ hội tạo lợi nhuận trong thị trường cá cược pari-mutuel.

## Method

Tác giả sử dụng **Multinomial Logit Model** để mô hình hóa quá trình lựa chọn người thắng trong cuộc đua. Mỗi ngựa được xem như một lựa chọn trong cùng một tập lựa chọn. Các đặc trưng của ngựa, nài ngựa và cuộc đua được đưa vào mô hình để tính điểm tiện ích cho từng ngựa. Sau đó mô hình chuyển các điểm này thành xác suất thắng tương ứng. Đây là một phương pháp thống kê phù hợp vì trong một cuộc đua chỉ có một ngựa chiến thắng và các đối thủ cạnh tranh trực tiếp với nhau.

## Dataset

Bài báo sử dụng cơ sở dữ liệu gồm khoảng **200 cuộc đua ngựa**. Dữ liệu bao gồm các thông tin trước cuộc đua như đặc điểm ngựa, thông tin nài ngựa, lịch sử thi đấu và kết quả thực tế. Bộ dữ liệu được dùng để ước lượng tham số mô hình và đánh giá khả năng dự đoán.

## Evaluation

Bài báo đánh giá mô hình bằng cách so sánh xác suất dự đoán với kết quả thực tế của cuộc đua. Ngoài ra, tác giả còn đánh giá khả năng tạo lợi nhuận khi sử dụng xác suất dự đoán trong chiến lược đặt cược. Các tiêu chí chính gồm độ chính xác dự đoán và hiệu quả lợi nhuận trong thị trường win-betting.

## Results

Kết quả cho thấy mô hình Multinomial Logit có thể dự đoán xác suất thắng của từng ngựa một cách có hệ thống. Mô hình giúp phát hiện sai lệch trong đánh giá của công chúng và có thể hỗ trợ chiến lược cá cược dựa trên dữ liệu. Bài báo chứng minh rằng dữ liệu lịch sử có giá trị thực tế trong việc dự đoán kết quả đua ngựa.

## Limitations

Mô hình vẫn là mô hình thống kê truyền thống, khó biểu diễn các quan hệ phi tuyến phức tạp giữa các đặc trưng. Bộ dữ liệu tương đối nhỏ so với tiêu chuẩn học máy hiện đại. Ngoài ra, bài báo tập trung vào cá cược hơn là tích hợp vào một hệ thống quản lý giải đấu hoàn chỉnh.

## Relevance to our topic

Bài báo liên quan trực tiếp đến đề tài của nhóm vì cùng giải quyết bài toán **dự đoán xác suất chiến thắng của ngựa**. Đây là nền tảng lý thuyết quan trọng cho module AI Prediction trong hệ thống quản lý giải đua ngựa. Ý tưởng chuyển dữ liệu lịch sử thành xác suất thắng có thể được áp dụng trực tiếp vào hệ thống của nhóm.

## Possible improvement

Nhóm có thể cải tiến bằng cách thay Multinomial Logit bằng các mô hình học máy hiện đại như **XGBoost** hoặc **Random Forest**. Ngoài ra, nhóm có thể bổ sung thêm các đặc trưng như phong độ gần đây, điểm xếp hạng, tỷ lệ thắng của nài ngựa, số lần thi đấu và tổng tiền thưởng. Điểm mới của nhóm là tích hợp mô hình dự đoán vào một hệ thống quản lý giải đua ngựa đầy đủ, không chỉ dừng lại ở nghiên cứu cá cược.
