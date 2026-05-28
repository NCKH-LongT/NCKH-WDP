# Citation

- **Title:** Optimizing Horse Racing Predictions through Ensemble Learning and Automated Betting Systems
- **Authors:** Nguyen Quoc Khanh, Nguyen Phuoc Sang, Tran Thi My Quyen, Vu Anh Tran
- **Year:** 2024
- **Source:** Ventus Group & Think Prompt
- **DOI/Link:** (PDF) Optimizing Horse Racing Predictions through Ensemble Learning and Automated Betting Systems

# Problem

Bài báo giải quyết các vấn đề sau:

- Dự đoán kết quả đua ngựa là một bài toán cực kỳ thách thức do có quá nhiều yếu tố biến động cùng tác động.
- Sự bùng nổ về khối lượng và độ phức tạp của dữ liệu đua ngựa trong kỷ nguyên số đặt ra yêu cầu phải có các phương pháp phân tích tiên tiến hơn.
- Các mô hình dự đoán truyền thống bộc lộ rõ sự yếu kém khi thường xuyên cho độ chính xác thấp và gặp lỗi cấu trúc trong thiết kế hệ thống.

# Method

Tác giả đã phát triển một hệ thống học máy sử dụng cấu trúc xếp chồng phân tầng (Stacked Ensemble Model) kết hợp nhiều thuật toán:

- **6 thuật toán nền tảng (Base Models):** Bao gồm LightGBM, XGBoost, CatBoostRegressor, HistGradientBoosting Regressor, AdaBoostRegressor, và TabNetRegressor (mô hình học sâu ứng dụng cơ chế chú ý dành riêng cho dữ liệu bảng).
- **Mô hình siêu cấp (Meta-Model):** Sử dụng thuật toán XGBoost để tổng hợp các kết quả đầu ra từ mô hình nền tảng nhằm đưa ra dự đoán cuối cùng và giảm thiểu sai số.
- **Kỹ nghệ đặc trưng (Feature Engineering):** Tính toán các chỉ số hiệu suất cuốn (rolling performance) của 5 trận gần nhất, chỉ số phong độ độc quyền (form index), và đặc biệt là sự kết hợp cặp bài trùng giữa Huấn luyện viên & Nài ngựa (trainer and jockey pairs).
- **Lựa chọn đặc trưng:** Áp dụng các kiểm định thống kê (Chi-square, ANOVA), giảm chiều dữ liệu PCA, và các phương pháp Lasso/Ridge để loại bỏ nhiễu dữ liệu.
- **Phân chia dữ liệu:** Chia tập dữ liệu theo trình tự thời gian (Chronological Split) với tỷ lệ 80% để huấn luyện và 20% để kiểm thử nhằm ngăn chặn hiện tượng rò rỉ dữ liệu.

# Dataset

Nghiên cứu sử dụng tập dữ liệu về các cuộc đua phẳng (flat races) tại hai thị trường lớn:

- **Úc (AUS):** Giai đoạn 2015–2024, lấy từ nền tảng Punters.com.au.
- **Vương quốc Anh & Ireland (UK):** Giai đoạn 2021–2023, lấy từ attheraces.com và racingbetdata.com.
- Cơ sở dữ liệu cốt lõi (Root Database) lưu trữ lũy tiến hơn 10 triệu bản ghi chi tiết về lịch sử của ngựa, nài ngựa và huấn luyện viên.
- Các thuộc tính dữ liệu bao gồm: thông tin sân đua, điều kiện mặt sân, thông tin nài ngựa, huấn luyện viên, cân nặng cõng (weightLb), tuổi ngựa (Age), điểm phong độ lịch sử (OR/RPRC/TRC) và tỷ lệ cược thập phân (Decimal price).

# Evaluation

Hệ thống được đánh giá song song qua hai khía cạnh độc lập:

- **Chỉ số kỹ thuật học máy:** Sử dụng Độ chính xác (Accuracy), F1-Score, biểu đồ đường cong ROC và chỉ số diện tích dưới đường cong AUC.
- **Chỉ số hiệu quả tài chính:** Sử dụng tỷ suất sinh lời (ROI %) để đánh giá thực tế thông qua việc thử nghiệm giả lập đặt cược từ ngày 01/06/2024 đến 30/09/2024 trên các chiến lược cược khác nhau.

# Results

- **Về mặt thuật toán:** Chiến lược chọn nhóm Top 3 đầu ra của mô hình (Top 3 Model Output) mang lại hiệu suất phân loại tốt nhất với chỉ số AUC vượt mức 0.65 ở cả hai thị trường.
- **Về mặt lợi nhuận thực tế:**
  - Việc đặt cược vào các con ngựa được yêu thích nhất (odds thấp từ 1 đến 2) mặc dù có độ chính xác cao nhưng luôn dẫn đến lợi nhuận ròng âm (thua lỗ).
  - Ngược lại, chiến lược Tối ưu ROI cho ngựa cửa dưới (Optimize ROI for Underdogs) do AI đề xuất mang lại hiệu quả sinh lời vượt trội nhất với ROI dương đạt +23.98% tại thị trường Úc và +20.94% tại thị trường Anh.

# Limitations

- Nếu hệ thống chỉ tập trung duy nhất vào một mục tiêu đơn lẻ là tối đa hóa ROI hoặc tối đa hóa độ chính xác (Optimize ROI / Optimize Precision) mà không có sự linh hoạt, hiệu suất thuật toán sẽ bị sụt giảm nghiêm trọng và tiệm cận mức đoán mò ngẫu nhiên (chỉ số AUC chỉ đạt quanh mức 0.49 - 0.50).
- Độ tin cậy của các dự đoán đơn lẻ (Top 1) vẫn còn biến động lớn tùy thuộc vào đặc thù môi trường đua riêng biệt của từng khu vực địa lý.

# Relevance to our topic

- Bài nghiên cứu này cung cấp một sơ đồ kiến trúc hệ thống thực tế (System Pipeline) hoàn chỉnh cho dự án web của nhóm: Từ khâu thu thập dữ liệu lớn (10M+ bản ghi) -> Xử lý qua mô hình AI xếp chồng -> Xuất kết quả trực quan ra giao diện web theo thời gian thực cho người dùng.
- Chứng minh bằng số liệu thực nghiệm rằng việc đưa sự kết hợp thông số giữa Nài ngựa và Huấn luyện viên (trainer and jockey pairs) vào làm đặc trưng dữ liệu đầu vào là cực kỳ quan trọng để cải thiện độ chính xác cho AI.

# Possible improvement

- **Tích hợp Dữ liệu Sinh học thực thời (Bio-data):** Vì hệ thống hiện tại hoàn toàn sử dụng dữ liệu thống kê lịch sử và tỷ lệ cược, nhóm có thể đề xuất tích hợp thêm các chỉ số sinh học thực tế của ngựa (nhịp tim, tần số sải chân) để tối ưu hóa năng lực học của mô hình học sâu TabNet.
- **Cập nhật Trọng số Meta-Model động:** Đề xuất xây dựng cơ chế học trực tuyến (Online Learning), cho phép mô hình siêu cấp XGBoost tự động điều chỉnh và tinh chỉnh lại trọng số phối hợp giữa 6 mô hình nền tảng ngay khi có sự thay đổi đột ngột về thời tiết hoặc biến động nài ngựa sát giờ đua.
