# Citation

- **Title:** Hierarchical Bayesian analysis of racehorse running ability and jockey skills.
- **Authors:** Nakakita, M., Nakatsuma, T..
- **Year:** 2023.
- **Source:** International Journal of Computer Science in Sport.
- **DOI/Link:** (PDF) Hierarchical Bayesian analysis of racehorse running ability and jockey skills

# Problem

Bài báo đề xuất một phương pháp đánh giá định lượng năng lực chạy của ngựa đua và kỹ năng của nài ngựa.
Vấn đề chính là làm thế nào để ước lượng đồng thời các hiệu ứng cá nhân không quan sát được (unobservable individual effects) của ngựa và nài ngựa cùng với các biến số giải thích khác, dựa trên dữ liệu mảng không cân bằng (unbalanced panel data - do số lần thi đấu của mỗi cá thể là khác biệt).

# Method

- Nhóm tác giả sử dụng mô hình Bayes phân cấp (Hierarchical Bayesian model) để ước lượng ổn định một lượng lớn các hiệu ứng cá nhân.
- Phương pháp Markov chain Monte Carlo (MCMC) được áp dụng kết hợp với Chiến lược đan xen Tính phụ trợ - Tính đủ (Ancillarity-Sufficiency Interweaving Strategy - ASIS) nhằm khắc phục tình trạng lấy mẫu kém hiệu quả và giúp mô hình hội tụ tốt hơn.

# Dataset

- Nghiên cứu sử dụng dữ liệu từ các cuộc đua cự ly 1.800 mét (không bao gồm đua vượt rào) do Hiệp hội Đua ngựa Nhật Bản (JRA) tổ chức trong khoảng thời gian từ năm 2016 đến 2018.
- Tập dữ liệu đưa vào phân tích sau khi đã làm sạch (loại bỏ dữ liệu ngoại lai và các cá thể thi đấu quá ít) bao gồm 22.183 kỷ lục cuộc đua của 4.063 con ngựa và 140 nài ngựa.

# Evaluation

- Tiêu chuẩn Thông tin Ứng dụng Rộng rãi (Widely Applicable Information Criterion - WAIC) được sử dụng làm thước đo để lựa chọn cấu hình biến số giải thích tối ưu nhất cho mô hình.
- Độ chính xác dự đoán của mô hình được đánh giá thông qua việc chia ngẫu nhiên 90% dữ liệu để huấn luyện và dùng 10% dữ liệu còn lại (2.218 lượt chạy) để đối chiếu tốc độ dự đoán với tốc độ thực tế.

# Results

- Việc ứng dụng thuật toán ASIS đã giúp giảm mức độ tự tương quan của dữ liệu, cải thiện đáng kể tốc độ lấy mẫu và giúp mô hình hội tụ thành công.
- Nghiên cứu phát hiện ra sự chênh lệch rất lớn về năng lực cá nhân giữa các con ngựa và nài ngựa. Chênh lệch kỹ năng giữa nài ngựa xuất sắc nhất và kém nhất có thể tạo ra khoảng cách chênh lệch tối đa lên tới 12,6 mét tại vạch đích.
- Đối với ngựa đua, sự khác biệt năng lực giữa con tốt nhất và kém nhất có thể tạo ra khoảng cách tối đa 47,7 mét. Năng lực chạy của ngựa đua có xu hướng tăng và bắt đầu suy giảm từ mốc 4,18 tuổi.

# Limitations

- Nhằm mục đích đơn giản hóa mô hình, nghiên cứu đã chủ ý loại bỏ biến số tương tác giữa hiệu ứng cá nhân của nài ngựa và hiệu ứng cá nhân của ngựa đua (tức là bỏ qua việc xem xét sự ăn ý/phù hợp giữa nài ngựa và con ngựa).
- Mô hình giả định rằng việc ngựa ngừng thi đấu là diễn ra ngẫu nhiên và độc lập, thay vì sử dụng một mô hình thời gian sống sót (survival time model) phức tạp hơn để xử lý việc thiếu hụt dữ liệu.

# Relevance to our topic

Bài báo cung cấp bằng chứng định lượng mạnh mẽ chứng minh rằng kỹ năng độc lập của nài ngựa có thể thay đổi cục diện cuộc đua rất lớn (khoảng cách 12,6 mét). Điều này khẳng định sự dẫn dắt của nài ngựa đóng vai trò trọng yếu trong thể thao đua ngựa, qua đó tạo cơ sở để lập luận rằng việc thiết lập sự phù hợp (matching) giữa nài ngựa giỏi và ngựa đua là cần thiết để tối ưu hóa những khoảng cách này.

# Possible improvement

Nhóm có thể cải tiến trực tiếp từ giới hạn của nghiên cứu này bằng cách bổ sung thêm một "biến tương tác" (interaction term) giữa nài ngựa và ngựa đua vào các mô hình học máy. Biến số này sẽ giúp đo lường định lượng xem sự tương thích, ăn ý khi ghép cặp có khả năng tạo ra bước nhảy vọt về tốc độ so với việc chỉ cộng dồn năng lực của hai bên hay không.
