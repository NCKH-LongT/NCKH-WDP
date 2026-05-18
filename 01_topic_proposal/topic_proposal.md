TOPIC PROPOSAL
1. Tên đề tài dự kiến
Scientific Journal Publication Trend Tracking System
Tên tiếng Việt đề xuất:
Hệ thống theo dõi xu hướng công bố bài báo khoa học trên các tạp chí học thuật
2. Lĩnh vực ứng dụng
Lĩnh vực ứng dụng của đề tài là:
Khai phá dữ liệu và Trực quan hóa dữ liệu (Data Mining & Data Visualization)
Quản lý tri thức học thuật (Academic Knowledge Management)
Phân tích dữ liệu lớn (Big Data Analytics)
Kỹ thuật phần mềm (Software Engineering)
Phân tích xu hướng dựa trên siêu dữ liệu (Metadata-based trend analysis)
Đề tài được áp dụng độc lập như một hệ thống quản lý tri thức, hỗ trợ các trường đại học, viện nghiên cứu và cá nhân làm khoa học tối ưu hóa giai đoạn Literature Review.
3. Vấn đề thực tế
Hiện nay, số lượng bài báo khoa học được công bố trên thế giới đang bùng nổ theo cấp số nhân, quá trình khảo sát và chọn hướng nghiên cứu thường gặp nhiều khó khăn:
Người dùng có thể tìm paper bằng Google Scholar, Semantic Scholar, IEEE, Scopus, OpenAlex, Crossref, v.v. nhưng đa số nền tảng chỉ tập trung vào search theo keyword thuần túy.
Người dùng cực kỳ khó nhận biết một chủ đề nghiên cứu cụ thể đang tăng trưởng mạnh mẽ hay đang giảm dần theo thời gian (Bão hòa).
Khó phát hiện kịp thời các chủ đề, từ khóa mới nổi do các bộ máy tìm kiếm truyền thống thường ưu tiên hiển thị bài báo cũ có lượt trích dẫn cao.
Khó so sánh xu hướng phát triển một cách trực quan giữa các keyword, các journal hoặc các nhóm chủ đề nghiên cứu.
Sinh viên, giảng viên và researcher mất quá nhiều thời gian đọc khảo sát thủ công chỉ để chọn được hướng nghiên cứu phù hợp.
Dữ liệu học thuật mở có rất nhiều trên các API công khai nhưng chưa được tổng hợp và trực quan hóa thành các dashboard biểu đồ dễ hiểu.
4. Đối tượng người dùng
4.1 Researcher
Là nhà nghiên cứu sử dụng hệ thống chuyên sâu nhất.
Nhu cầu:
Phân tích và dự đoán trend dài hạn của một lĩnh vực.
Theo dõi sát sao hoạt động của các Keyword, Journal, Topic.
Phát hiện các hướng nghiên cứu mới (chủ đề ngách tiềm năng).
Xuất các báo cáo phân tích xu hướng (Trend Reports) để làm tài liệu tổng quan.
4.2 Lecturer / Student
Là giảng viên hoặc sinh viên sử dụng hệ thống ở mức cơ bản hơn.
Nhu cầu:
Tìm kiếm bài báo tham khảo nhanh theo từ khóa, tác giả, tạp chí.
Xem các dashboard đơn giản để nắm bắt các topic phổ biến của ngành.
Lưu bài báo (Bookmark) và theo dõi (Follow) từ khóa để chọn đề tài tốt nghiệp hoặc làm literature review.
4.3 System Administrator
Là người quản trị hệ thống.
Nhu cầu:
Quản lý tài khoản người dùng và phân chia quyền hạn (RBAC).
Cấu hình kết nối và quản lý hạn mức gọi các API nguồn dữ liệu học thuật.
Giám sát, thiết lập lịch trình và kích hoạt (Force Sync) quá trình đồng bộ dữ liệu hệ thống.
5. Lý do cần tích hợp AI và Thuật toán Analytics
Thuật toán dữ liệu và AI được tích hợp vào hệ thống nhằm biến các metadata bài báo khoa học rời rạc thành các insight xu hướng trực quan. Các lý do chính bao gồm:
Giảm tối đa thời gian làm tổng quan tài liệu (Literature Review) cho người dùng.
Tự động hóa việc gom nhóm và đếm tần suất xuất hiện của từ khóa theo từng năm.
Ứng dụng công thức Toán học phi tuyến tính Trend Score để tính toán chính xác độ hot thực tế của từ khóa, khắc phục nhược điểm của phép tính phần trăm thông thường.
Sử dụng hàm Logarit để kìm hãm ưu thế số lượng của các từ khóa cũ, giúp các từ khóa mới xuất hiện có cơ hội hiển thị trên bảng xếp hạng xu hướng.
Tự động phát hiện và cảnh báo các chủ đề đang bứt phá mạnh mẽ để gợi ý hướng nghiên cứu đón đầu công nghệ.
6. Model AI và Nguồn API dự kiến sử dụng
Hệ thống không tự xây dựng hoặc huấn luyện mô hình AI riêng, cũng như không thu thập dữ liệu bằng cách crawl web thủ công. Thay vào đó, hệ thống sẽ kết nối với các API học thuật công khai:
OpenAlex API
Semantic Scholar API
Crossref API
Hệ thống sẽ gửi yêu cầu và nhận dữ liệu đầu vào (Metadata) bao gồm: Title, Abstract, Keywords, Authors, Journal, Publication year, DOI, Citation count.
Dữ liệu sau khi xử lý sẽ được nạp vào Backend để tính toán và trả về kết quả trên UI:
Số lượng bài báo theo năm (Line Chart).
Top từ khóa bứt phá nhất (Word Cloud / Bar Chart dựa trên điểm Trend Score).
Thứ hạng các tạp chí công bố nhiều bài nhất theo từng Topic.
Danh sách paper mới dựa trên những Keyword/Journal mà người dùng đã bấm Theo dõi 
7. Kết quả mong muốn
7.1 Về mặt hệ thống
Hệ thống có thể tự động gọi API quốc tế theo lịch trình ngầm định kỳ bằng node-cron vào khung giờ thấp điểm 
Hệ thống thực hiện chuẩn hóa dữ liệu (Normalization) và lọc trùng lặp bài báo dựa trên mã định danh duy nhất DOI.
Hệ thống chạy mượt mà các câu lệnh MongoDB Aggregation Pipeline để xử lý tính toán số liệu tại chỗ (Local Database), đảm bảo thời gian tải trang Dashboard nhanh chóng
Giao diện hiển thị trực quan các biểu đồ xu hướng uốn lượn và đám mây từ khóa sinh động.
7.2 Về mặt người dùng
Sinh viên và Giảng viên có cái nhìn toàn cảnh về dòng chảy công nghệ của ngành để chọn đề tài an toàn hoặc bứt phá.
Nhà nghiên cứu có công cụ đối sánh xu hướng mạnh mẽ, tiết kiệm hàng tuần trời tìm kiếm tài liệu thủ công.
Người dùng nhận được thông báo tự động (Notification) ngay khi có paper mới thuộc chủ đề mình quan tâm.
7.3 Về mặt nghiên cứu ứng dụng
Đánh giá hiệu quả của việc thiết kế một Data Pipeline trong Node.js khi tách biệt luồng xử lý nặng chạy ngầm ra khỏi luồng tương tác của người dùng cuối.
Thử nghiệm độ chính xác của công thức Trend Score phối hợp hàm trừ bứt phá (ΔN) và hàm nén Logarit (ln) trong việc lọc nhiễu dữ liệu học thuật lớn.
8. Phạm vi đề tài
8.1 In Scope
Đề tài tập trung vào:
Quản lý tài khoản người dùng, lưu Bookmark và danh sách Follow.
Tích hợp các API học thuật mở để lấy Metadata bài báo.
Xử lý luồng chạy ngầm định kỳ (node-cron) để cập nhật dữ liệu tự động.
Chuẩn hóa từ khóa (chữ thường, xóa khoảng trắng) và lọc trùng bằng mã DOI.
Tiếp nhận và xử lý các bài báo khoa học do người dùng chủ động cập nhật/nạp vào hệ thống.
Tính toán các chỉ số xu hướng (Growth Rate % và Trend Score) bằng MongoDB Aggregation.
Trực quan hóa dữ liệu lên các biểu đồ giao diện (Dashboard Charts).
8.2 Out of Scope
Đề tài không bao gồm:
Tự xây dựng, huấn luyện hoặc tinh chỉnh (Fine-tuning) các mô hình AI.
Cào dữ liệu bằng các công cụ crawl web tự chế gây quá tải hệ thống nguồn.
Cập nhật dữ liệu theo thời gian thực (Real-time) liên tục từng giây từng phút.
Bao phủ mọi lĩnh vực học thuật khác (Chỉ giới hạn scope trong ngành Computer Science và AI).
9. Định hướng áp dụng vào hệ thống
Đề tài này sẽ được áp dụng trực tiếp vào các module chức năng sau:
Academic Data Ingestion Module: Chịu trách nhiệm chạy ngầm định kỳ  để gọi API quốc tế, xử lý giới hạn lượt gọi (Rate Limit), chuẩn hóa dữ liệu và lọc trùng bài báo bằng mã DOI.
User-Contributed Content Module: Xử lý logic tiếp nhận thông tin bài báo mới do người dùng chủ động nạp vào hệ thống để cập nhật kho dữ liệu.
Trend Analytics Engine: Chạy các câu lệnh MongoDB Aggregation tính toán điểm Trend Score và Growth Rate dựa trên dữ liệu tổng hợp.
Researcher & Student Dashboard: Giao diện trực quan hóa dữ liệu thành Đám mây từ khóa (Word Cloud) và Biểu đồ đường (Line Chart) phục vụ người dùng cuối.
Quy trình tổng quan: Hệ thống cào dữ liệu tự động theo danh sách từ khóa hạt giống từ API quốc tế kết hợp với bài báo do người dùng tự đóng góp → Tiến hành lọc trùng bằng mã DOI và lưu vào Database → Tính toán sẵn điểm số xu hướng bằng công thức Logarit → Trả kết quả JSON siêu tốc lên Dashboard biểu đồ trực quan cho người dùng theo dõi.
10. Kết luận
Đề tài Scientific Journal Publication Trend Tracking System hoàn toàn phù hợp với định hướng phát triển một ứng dụng quản lý tri thức và phân tích dữ liệu lớn hiện đại. Bằng việc giải quyết triệt để bài toán "nhiễu thông tin" trong dữ liệu khoa học thông qua các thuật toán tính chỉ số xu hướng thông minh, hệ thống mang lại giá trị thực tiễn cực kỳ cao cho cộng đồng học thuật, giúp biến những dữ liệu bài báo rời rạc thành những insight xu hướng công nghệ vô giá trong thời gian ngắn nhất.
