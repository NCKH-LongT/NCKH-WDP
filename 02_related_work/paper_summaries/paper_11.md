# Citation

- **Title:** Optimal Model of Horse Racing Competition Decision Management Based on Association Rules and Neural Network
- **Authors:** Shuang Zhang
- **Year:** 2022
- **Source:** Scientific Programming (Hindawi)
- **DOI/Link:** https://doi.org/10.1155/2022/4240244

# Problem

Bài báo giải quyết các vấn đề sau:

- Sự bùng nổ về quy mô và số chiều dữ liệu (dimensional disaster) trong đua ngựa hiện đại gây ra nhiều khó khăn cho việc quản lý và dự đoán kết quả giải đấu.
- Các mô hình dự đoán truyền thống bộc lộ nhiều khuyết điểm như cấu trúc hệ thống chưa hoàn thiện và độ chính xác dự báo thấp, không còn đáp ứng được nhu cầu thực tế.
- Khó khăn trong việc định lượng và sắp xếp mức độ ảnh hưởng của hàng loạt yếu tố đan xen (yếu tố bên trong con ngựa lẫn tác động bên ngoài) lên thành tích thi đấu.

# Method

Tác giả đề xuất một mô hình tối ưu hóa quản lý quyết định dựa trên sự kết hợp giữa Luật kết hợp (Association Rules) và Mạng thần kinh (Neural Network):

- **Mạng thần kinh truyền ngược (BP Neural Network):** Sử dụng cấu trúc 3 lớp (đầu vào, lớp ẩn, đầu ra) làm lõi tính toán và ánh xạ mối quan hệ phi tuyến phức tạp của các thuộc tính giải đua. Dữ liệu đầu vào được chuẩn hóa về khoảng $[0, 1]$.
- **Luật kết hợp (Association Rules):** Được dùng để tìm ra mối liên kết ngầm giữa các nơ-ron (biến số), từ đó xác định trọng số (connection strength) và tỷ lệ đóng góp của từng yếu tố đầu vào đối với kết quả dự đoán.
- **Thuật toán phụ trợ nền tảng:** Áp dụng thuật toán ISSFS để lựa chọn đặc trưng dữ liệu và thuật toán lai HGAPSO để tối ưu hóa các tham số phạt ($C, g$) của cấu trúc mô hình nền. Sử dụng phân phối Weibull 3 tham số để tính toán hàm độ tin cậy/sức khỏe của ngựa.
- **Kiến trúc hệ thống:** Xây dựng hệ thống theo mô hình B/S (Browser/Server) phân tầng thành 4 lớp rõ rệt từ dưới lên trên: Lớp thu thập dữ liệu -> Lớp dịch vụ dữ liệu -> Lớp logic nghiệp vụ -> Lớp giao diện người dùng.

# Dataset

- Dữ liệu thực nghiệm được thu thập từ hơn 5,000 bản ghi huấn luyện và thi đấu thực tế thuộc 9 lịch trình cự ly chặng đua khác nhau (kéo dài từ 1000m đến 2400m).
- Tập dữ liệu bao gồm thông tin toàn diện của hai mùa giải (2019 và 2020) liên quan đến địa điểm, thông số ngựa, huấn luyện viên và nài ngựa.
- Hệ thống theo dõi và phân tích 13 yếu tố ảnh hưởng cốt lõi, phân thành 4 nhóm chính:
  - Yếu tố quyết định: Lịch trình/cự ly chặng đua (schedule).
  - Yếu tố nội tại của ngựa: Tuổi (age), giới tính (gender), cân nặng (weight).
  - Yếu tố chất lượng phong độ: Điểm số năng lực (score), tỷ lệ lọt vào top 3 (horse top three rate).
  - Yếu tố tác động bên ngoài: Nài ngựa (jockey), khối lượng tạ cõng (weight load), trang bị cương ngựa (harness), vị trí phân hạng lồng (qualifying), tính chất sân (field nature), trường đua (field), và huấn luyện viên (trainer).

# Evaluation

Hệ thống được đánh giá qua các chỉ số thực nghiệm hệ thống và mô phỏng bao gồm:

- **Độ chính xác dự đoán (Prediction Accuracy %):** Đo lường bằng cách đối chiếu kết quả dự báo của mạng thần kinh với kết quả chạy thực tế trên các cự ly.
- **Thời gian xử lý dự toán (Average Time Consumption):** Đo bằng giây (s) kể từ khi hệ thống nhận yêu cầu đến khi xuất kết quả.
- **Tỷ lệ thẩm định sai / tỷ lệ lỗi (Misappraisal rate / Error rate %).**
- **Độ cải thiện thành tích thực tế:** So sánh thời gian chạy trung bình của Top 3 qua các mùa giải sau khi áp dụng mô hình quản lý quyết định.

# Results

- **Trọng số tầm quan trọng của các biến:** AI đã phân tích dữ liệu lớn và chứng minh thứ tự ảnh hưởng từ mạnh nhất đến yếu nhất của 13 yếu tố là: Lịch trình chặng đua > Tuổi > Giới tính > Cân nặng > Điểm số > Tỷ lệ lọt Top 3 > Nài ngựa > Khối lượng cõng > Trang bị > Vị trí phân hạng > Tính chất sân > Trường đua > Huấn luyện viên
- **Hiệu suất thuật toán:** Mô hình mạng thần kinh (Neural Network) đạt độ chính xác vượt mức 90%. Kết quả này vượt trội hơn hẳn so với các thuật toán truyền thống khác như Mô hình xám (đạt hơn 80%), Trung bình trượt động, hay San phẳng số mũ.
- **Hiệu năng hệ thống trên Web:** Thời gian tiêu thụ dự đoán trung bình của hệ thống cực kỳ nhanh, chỉ mất 2.01 giây (hệ thống cũ mất 3.75 giây). Tỷ lệ lỗi trung bình rất thấp, ở mức 0.12%.
- **Ứng dụng thực tế:** Khi áp dụng mô hình vào quản lý huấn luyện, thành tích thi đấu của mùa giải 2020 đã được tối ưu hóa rõ rệt so với 2019, thời gian chạy trung bình của Top 3 giảm cao nhất tới 0.984 giây.

# Limitations

- Các phân hệ chức năng trên nền tảng hệ thống hiện tại vẫn chưa hoàn thiện hoàn toàn ở mức tối đa.
- Độ chính xác và tính bền vững lâu dài của các dự đoán cuối cùng vẫn cần một lượng dữ liệu lớn và đa dạng hơn nữa từ các môi trường thực địa khác nhau để liên tục xác thực và kiểm chứng.

# Relevance to our topic

- **Xác thực vai trò của Nài ngựa (Jockey):** Bài báo xếp nài ngựa đứng vị trí thứ 7 trong các yếu tố quyết định và nằm trong nhóm "Yếu tố tác động ngoại cảnh cốt lõi". Đây là luận cứ học thuật vững chắc cho đề tài nghiên cứu sự phù hợp của nài ngựa.
- **Mẫu thiết kế hệ thống Web:** Mô hình kiến trúc 4 tầng (Collection -> Service -> Business Logic -> UI) dựa trên cấu trúc B/S và Web App (chạy đồng thời trên PC, Android, iOS) của bài báo là một khung tham chiếu (Blueprint) hoàn hảo cho việc lập trình một nền tảng quản lý đua ngựa hiện đại.

# Possible improvement

- **Nâng cấp kiến trúc mạng thần kinh đầu lõi:** Thay vì sử dụng mạng truyền ngược BP Neural Network cổ điển vốn dễ rơi vào cực trị cục bộ, nhóm có thể đề xuất thay thế bằng các kiến trúc Học sâu tân tiến như Mạng thần kinh tích chập (CNN) kết hợp các tầng Chú ý (Attention Layer) để tăng khả năng phân tích ma trận dữ liệu.
- **Mở rộng các thuộc tính động thực thời (Bio-data):** Mô hình hiện tại của tác giả phụ thuộc vào dữ liệu bảng tĩnh và thông số nhập thủ công. Nhóm có thể đề xuất hướng cải tiến là nạp thêm luồng dữ liệu sinh học thời gian thực (nhịp tim, tần số bước chạy thu thập từ cảm biến hoặc camera) vào làm nơ-ron đầu vào, giúp hệ thống đưa ra quyết định huấn luyện chính xác hơn.
