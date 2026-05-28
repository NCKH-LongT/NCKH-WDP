# Citation

- **Title:** Winning the Race: Profitability in Pari-Mutuel Horse Betting.
- **Authors:** Alexander Won.
- **Year:** 2025.
- **Source:** Wharton Research Scholars, The Wharton School, University of Pennsylvania.
- **DOI/Link:** https://repository.upenn.edu/server/api/core/bitstreams/9b580267-c2ab-45f5-a3e0-cace231c4fa4/content.

# Problem

Bài báo giải quyết câu hỏi liệu một chiến lược cá cược thể thao dựa trên dữ liệu có thể mang lại lợi nhuận bền vững, đã điều chỉnh rủi ro trong các hệ thống cá cược chia đều (pari-mutuel) của Câu lạc bộ đua ngựa Hồng Kông (HKJC) hay không.
Tác giả chỉ ra một khoảng trống trong các nghiên cứu trước đây: thiếu sự kết hợp đồng thời giữa phân tích dự đoán, quản lý danh mục đầu tư và tâm lý cá cược tại một thị trường khó dự đoán như HKJC.

# Method

- **Phân tích dự đoán:** Sử dụng mô hình Extreme Gradient Boosting (XGBoost) phân loại đa lớp (multi-class soft-probability) để tạo ra các dự báo xác suất chiến thắng cho từng con ngựa trong cuộc đua.
- **Quản lý vốn (Portfolio management):** Sử dụng chiến lược phân bổ vốn Dutching (chia vốn để đạt lợi nhuận đồng đều) và Tiêu chuẩn Kelly phân số (fractional-Kelly) nhằm tối đa hóa lợi tức đầu tư và kiểm soát biến động.

# Dataset

- Dữ liệu được thu thập (web scraping) từ trang web của HKJC, bao gồm các mùa giải từ năm 2015 đến 2024.
- Tập dữ liệu cuối cùng gồm 7.728 cuộc đua (chỉ lấy các cuộc đua hạng Class 1-5), được chuyển đổi sang định dạng bảng ngang (wide-format).
- Các đặc trưng (features) đầu vào bao gồm: tỷ lệ cược thị trường, thuộc tính của ngựa, thông tin nài ngựa (jockey), bối cảnh cuộc đua, và các biến số đo lường tâm lý người cá cược (như thành kiến gần đây - recency bias).

# Evaluation

- **Đánh giá mô hình dự đoán:** Sử dụng hàm mất mát Multiclass log-loss, Độ chính xác tổng thể (Accuracy) và đặc biệt tập trung vào Độ chuẩn xác (Precision - chỉ số quan trọng nhất trong cá cược để tránh các dự đoán dương tính giả gây mất tiền).
- **Đánh giá tài chính:** Dùng 100 mô phỏng Monte-Carlo back tests để đo lường Vốn cuối cùng (Bankroll), Hệ số nhân vốn (Multiple of Money - MoM) và Tỷ suất hoàn vốn nội bộ (IRR).

# Results

- Về mặt dự đoán, độ chuẩn xác (precision) của mô hình đối với con ngựa được đánh giá cao nhất (crowd-favorite) là 31,8%, vượt qua dự đoán của đám đông (30,75%) nhưng chỉ ở mức biên.
- Việc liên tục cá cược vào con ngựa được yêu thích nhất (dù áp dụng quản lý vốn Kelly) đều dẫn đến phá sản.
- Lợi nhuận thực sự được sinh ra từ việc khai thác có hệ thống các con ngựa không được yêu thích nhất (đặc biệt là ngựa số 4, 6, và 13) mà đám đông thường đánh giá thấp.
- Danh mục đầu tư tốt nhất (tập trung vào 3 con ngựa tiềm năng) kết hợp với tiêu chuẩn Kelly mang lại Tỷ suất hoàn vốn nội bộ (IRR) trung bình là 4,46% và MoM là 0,09x.

# Limitations

- Nghiên cứu bị giới hạn bởi dữ liệu công khai; các dữ liệu ẩn/độc quyền (như dữ liệu sinh trắc học) có thể mang lại lợi thế thông tin tốt hơn.
- Dù có lợi nhuận kỳ vọng dương, chiến lược này vẫn đối mặt với sự biến động lớn và rủi ro sụt giảm tài khoản cao (ví dụ: thử nghiệm thực tế từ tháng 1 đến tháng 3/2025 không mang lại lợi nhuận).
- Bộ tính năng tĩnh hiện tại có thể bỏ qua các chu kỳ phong độ và hiệu ứng động lượng (momentum) theo thời gian của ngựa.

# Relevance to our topic

- Bài báo chứng minh vai trò cực kỳ quan trọng của Nài ngựa (Jockey) trong việc dự đoán kết quả cuộc đua. Tác giả đã dành hẳn một bộ biến số riêng cho nài ngựa như: tổng số trận thắng, tỷ lệ thắng, số ngày nghỉ kể từ lần đua cuối, và phong độ gần nhất.
- Đáng chú ý, các biến số liên quan đến nài ngựa (ví dụ: Horse3_Jockey_Previous_Winner và Horse1_Jockey_Days_Since_Last_Race) đã lọt vào top 20 đặc trưng có mức độ đóng góp (Gain) cao nhất cho mô hình XGBoost. Điều này cung cấp cơ sở dữ liệu định lượng mạnh mẽ cho nhóm: sự thành bại không chỉ nằm ở con ngựa, mà nài ngựa (và sự phù hợp về phong độ, lịch sử thi đấu của họ) là yếu tố quyết định tạo nên chiến thắng.

# Possible improvement

- **Thiết lập các biến tương tác (Interaction Features):** Thay vì chỉ đánh giá thông số ngựa và thông số nài ngựa một cách độc lập như bài báo, nhóm có thể cải tiến bằng cách tạo ra các đặc trưng tương tác trực tiếp. Ví dụ: Tính toán "Tỷ lệ chiến thắng chung của cặp nài ngựa - ngựa này trong quá khứ", hoặc "Mức độ cải thiện thành tích của ngựa X khi được cưỡi bởi nài ngựa Y so với các nài ngựa khác".
- **Phân tích chuỗi thời gian (Temporal Modeling):** Như tác giả đã đề xuất ở phần tương lai, nhóm có thể sử dụng mô hình chuỗi thời gian để theo dõi xem "sự phù hợp" giữa một nài ngựa và một con ngựa tăng lên hay giảm đi qua từng giai đoạn huấn luyện và thi đấu.
