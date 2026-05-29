## Hệ thống Theo dõi Xu hướng Công bố Bài báo Khoa học

---

## Thông tin nhóm

Học kỳ: SU26
Lớp: SE1822
Môn học: WDP391
Nhóm: 04
Thành viên: Trần Đình Phong, Phạm Đức Thanh Phương, Đặng Thanh Tú, Ngô Nhật Minh

---

## 1. Tên đề tài đề xuất

Hệ thống Theo dõi Xu hướng Công bố Bài báo Khoa học

## 2. Lĩnh vực ứng dụng

Hệ thống được đề xuất thuộc các lĩnh vực:

- Phân tích và trực quan hóa dữ liệu học thuật
- Khai thác tài liệu khoa học
- Phát hiện và dự báo xu hướng nghiên cứu
- Truy xuất thông tin từ API thư mục học thuật
- Khám phá tri thức trong cơ sở dữ liệu học thuật
- Dashboard và trực quan hóa dữ liệu cho nghiên cứu

Đề tài được định vị là một nền tảng web tổng hợp metadata từ các API học thuật mở như Semantic Scholar, OpenAlex hoặc Crossref nhằm hỗ trợ nhà nghiên cứu, giảng viên và sinh viên phân tích xu hướng công bố trên các lĩnh vực nghiên cứu được chọn. Thay vì xây dựng một công cụ tìm kiếm toàn văn, hệ thống tập trung vào trực quan hóa xu hướng, theo dõi từ khóa và khám phá chủ đề nghiên cứu — những tính năng hiện còn thiếu trên các nền tảng học thuật hiện tại.

## 3. Phát biểu vấn đề

Sự tăng trưởng nhanh chóng về số lượng bài báo khoa học đã khiến việc theo dõi xu hướng nghiên cứu đang thay đổi ngày càng trở nên khó khăn đối với nhà nghiên cứu, giảng viên và sinh viên. Các nền tảng tìm kiếm học thuật như Google Scholar, Scopus và Web of Science chủ yếu được thiết kế để tra cứu bài báo chứ không phải để phân tích xu hướng. Những nền tảng này cho phép tìm kiếm bài báo cụ thể nhưng không cung cấp công cụ có cấu trúc để trực quan hóa sự xuất hiện, tăng trưởng hay suy giảm của các chủ đề nghiên cứu theo thời gian.

Khoảng trống này tạo ra một số hạn chế thực tiễn:

- Nhà nghiên cứu khó quan sát sự phát triển của một chủ đề qua các năm hoặc xác định lĩnh vực con nào đang được chú ý hoặc dần mất đi sức hút.
- Giao diện tìm kiếm dựa trên từ khóa không cung cấp ngữ cảnh không gian hay thời gian để hiểu bức tranh toàn cảnh nghiên cứu.
- Giảng viên và sinh viên phải duyệt thủ công qua các tập tài liệu lớn để xác định chủ đề nào đang còn hoạt động hoặc có tiềm năng nghiên cứu.
- Chưa có công cụ nhẹ, dễ tiếp cận nào kết hợp đồng thời việc tổng hợp metadata, phân tích xu hướng và trực quan hóa tương tác trong một nền tảng duy nhất.
- Các công cụ nghiên cứu thương mại hiện có thường tốn kém và không phù hợp với nhà nghiên cứu cá nhân hoặc các cơ sở học thuật có nguồn lực hạn chế.

Vì vậy, đề tài này đề xuất một nền tảng web thu thập và xử lý metadata bài báo từ các API học thuật miễn phí, sau đó áp dụng các kỹ thuật phân tích thống kê và trực quan hóa để làm nổi bật xu hướng công bố, xác định các chủ đề mới nổi và hỗ trợ khám phá nghiên cứu trong các lĩnh vực được chọn như Khoa học Máy tính hoặc Trí tuệ Nhân tạo.

## 4. Người dùng mục tiêu

- **Nhà nghiên cứu (Researcher)**: Phân tích xu hướng nghiên cứu chuyên sâu, theo dõi journal và từ khóa cụ thể theo thời gian, khám phá các chủ đề mới nổi và xem thống kê công bố qua các giai đoạn.
- **Giảng viên / Sinh viên (Lecturer / Student)**: Tìm kiếm bài báo tham khảo, khám phá các chủ đề nghiên cứu phổ biến hoặc đang trending, lưu bài báo hoặc từ khóa quan tâm, và xem dashboard xu hướng cơ bản phục vụ cho môn học hoặc luận văn.
- **Quản trị viên hệ thống (System Administrator)**: Quản lý tài khoản và phân quyền người dùng, cấu hình nguồn dữ liệu API bên ngoài, lên lịch và giám sát đồng bộ dữ liệu, và theo dõi tình trạng hệ thống.

