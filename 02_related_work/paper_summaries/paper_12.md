# Citation

- **Title:** Machine Learning-based Learning-to-Rank Approach for Horse Race Prediction and Web Service Development
- **Authors:** Yubin So, Eunbi Woo, Hanjun Lee
- **Year:** 2025
- **Source:** Journal of The Korea Society of Computer and Information / JKSCI
- **DOI/Link:** Machine Learning-based Learning-to-Rank Approach for Horse Race Prediction and Web Service Development

# Problem

Bài báo tập trung khắc phục những hạn chế lớn của các mô hình dự đoán kết quả đua ngựa truyền thống:

- **Hạn chế của việc dự đoán đơn lẻ:** Các nghiên cứu trước đây thường chỉ dự đoán xác suất chiến thắng hoặc thời gian chạy của từng cá thể ngựa độc lập, chưa mô hình hóa được thứ hạng tương đối giữa các con ngựa trong cùng một lượt đua.
- **Điểm yếu của phương pháp Pairwise LTR cũ:** Một số nghiên cứu gần đây áp dụng cấu trúc so sánh cặp (Pairwise) nhưng bị giới hạn trong việc chỉ so sánh giữa hai cá thể, dẫn đến việc không thể học và tối ưu hóa thứ hạng trên toàn bộ danh sách ngựa tham gia lượt chạy.
- **Hệ thống dự đoán thiếu trực quan:** Các tài liệu dự báo truyền thống quá phức tạp khiến những người mới tham gia (novice users) rất khó phân tích dữ liệu để đưa ra quyết định đặt cược một cách khoa học.

# Method

Tác giả đề xuất một khung giải pháp toàn diện sử dụng cách tiếp cận Học xếp hạng (Learning-to-Rank - LTR) phối hợp giữa thuật toán máy học nâng cao và ứng dụng web dịch vụ thực tế:

- **Thuật toán học xếp hạng Listwise:** Áp dụng thuật toán LambdaRank theo cơ chế Listwise tích hợp vào mô hình LightGBM (sử dụng hàm mục tiêu rank_xendcg) nhằm trực tiếp tối ưu hóa thứ tự của toàn bộ danh sách ngựa trong một trận đấu.
- **Thử nghiệm đối chứng các mô hình GBDT:** So sánh mô hình đề xuất với hai cấu trúc LTR dựa trên cơ chế Pairwise bao gồm XGBoost (hàm rank:pairwise) và CatBoost (hàm YetiRankPairwise).
- **Giải thích mô hình:** Sử dụng phương pháp phân tích mức độ quan trọng của đặc trưng (Feature Importance) dựa trên chỉ số Gini nhằm làm rõ cách các mô hình đưa ra quyết định xếp hạng.
- **Phát triển hệ thống dịch vụ Web:** Xây dựng một ứng dụng web dạng Đơn trang (SPA) hoàn chỉnh với kiến trúc: Giao diện người dùng (Frontend) bằng React, máy chủ xử lý (Backend) bằng Django, cơ sở dữ liệu quan hệ PostgreSQL, và lưu trữ đám mây qua AWS S3.

# Dataset

- Dữ liệu được thu thập từ Cơ quan Đua ngựa Hàn Quốc (Korea Racing Authority), tập trung vào các giải đua tại Trường đua Seoul (nơi chiếm 55% doanh thu toàn ngành).
- Quy mô mẫu gồm 9,140 hồ sơ dữ liệu cuộc đua diễn ra trong vòng 1 năm từ tháng 05/2024 đến tháng 04/2025.
- Các tập tin dữ liệu về ngựa, nài ngựa (jockey), và huấn luyện viên (trainer) được liên kết lại để tạo ra các biến phái sinh đa dạng:
  - **Đặc trưng lịch sử của ngựa:** Thứ hạng trung bình trong 5 trận gần nhất, thứ hạng trung bình tích lũy, tỷ lệ thắng.
  - **Đặc trưng kết hợp:** Tỷ lệ thắng phối hợp giữa ngựa-nài ngựa, thứ hạng trung bình của huấn luyện viên.
  - **Đặc trưng môi trường và sinh học:** Độ ẩm đường chạy, tình trạng đường đua, số cổng xuất phát, số ngày nghỉ ngơi và độ tuổi của ngựa.

# Evaluation

- **Kiểm chứng thuật toán:** Áp dụng kỹ thuật kiểm chứng chéo 5 lần (5-Fold Cross-Validation) được chia nhóm nghiêm ngặt theo ID cuộc đua (group_id) để ngăn chặn hoàn toàn hiện tượng rò rỉ dữ liệu (data leakage).
- **Chỉ số đánh giá xếp hạng học thuật:** Sử dụng các thang đo chất lượng danh sách gồm $NDCG$, $MAP$, $MRR$, và một chỉ số tùy biến gọi là ExactRank Accuracy (Độ chính xác thứ hạng tuyệt đối).
- **Mô phỏng kịch bản đặt cược thực tế:** Đánh giá độ chính xác của các mô hình dựa trên nhiều thể loại cược khác nhau (Win - Đơn thắng, Place/Show - Cược hạng đầu, Quinella - Cược đôi, Exacta - Cược đôi chính xác thứ tự, Trio - Tam kích, Trifecta - Tam kích chính xác thứ tự).
- **Mô phỏng ROI:** Tiến hành mô phỏng cược Top-N (chọn top 1 đến 3) để tính toán tỷ lệ hoàn vốn (ROI) và tỷ lệ trúng thực tế.

# Results

Kết quả thực nghiệm cho thấy hiệu năng của các mô hình thay đổi rõ rệt dựa trên mục tiêu ứng dụng cụ thể:

