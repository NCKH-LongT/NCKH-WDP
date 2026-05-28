# Citation
* **Title:** Apprentice Jockeys Revisited
* **Authors:** David Renham
* **Year:** 2022 (August 24, 2022)
* **Source:** https://www.oncourseprofits.com/apprentice-jockeys-revisited/
* **DOI/Link:** https://www.oncourseprofits.com/apprentice-jockeys-revisited/

# Problem
Bài báo giải quyết vấn đề đánh giá hiệu quả thực tế và khả năng sinh lời (dành cho người cá cược) khi đặt cược vào các kỵ sĩ học việc (apprentice jockeys) trong các cuộc đua ngựa phẳng (flat racing) tại Vương quốc Anh. Cụ thể, bài báo xem xét liệu mức tạ được giảm (3lbs, 5lbs, 7lbs) và các loại hình cuộc đua khác nhau (đặc biệt là Handicap) có thực sự mang lại lợi thế hay không.

# Method
Bài báo dùng phương pháp phân tích thống kê mô tả (Descriptive Statistics) dựa trên dữ liệu lịch sử. Tác giả tổng hợp, phân loại chéo (cross-tabulation) và so sánh các chỉ số về tỷ lệ thắng và mức độ sinh lời/thua lỗ theo từng mức trọng lượng được giảm (Claim) và từng loại hình cuộc đua (Race Type: Claimer, Seller, Maiden, Novices, Handicap). Lợi nhuận/Lỗ được tính dựa trên tỷ lệ cược xuất phát của Betfair (Betfair SP) sau khi đã trừ 5% hoa hồng.

# Dataset
Dữ liệu lịch sử đua ngựa phẳng của Anh (bao gồm cả đua trên cỏ và sân nhân tạo) trong 5 mùa giải trọn vẹn (2017 – 2021) ở các cuộc đua mở (open races). Tổng quan bộ dữ liệu gồm 52.659 lượt chạy (Runs) và 4.655 chiến thắng (Wins).

# Evaluation
Bài báo đánh giá bằng các metric:
* **Strike Rate (%):** Tỷ lệ thắng (Wins / Runs).
* **Profit / Loss:** Tổng số tiền lời/lỗ tính bằng bảng Anh (£).
* **ROI (%):** Tỷ suất hoàn vốn (Return on Investment).

# Results
Kết quả chính cho thấy việc đặt cược vào kỵ sĩ học việc nhìn chung không mang lại lợi nhuận:
* Trung bình, tỷ lệ thắng (Strike Rate) chỉ là 8.80% (khoảng 1/11 lượt đua) với mức ROI âm 11.40% (lỗ hơn 11 xu cho mỗi bảng Anh đặt cược).
* Mức trọng lượng được giảm (3lbs, 5lbs, 7lbs) gần như không tạo ra sự khác biệt về ROI (đều dao động từ lỗ 10.60% đến 12.50%).
* Kỵ sĩ học việc được sử dụng chủ yếu trong các cuộc đua Handicap (42.583 lượt chạy), với Strike Rate 9.20% nhưng ROI vẫn âm (-11.50%).
* Các cuộc đua loại "Maiden" là tệ nhất khi sử dụng kỵ sĩ học việc (Strike Rate cực thấp: 6.50%, ROI âm nặng nhất: -25.90%).

# Limitations
* Phân tích chỉ dừng ở mức thống kê tổng thể và tính trung bình, chưa đi sâu vào việc phân tách các yếu tố ngữ cảnh khác như: phong độ của ngựa, sự kết hợp giữa kỵ sĩ và huấn luyện viên cụ thể, hay điều kiện thời tiết/đường đua.
* Chưa chỉ ra được các "ngách" (niche) thực sự có lời (phần này bị ẩn sau paywall/bản Gold của trang web).

# Relevance to our topic
(Phần này phụ thuộc vào hướng đi cụ thể của nhóm bạn). Nhìn chung, bài báo cung cấp nền tảng kiến thức thực tế về hệ thống "Handicap" và "Weight Claim" trong thể thao. Nếu đề tài của nhóm liên quan đến phân tích dữ liệu thể thao, dự đoán tỷ lệ cược (betting models), hoặc tối ưu hóa thuật toán bù trừ (handicap/compensation systems), bài báo này chứng minh rằng các quy tắc bù trừ vật lý (giảm tạ) đôi khi không đủ để bù đắp cho kỹ năng thực tế của con người, dẫn đến chỉ số ROI vẫn âm.

# Possible improvement
* **Phân tích đa biến (Multivariate Analysis) hoặc Machine Learning:** Nhóm có thể thu thập thêm dữ liệu từ bài toán này và áp dụng các mô hình học máy (như Random Forest, XGBoost) để tìm ra những pattern ẩn. Ví dụ: kỵ sĩ học việc được giảm 7lbs cỡi một con ngựa mạnh nhưng chạy trên địa hình lầy lội thì tỷ lệ thắng thay đổi thế nào.
* **Tối ưu hóa chiến lược (Strategy Optimization):** Thay vì đánh giá chung toàn bộ, có thể phân cụm (clustering) các kỵ sĩ học việc có tiềm năng cao nhất để xem liệu có một nhóm nhỏ nào đó thực sự tạo ra ROI dương hay không.