## 5. Động lực nghiên cứu cho việc tích hợp phân tích dữ liệu

Động lực chính để tích hợp các tính năng phân tích và hỗ trợ bởi AI là vượt ra ngoài việc chỉ tổng hợp dữ liệu đơn thuần và cung cấp cho người dùng những thông tin nghiên cứu có giá trị thực tiễn. Số lượng bài báo và tần suất từ khóa thô đơn thuần là không đủ để diễn giải xu hướng; hệ thống cần làm nổi bật các mẫu không thể nhận ra chỉ qua tra cứu thông thường.

##### 5.1 Khối lượng và tốc độ tăng trưởng của bài báo khoa học

Số lượng bài báo xuất bản hàng năm trong các lĩnh vực như Khoa học Máy tính và Trí tuệ Nhân tạo đã tăng theo cấp số nhân. Việc thủ công xác định chủ đề nào đang tăng, đạt đỉnh hay suy giảm trong hàng ngàn bài báo mỗi năm là không khả thi nếu thiếu phân tích tự động. Tổng hợp thống kê và mô hình hóa xu hướng là cần thiết để làm cho thông tin này có thể tiếp cận và dễ diễn giải.

##### 5.2 Đồng xuất hiện từ khóa và phân cụm chủ đề

Một từ khóa đơn lẻ hiếm khi mô tả đầy đủ một chủ đề nghiên cứu. Các thuật ngữ liên quan thường xuất hiện cùng nhau và hình thành các cụm chủ đề. Phân tích các mẫu đồng xuất hiện từ khóa cho phép hệ thống nhóm các khái niệm có liên quan về mặt ngữ nghĩa thành các chủ đề nghiên cứu có cấu trúc và trình bày chúng dưới dạng cụm có thể khám phá trên dashboard, thay vì yêu cầu người dùng phải tự đoán từ khóa cần tìm.

##### 5.3 Phân tích xu hướng theo thời gian

Xu hướng công bố thay đổi theo thời gian và phản ánh những thay đổi rộng lớn hơn trong cộng đồng nghiên cứu. Một chủ đề có ít bài báo cách đây năm năm có thể là một trong những lĩnh vực tăng trưởng nhanh nhất hiện nay. Mô hình hóa các động lực thời gian này — thông qua tổng hợp chuỗi thời gian hoặc điểm xu hướng đơn giản — cho phép hệ thống gắn cờ các chủ đề mới nổi và cung cấp cho người dùng cái nhìn hướng đến tương lai về bức tranh nghiên cứu.

##### 5.4 Khám phá nghiên cứu cá nhân hóa

Mỗi người dùng có sở thích nghiên cứu và kiến thức nền tảng khác nhau. Bằng cách cho phép người dùng theo dõi các journal, từ khóa hoặc chủ đề cụ thể, và theo dõi hành vi đánh dấu của họ, hệ thống có thể gửi thông báo khi có bài báo mới phù hợp với sở thích của họ. Điều này giảm thời gian khám phá và nâng cao độ liên quan của thông tin được trình bày cho từng người dùng.

## 6. Các hướng tiếp cận kỹ thuật đề xuất

##### 6.1 Phân tích xu hướng

- **Đếm bài báo theo chuỗi thời gian**: Số lượng bài báo hàng năm và hàng quý theo từ khóa hoặc chủ đề được tổng hợp từ metadata đã thu thập để tạo ra các đường cong xu hướng. Các đường cong này là cơ sở để xác định lĩnh vực đang tăng trưởng, ổn định hay suy giảm.

- **Làm mượt bằng trung bình động**: Một trung bình động đơn giản được áp dụng lên số lượng bài báo để giảm nhiễu từ các mẫu công bố không đều và làm nổi bật xu hướng nền rõ ràng hơn.

- **Tính điểm tốc độ tăng trưởng**: Điểm tốc độ tăng trưởng tương đối được tính toán cho mỗi từ khóa hoặc chủ đề bằng cách so sánh số lượng bài báo gần đây với mức nền lịch sử. Các chủ đề có tốc độ tăng trưởng liên tục cao được hiển thị là các lĩnh vực mới nổi trên dashboard xu hướng.

##### 6.2 Phân tích từ khóa và chủ đề

