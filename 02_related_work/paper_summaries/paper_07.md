# Tóm tắt Bài báo 07

## Trích dẫn

Viola, L., Ronchieri, E., & Cavallaro, C. (2022). *Combining Log Files and Monitoring Data to Detect Anomaly Patterns in a Data Center*. *Computers, 11*(8), 117. https://doi.org/10.3390/computers11080117

## Vấn đề nghiên cứu

Nhiều cách tiếp cận phát hiện bất thường trong trung tâm dữ liệu chỉ phân tích riêng lẻ log dịch vụ hoặc dữ liệu giám sát hạ tầng. Sự tách biệt này làm giảm khả năng nhận diện các tín hiệu giao thoa có ý nghĩa giữa sự cố ở mức dịch vụ và hành vi ở mức máy chủ.

## Phương pháp

Nhóm tác giả đề xuất một cách tiếp cận lai tích hợp `log analysis` và `monitoring data`. Họ xây dựng từ điển cho từng tệp log, trích xuất các `n-grams` bất thường, làm giàu phân tích bằng các kỹ thuật `NLP` như word cloud và topic modeling, sau đó áp dụng phân cụm để nhóm các loại bất thường. Song song với đó, phát hiện bất thường chuỗi thời gian được áp dụng trên các luồng cảm biến và giám sát; cuối cùng, hai góc nhìn này được liên kết ở cấp máy chủ và cấp dịch vụ.

## Dữ liệu

Nghiên cứu được tiến hành trên một trung tâm dữ liệu sản xuất thực. Dữ liệu do `National Institute for Nuclear Physics (INFN)` tại Ý cung cấp, bao gồm cả tệp log lẫn dữ liệu giám sát mô tả các tài nguyên vật lý và ảo.

## Đánh giá

Đánh giá xem xét liệu các bất thường được phát hiện trong log có tương ứng với các bất thường quan sát được trong các chỉ số giám sát hay không. Nhờ vậy, nhóm tác giả có thể kiểm định liệu việc kết hợp cả hai nguồn dữ liệu có cải thiện khả năng diễn giải và giá trị vận hành hay không.

## Kết quả

Bài báo báo cáo các kết quả đầy hứa hẹn từ việc tích hợp log và dữ liệu giám sát. Nghiên cứu ghi nhận sự tương ứng có ý nghĩa giữa bất thường trong log với các tín hiệu hạ tầng như suy giảm bộ nhớ hoặc gia tăng tải máy, qua đó gợi ý rằng phân tích bất thường đa phương thức có thể phản ánh tốt hơn các sự kiện vận hành thực tế.

## Hạn chế

Cách tiếp cận này phụ thuộc vào tri thức miền từ quản trị viên hệ thống để diễn giải chính xác các kịch bản quan trọng. Nó cũng thiên về khám phá mẫu và tương quan bất thường hơn là mô hình hóa dự báo hoặc trình bày thông tin qua AR.

## Mức độ liên quan tới đề tài của nhóm

Bài báo có mức độ liên quan cao tới kiến trúc mà nhóm đề xuất vì nhóm cũng dự định kết hợp telemetry, log và ngữ cảnh vận hành. Công trình này củng cố lập luận rằng khả năng quan sát hạ tầng có hỗ trợ AI không nên dựa trên một nguồn tín hiệu duy nhất.

## Hướng cải tiến khả dĩ

Đối với dự án của nhóm, có thể đơn giản hóa ý tưởng lai này thành một proof-of-concept bằng cách tương quan log container, trạng thái dịch vụ và các chỉ số mức node. Sau đó, ngữ cảnh bất thường đã hợp nhất có thể được hiển thị không chỉ trên dashboard mà còn thông qua lớp phủ AR trên các node mô phỏng tương ứng.
