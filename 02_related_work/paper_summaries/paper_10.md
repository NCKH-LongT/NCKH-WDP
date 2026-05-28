# Citation

- **Title:** Computer Aided Management System of Sports Horse Registration Based on Distributed Storage System and Deep Fusion Learning
- **Authors:** Shuang Zhang, Mairu Liu
- **Year:** 2021
- **Source:** Microprocessors and Microsystems
- **DOI/Link:** Computer Aided Management System of Sports Horse Registration Based on Distributed Storage System and Deep Fusion Learning

# Problem

Bài báo tập trung giải quyết các vấn đề tồn tại trong hệ thống quản lý thông tin thể thao truyền thống:

- Quản lý thủ công kém hiệu quả: Ban quản lý và huấn luyện viên thường phải kiểm tra thông tin vận động viên dựa trên các báo cáo và dữ liệu ghi chép thủ công.
- Thiếu khả năng phân tích chuyên sâu: Chưa có sự khai thác và ứng dụng tốt dữ liệu của vận động viên để nâng cao năng lực cho cá nhân và tổ chức.
- Hệ thống hiện tại lỗi thời: Các hệ thống quản lý thông tin cũ có chức năng quá đơn giản, nội dung không toàn diện, đồng thời gặp hạn chế lớn về vấn đề bảo mật và chia sẻ thông tin.
- Bài toán đặc thù: Đăng ký và quản lý chính xác, nhanh chóng thông tin của ngựa thể thao trong quá trình thi đấu thực tế trên sân.

# Method

Tác giả đề xuất một Hệ thống hỗ trợ ra quyết định và quản lý thông tin đăng ký ngựa thể thao kết hợp giữa phần mềm và phần cứng:

- **Thuật toán Học sâu (Deep Learning - DL):** Áp dụng thuật toán học sâu kết hợp phương pháp Trí tuệ doanh nghiệp (Business Intelligence) để xử lý dữ liệu lớn, giảm thiểu tỷ lệ lỗi và nâng cao độ chính xác quản lý. Sơ đồ khối hoạt động gồm các bước: Nhận dữ liệu đầu vào $\rightarrow$ Đăng ký $\rightarrow$ Lưu cơ sở dữ liệu $\rightarrow$ Quản lý dữ liệu Học sâu $\rightarrow$ Xuất đầu ra.
- **Tăng tốc phần cứng bằng FPGA:** Sử dụng phần cứng reconfigurable FPGA (thiết kế dựa trên phần mềm Xilinx) tích hợp với CPU để xử lý song song các tác vụ thị giác máy tính chuyên sâu.
- **Hệ thống thị giác (Vision System):** Sử dụng hai camera bố trí trong nhà thi đấu để cung cấp tầm nhìn toàn diện, tự động theo dõi quỹ đạo chuyển động của ngựa và vận động viên.

# Dataset

- Hệ thống sử dụng dữ liệu mô phỏng ban đầu được tạo ra ngẫu nhiên dựa trên tỷ lệ thi đấu.
- Dữ liệu hình ảnh/video thực tế thu nạp trực tiếp từ hệ thống 2 camera giám sát động để theo dõi chuyển động của ngựa thể thao và vận động viên trong sân đấu.

# Evaluation

Hiệu năng của hệ thống được đánh giá qua hai khía cạnh chính và so sánh trực tiếp với hai phương pháp truyền thống là SVM (Support Vector Machine) và Cây quyết định (Decision Tree):

- **Chỉ số hiệu năng thuật toán:** Độ chính xác (Accuracy %), Tỷ lệ lỗi (Error Rate %), và Thời gian xử lý (Time Analysis - tính bằng giây).
- **Chỉ số tài nguyên phần cứng (trên chip FPGA):** Điện năng tiêu thụ (Power supply - W), Số lượng cấu trúc Slice (Slice count), và Số lượng mạch chốt (Latches count).

# Results

Phương pháp Học sâu tăng tốc bằng FPGA vượt trội hơn hẳn so với các phương pháp cũ:

- **Độ chính xác cao vượt trội:** Đạt 94.7% (trong khi SVM chỉ đạt 76.6% và Decision Tree đạt 81.9%).
- **Tỷ lệ lỗi thấp tối đa:** Giảm xuống chỉ còn 5.4% (so với SVM là 23.9% và Decision Tree là 15.4%).
- **Thời gian xử lý siêu tốc:** Chỉ mất 3.7 giây để hoàn thành phân tích (nhanh hơn nhiều so với SVM là 13.2 giây và Decision Tree là 11.7 giây).
- **Tiết kiệm năng lượng:** Tiêu thụ điện năng chỉ 13W, thấp hơn hẳn so với SVM (26W) và Decision Tree (19W).
- **Lưu ý về tài nguyên phần cứng:** Để đổi lấy hiệu năng cao, hệ thống DL yêu cầu phần cứng lớn hơn, tiêu tốn 421 Slices và 504 Latches.

# Limitations

- Văn phong bài báo lặp lại: Bản text của bài báo (Journal Pre-proof) có nhiều đoạn câu từ bị lặp lại, hành văn đôi chỗ lủng củng và giống định dạng dịch thô hoặc sinh tự động (ví dụ: "take a gander at details" , "Information base structure enhancement is straightforwardly identified..." ).
- Thiếu chi tiết thuật toán: Bài báo nói về "Deep Learning" và "Deep Fusion Learning" nhưng không giải thích rõ cấu trúc mạng cụ thể được dùng là gì (như CNN, RNN hay mạng tùy biến nào khác).
- Đánh giá phần cứng chưa tối ưu: Lượng tài nguyên phần cứng (Slice và Latches) bị chiếm dụng nhiều hơn đáng kể so với các phương pháp cũ, điều này có thể gây hạn chế khi triển khai trên các dòng chip FPGA phân khúc thấp.

# Relevance to our topic

- **Tự động hóa quản lý thông tin ngựa bằng AI:** Bài báo minh chứng cách áp dụng Học sâu (Deep Learning) và Trí tuệ doanh nghiệp (BI) để số hóa, tự động cấp mã số và quản lý cơ sở dữ liệu đăng ký của ngựa thể thao trong thi đấu, thay thế hoàn toàn cho các phương pháp báo cáo thủ công cũ.
- **Thị giác máy tính theo dõi chuyển động của ngựa:** Hệ thống trong bài nghiên cứu sử dụng camera thông minh kết hợp thuật toán AI để tự động theo dõi (auto-track) quỹ đạo di chuyển, phân tích các động tác kỹ thuật và trạng thái vận động của cả ngựa lẫn kỵ sĩ theo thời gian thực trên sân.
- **Triển khai AI phần cứng tối ưu cho trường đua:** Hướng dẫn phương pháp đưa mô hình AI lên thiết bị phần cứng nhúng (FPGA) giúp hệ thống xử lý hình ảnh cực nhanh (chỉ mất 3.7 giây), giảm độ trễ tối đa và tiết kiệm điện năng, rất phù hợp để lắp đặt vận hành thực tế tại các trường đua hoặc nhà thi đấu.

# Possible improvement

- **Cụ thể hóa kiến trúc AI:** Thay vì dùng "Học sâu" chung chung, nhóm có thể áp dụng các mô hình Object Tracking hiện đại thời gian thực (ví dụ: YOLOv8/YOLOv10 kết hợp với ByteTrack hoặc StrongSORT) để nhận diện và theo dõi chính xác hơn cả ngựa lẫn kỵ sĩ.
- **Tối ưu thiết kế phần cứng (FPGA):** Áp dụng các kỹ thuật lượng tử hóa mô hình (Quantization) hoặc cắt tỉa mạng (Pruning) để giảm số lượng Slices và Latches tiêu thụ trên chip, giúp hệ thống nhẹ hơn và dễ triển khai trên thiết bị Edge-AI thực tế.
- **Xây dựng Dataset thực tế chuẩn hóa:** Thay thế dữ liệu tạo ngẫu nhiên bằng một tập dữ liệu video chất lượng cao được gán nhãn chuẩn (Bounding box, Keypoints chuyển động của ngựa) để tăng tính thuyết phục cho phần đánh giá thuật toán.