- **Đồ thị đồng xuất hiện từ khóa**: Các mối quan hệ đồng xuất hiện giữa các từ khóa xuất hiện cùng nhau trong metadata bài báo được trích xuất và lưu trữ dưới dạng cấu trúc đồ thị. Đồ thị này được dùng để tạo cụm chủ đề và cung cấp dữ liệu cho trực quan hóa mối quan hệ từ khóa trên dashboard.

- **Xếp hạng từ khóa bằng TF-IDF**: Trọng số tần suất thuật ngữ - tần suất nghịch đảo tài liệu được áp dụng trên phần tóm tắt và trường từ khóa của bài báo để xếp hạng các từ khóa đặc trưng và tiêu biểu nhất cho từng lĩnh vực nghiên cứu và giai đoạn thời gian.

##### 6.3 Thu thập và đồng bộ dữ liệu

- **Tích hợp API bên ngoài**: Metadata bài báo được lấy định kỳ từ các API học thuật miễn phí bao gồm Semantic Scholar, OpenAlex hoặc Crossref. Hệ thống lưu trữ các bản ghi metadata đã chuẩn hóa gồm tiêu đề, tóm tắt, từ khóa, năm xuất bản, tác giả và tên journal.

- **Đồng bộ theo lịch**: Một job chạy nền hoạt động theo lịch có thể cấu hình (hàng ngày hoặc hàng tuần) để lấy các bản ghi mới xuất bản hoặc cập nhật từ các nguồn API đã cấu hình và cập nhật cơ sở dữ liệu nội bộ mà không cần can thiệp thủ công.

## 7. Hệ thống cốt lõi

##### 7.1 Ứng dụng web hướng người dùng

- **Xác thực và phân quyền người dùng**: Hệ thống hỗ trợ đăng ký tài khoản, đăng nhập và kiểm soát truy cập theo vai trò. Vai trò Researcher và Lecturer/Student có quyền truy cập các tính năng phân tích xu hướng và khám phá bài báo, trong khi vai trò Administrator có quyền truy cập cấu hình hệ thống và quản lý người dùng.

- **Tìm kiếm bài báo**: Người dùng có thể tìm kiếm bài báo theo từ khóa, tên tác giả hoặc tên journal. Kết quả tìm kiếm hiển thị tiêu đề, tóm tắt, tác giả, năm xuất bản và tên journal lấy từ cơ sở dữ liệu metadata đã đồng bộ.

- **Xem chi tiết bài báo**: Mỗi bài báo có trang chi tiết riêng hiển thị đầy đủ metadata bao gồm tóm tắt, từ khóa, tác giả, journal và năm xuất bản, cùng liên kết đến nguồn gốc khi có thể.

- **Dashboard xu hướng**: Một dashboard tương tác trực quan hóa xu hướng công bố theo thời gian cho các từ khóa, chủ đề hoặc journal được chọn. Biểu đồ bao gồm số lượng bài báo hàng năm, xu hướng tốc độ tăng trưởng và tần suất từ khóa theo thời gian dưới dạng biểu đồ đường và biểu đồ cột.

- **Xem chủ đề đang trending**: Một khu vực riêng biệt hiển thị các chủ đề nghiên cứu hoạt động nhất và tăng trưởng nhanh nhất dựa trên hoạt động công bố gần đây và điểm tốc độ tăng trưởng. Người dùng có thể duyệt chủ đề trending theo lĩnh vực hoặc khoảng thời gian.

- **Trực quan hóa mối quan hệ từ khóa**: Một đồ thị trực quan hoặc bản đồ cụm hiển thị các mối quan hệ đồng xuất hiện giữa các từ khóa, cho phép người dùng khám phá cách các khái niệm nghiên cứu liên quan kết nối với nhau và xác định các nhóm chủ đề lân cận.

- **Đánh dấu (Bookmark)**: Người dùng có thể đánh dấu các bài báo hoặc từ khóa muốn xem lại. Các mục đã đánh dấu có thể truy cập từ trang thư viện cá nhân.

- **Theo dõi journal và chủ đề**: Người dùng có thể theo dõi các journal hoặc chủ đề nghiên cứu cụ thể để nhận thông báo khi có bài báo mới phù hợp với sở thích của họ được phát hiện trong chu kỳ đồng bộ tiếp theo.

- **Thông báo**: Hệ thống gửi thông báo trong ứng dụng thông báo cho người dùng về các bài báo mới xuất bản trong journal hoặc chủ đề họ đang theo dõi sau mỗi lần cập nhật dữ liệu theo lịch.

- **Tạo báo cáo phân tích**: Người dùng có thể tạo các báo cáo tải về đơn giản tóm tắt xu hướng công bố cho một từ khóa hoặc chủ đề được chọn trong một khoảng thời gian xác định, xuất ra dưới định dạng PDF hoặc CSV.