- **Về mặt học thuật và chất lượng xếp hạng chung:** Mô hình CatBoost đạt hiệu năng cao nhất với chỉ số $NDCG = 0.8895$ và $MAP = 0.4204$. Tuy nhiên, chỉ số $MRR$ của CatBoost thấp hơn (0.1785) do mô hình này tập trung tối ưu hóa tính nhất quán của toàn bộ danh sách thay vì chỉ tập trung vào vị trí Top-1.
- **Về mặt thực tế áp dụng đặt cược (Betting Scenarios):** LightGBM và XGBoost cho kết quả vượt trội hơn hẳn.
  - **LightGBM:** Thể hiện năng lực tốt nhất ở các thể loại cược yêu cầu thứ tự chính xác cao như cược Đơn (Win: 18.85%), cược Đôi chính xác (Exacta: 5.76%), và là mô hình duy nhất đạt tỷ lệ trúng trên 1% ở thể loại cược Tam kích chính xác siêu khó (Trifecta: 1.05%).
  - **XGBoost:** Đạt hiệu suất cao nhất ở các thể loại cược bao hàm (chỉ cần đối tượng nằm trong Top-N) như cược Hạng đầu (Place/Show: 52.88%), cược Tam kích (Trio: 5.24%) và cược Đôi bao hàm (Quinella Place: 19.37%).
- **Các đặc trưng cốt lõi quyết định thứ hạng:** Phân tích cho thấy Thứ hạng trung bình trong 5 trận gần nhất, Thứ hạng trung bình lịch sử, Trọng lượng tạ nặng phải gánh (assigned weight), và Tuổi của ngựa là 4 yếu tố quan trọng nhất ảnh hưởng đến chiến thắng.
- **Sản phẩm hệ thống:** Phát triển thành công dịch vụ web hiển thị trực quan các biểu đồ phân tích thành tích quá khứ, dự đoán thứ hạng theo thời gian thực và cho phép người dùng cá nhân hóa ngưỡng bộ lọc theo gu cược an toàn hay mạo hiểm.

# Limitations

- **Giới hạn thời gian dữ liệu:** Nghiên cứu chỉ sử dụng tập dữ liệu bảng (tabular data) trong một năm duy nhất.
- **Thiếu các biến động phi cấu trúc thực tế:** Hệ thống chưa thể tự động tích hợp các yếu tố bất định phát sinh ngay trong ngày đua thực tế như sự thay đổi thời tiết đột ngột tại sân hoặc tình trạng sức khỏe tâm lý/thể chất tức thời của ngựa trước giờ xuất phát.

# Relevance to our topic

- **Kiến trúc hệ thống Web hoàn chỉnh:** Bài báo cung cấp một bản thiết kế hệ thống (System Architecture) rất thực tế, kết hợp các thuật toán máy học với nền tảng cơ sở dữ liệu quan hệ PostgreSQL. Đây là tài liệu tham khảo trực tiếp giúp định hình cách tổ chức dữ liệu quan hệ chặt chẽ giữa các đối tượng (Ngựa - Nài ngựa - Lịch sử thành tích) trên một hệ thống SaaS thực tế.
- **Cách tiếp cận bài toán bằng AI dạng Xếp hạng (LTR):** Thay vì chỉ phân loại xem ngựa có khỏe/yếu hoặc thắng/thua bằng các thuật toán phân loại tĩnh, bài báo gợi ý tư duy chuyển đổi bài toán phân tích thông số sinh học và phong độ của ngựa thành bài toán xếp hạng tương đối (Listwise), giúp tăng độ chính xác phân tích khi đặt trong một nhóm quần thể thi đấu cụ thể.
- **Xác định các thông số sinh học/vận động then chốt:** Kết quả phân tích Feature Importance giúp đội ngũ phát triển biết rõ tầm quan trọng của các chỉ số như độ tuổi của ngựa và tải trọng gánh chịu, từ đó ưu tiên thiết kế các trường dữ liệu trực quan trên giao diện ứng dụng để hỗ trợ người dùng ra quyết định nhanh chóng.

# Possible improvement

Nhóm nghiên cứu có thể mở rộng và tối ưu hóa từ nền tảng bài báo này:

- **Chuyển đổi Stack công nghệ linh hoạt:** Phù hợp với các hệ thống quản lý hiện đại, nhóm có thể chuyển đổi phần máy chủ backend từ Django sang Node.js và hệ cơ sở dữ liệu sang dạng tài liệu linh hoạt như MongoDB (Mongoose) để dễ dàng lưu trữ, mở rộng các trường dữ liệu sinh học (Bio-data) biến động liên tục của ngựa mà không bị giới hạn bởi cấu trúc bảng cứng nhắc của PostgreSQL.
- **Ứng dụng mô hình AI dạng chuỗi (Sequence Models):** Thay vì sử dụng các mô hình cây quyết định (GBDT) thuần túy vốn xử lý dữ liệu bảng tĩnh, nhóm có thể áp dụng các kiến trúc mạng học sâu xử lý chuỗi thời gian như LSTM, GRU hoặc Transformer để phân tích sâu hơn toàn bộ chuỗi hành vi lịch sử thi đấu và phong độ đa năm của ngựa.
- **Bổ sung dữ liệu IoT thời gian thực:** Khắc phục hạn chế của bài báo bằng cách tích hợp cổng API nhận dữ liệu trực tiếp từ các thiết bị cảm biến đeo trên người ngựa (như nhịp tim, nhiệt độ cơ thể tức thời trước trận đấu) để cập nhật lại điểm số dự đoán của mô hình AI ngay tại thời điểm thực tế diễn ra sự kiện.
