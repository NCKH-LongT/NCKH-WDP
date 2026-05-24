# Paper 04 Summary

## Citation
- **Tên bài:** A Science Mapping Software Tool for Literature Analysis and Trend Visualization
- **Tác giả:** Chen, C.
- **Năm:** 2021
- **Nguồn:** Journal of Informetrics
- **DOI/Link:** https://doi.org/10.1016/j.joi.2021.101152

## Problem
Khi nghiên cứu một lĩnh vực mới, các nhà nghiên cứu thường bị lạc trong ma trận bài báo và rất khó nhìn ra mối liên hệ giữa các tác giả hoặc các từ khóa học thuật. Các công cụ hiện tại chủ yếu hiển thị danh sách bài báo dạng văn bản thuần túy, thiếu khả năng biểu diễn mối quan hệ mạng lưới (Network) giữa các thực thể.

## Method
Đề xuất phương pháp phân tích mạng lưới đồng trích dẫn (Co-citation Network Analysis) và kỹ thuật gom cụm mạng lưới (Network Clustering). Tác giả phát triển thuật toán tính toán độ tương đồng giữa các từ khóa và sử dụng các metric đồ thị (Modularity Q, Silhouette) để tối ưu hóa việc phân vùng các cụm nghiên cứu.

## Dataset
Sử dụng các file trích xuất metadata định dạng `.txt` hoặc `.csv` từ Web of Science và Scopus với số lượng từ 2,000 đến 5,000 bài báo theo chủ đề.

## Evaluation
- Modularity Q (độ chặt chẽ của các phân cụm trong mạng lưới).
- Mean Silhouette (độ thấu quang / độ chính xác của các cụm từ khóa).

## Results
Hệ thống tạo ra các bản đồ mạng lưới (Science Mapping) trực quan, giúp người dùng nhìn thấy rõ các "cụm đảo kiến thức" (Knowledge Domains) đang nổi lên hoặc đang thoái trào, từ đó phát hiện ra các khoảng trống nghiên cứu.

## Limitations
Đây là phần mềm chạy offline (Desktop Application). Người dùng phải tự lên mạng tải file dữ liệu về một cách thủ công để nạp vào hệ thống, không có tính năng tự động đồng bộ qua API (No Realtime / Live Data Pipeline) và giao diện phức tạp, đòi hỏi người dùng phải có kiến thức chuyên môn sâu.

## Relevance to our topic
Bài báo này định hướng cho tính năng "Display charts and dashboard statistics" và "Track publication trends by keyword or topic" của nhóm. Nó gợi ý cách thiết kế các biểu đồ quan hệ hoặc danh mục từ khóa thông minh.

## Possible improvement
Nhóm sẽ khắc phục nhược điểm của bài báo này bằng cách đưa toàn bộ trải nghiệm lên nền tảng Web gọn nhẹ. Thay vì bắt người dùng tải file thủ công, hệ thống theo dõi xu hướng xuất bản tạp chí khoa học sẽ tự động cào/đồng bộ dữ liệu định kỳ từ API bên thứ ba vào MongoDB. Giao diện cũng được tinh giản để phục vụ tốt cho cả đối tượng sinh viên (Dashboard cơ bản) thay vì chỉ dành cho các chuyên gia nghiên cứu sâu.