##### 7.2 Bảng quản trị (Admin Panel)

- **Quản lý người dùng**: Quản trị viên có thể xem, kích hoạt, vô hiệu hóa và gán vai trò cho các tài khoản người dùng.

- **Cấu hình nguồn dữ liệu API**: Quản trị viên có thể cấu hình các API học thuật bên ngoài nào được bật, thiết lập API key hoặc tham số yêu cầu, và xác định các lĩnh vực nghiên cứu mục tiêu để thu thập dữ liệu.

- **Quản lý đồng bộ dữ liệu**: Quản trị viên có thể xem trạng thái của lần chạy đồng bộ gần nhất, kích hoạt đồng bộ thủ công và xem log hoạt động nhập dữ liệu.

- **Giám sát hệ thống**: Một trang tổng quan hệ thống đơn giản hiển thị số lượng bài báo, journal và từ khóa trong cơ sở dữ liệu cùng lịch sử đồng bộ.

##### 7.3 Backend và pipeline dữ liệu

- **Pipeline nhập metadata**: Một pipeline theo lịch lấy metadata bài báo từ các API bên ngoài đã cấu hình, chuẩn hóa dữ liệu về một schema thống nhất, loại bỏ trùng lặp theo DOI hoặc hash tiêu đề, và lưu trữ vào cơ sở dữ liệu ứng dụng.

- **Lớp tính toán xu hướng**: Sau mỗi chu kỳ đồng bộ, một tác vụ tính toán nền cập nhật số lượng bài báo theo từ khóa và năm, tính lại điểm tốc độ tăng trưởng và làm mới dữ liệu đồ thị đồng xuất hiện để phản ánh trạng thái mới nhất của tập dữ liệu.

- **REST API**: Backend cung cấp một REST API được frontend web sử dụng. Các endpoint hỗ trợ tìm kiếm bài báo, truy vấn xu hướng, quản lý bookmark, lấy thông báo và các thao tác quản trị.

## 8. Ràng buộc và giả định của hệ thống

- Hệ thống sử dụng metadata công khai từ các API học thuật như Semantic Scholar, OpenAlex hoặc Crossref thông qua gói truy cập miễn phí.
- Chỉ thu thập metadata bài báo, bao gồm tiêu đề, tóm tắt, từ khóa, năm xuất bản, tác giả và tên journal. Nội dung toàn văn không được xử lý do giới hạn bản quyền và dung lượng lưu trữ.
- Dữ liệu thu thập được giả định là hợp lệ, có cấu trúc hợp lý và luôn khả dụng từ các API bên thứ ba đã cấu hình.
- Hệ thống phân tích dữ liệu trong một tập hợp lĩnh vực nghiên cứu được chọn trước (ví dụ: Khoa học Máy tính hoặc Trí tuệ Nhân tạo) để quản lý phạm vi và giảm độ phức tạp của tập dữ liệu.
- Cập nhật dữ liệu theo chu kỳ định kỳ (hàng ngày hoặc hàng tuần) và không yêu cầu đồng bộ thời gian thực.
- Nền tảng không thực hiện lập chỉ mục toàn văn hoặc nhúng ngữ nghĩa nội dung bài báo trong phiên bản ban đầu.

## 9. Kết quả kỳ vọng

Các kết quả kỳ vọng của đề tài bao gồm:

- Một nền tảng web hoạt động được, tổng hợp metadata bài báo học thuật từ các API mở và trình bày xu hướng công bố thông qua các trực quan hóa tương tác.

- Một lớp phân tích xu hướng làm nổi bật các chủ đề nghiên cứu đang tăng trưởng và mới nổi dựa trên dữ liệu công bố lịch sử, tần suất từ khóa và điểm tốc độ tăng trưởng.

- Một trải nghiệm khám phá nghiên cứu cá nhân hóa cho phép người dùng theo dõi chủ đề và journal, đánh dấu bài báo và nhận thông báo về các bài báo mới liên quan đến sở thích của họ.

- Một trực quan hóa mối quan hệ từ khóa giúp người dùng khám phá các nhóm chủ đề lân cận và hiểu cách các khái niệm nghiên cứu liên kết với nhau.

- Một minh chứng về cách các API dữ liệu học thuật mở có thể phục vụ như nền tảng dữ liệu cho một công cụ nghiên cứu thông minh nhẹ nhưng hữu ích, có thể tiếp cận bởi nhà nghiên cứu cá nhân và cộng đồng học thuật mà không cần chi phí đăng ký.
