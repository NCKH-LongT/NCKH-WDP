# Paper 01 Summary

## Citation
- **Tên bài:** An Automated System for Tracking and Visualizing Scientific Publication Trends
- **Tác giả:** Wang, L. & Zhang, X.
- **Năm:** 2023
- **Nguồn:** IEEE Access
- **DOI/Link:** https://doi.org/10.1109/ACCESS.2023.3214567

## Problem
Bài báo giải quyết vấn đề quá tải thông tin học thuật. Các nhà nghiên cứu gặp khó khăn trong việc xác định hướng đi nào trong ngành Máy tính đang tăng trưởng và hướng đi nào đang bão hòa, do các công cụ hiện tại chỉ hỗ trợ tìm kiếm từ khóa tĩnh, không hiển thị được dòng thời gian động của chủ đề.

## Method
Xây dựng một kiến trúc hệ thống 3 lớp (Lớp thu thập dữ liệu - Lớp xử lý AI - Lớp hiển thị Dashboard). Hệ thống sử dụng mô hình chủ đề cổ điển LDA để trích xuất các cụm từ khóa từ abstract bài báo và vẽ biểu đồ đường (Line chart) để biểu diễn tốc độ tăng trưởng của từng cụm theo năm.

## Dataset
Sử dụng bộ dữ liệu metadata gồm 10,000 bài báo được cào tự động từ cổng IEEE Xplore thuộc phân mục "Computer Science" giai đoạn 2018-2022.

## Evaluation
- Định lượng: Sử dụng độ đo Coherence Score để đánh giá chất lượng phân cụm của thuật toán AI.
- Định tính: Khảo sát mức độ hài lòng của 50 giảng viên về tính trực quan của các đồ thị xu hướng (Dashboard).

## Results
Hệ thống nhận diện chính xác sự chuyển dịch xu hướng từ "Deep Learning truyền thống" sang "Transformer" và "Generative AI" qua các năm với độ chính xác phân cụm đạt Coherence Score = 0.68. Giao diện biểu đồ giúp giảm 45% thời gian tìm kiếm bài báo định hướng của nghiên cứu sinh.

## Limitations
Thuật toán LDA phụ thuộc nặng nề vào việc cấu hình trước số lượng chủ đề (K-parameters). Nếu cấu hình sai, các từ khóa sẽ bị gom nhầm cụm, dẫn đến dashboard hiển thị sai lệch xu hướng. Hệ thống chưa có cơ chế thông báo (Notification) tự động khi có bài báo mới thuộc xu hướng.

## Relevance to our topic
Bài báo này là nền tảng trực tiếp cho hệ thống theo dõi xu hướng xuất bản tạp chí khoa học. Nó cung cấp thiết kế luồng dữ liệu (Dataflow) từ khâu đọc metadata (Tiêu đề, abstract, từ khóa, năm) cho đến việc xuất ra các biểu đồ thống kê cho Dashboard người dùng.

## Possible improvement
Nhóm có thể cải tiến bằng cách thay thế thuật toán LDA lỗi thời bằng mô hình học sâu tiên tiến hơn (như BERTopic), đồng thời bổ sung tính năng cấu hình API dữ liệu động từ OpenAlex và hệ thống gửi thông báo (Notification) qua email/hệ thống cho người dùng khi chủ đề họ "follow" có xu hướng tăng trưởng đột biến.