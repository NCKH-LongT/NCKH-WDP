# Citation

- **Title:** Influence of horse demographics, country of training and race distance on the rating of Thoroughbreds
- **Authors:** Eva Sobotková, Tomáš Kopec, Vladimír Mikule, and Dana Kuřitková
- **Year:** 2023
- **Source:** https://pmc.ncbi.nlm.nih.gov/articles/PMC10654610/pdf/aab-66-299-2023.pdf
- **DOI/Link:** https://doi.org/10.5194/aab-66-299-2023

# Problem

Bài báo giải quyết bài toán đánh giá mức độ ảnh hưởng của các yếu tố nhân khẩu học và môi trường (tuổi, giới tính, ngựa cha, quốc gia sinh ra, quốc gia huấn luyện và cự ly đua) đến xếp hạng hiệu suất thi đấu quốc tế của giống ngựa đua thuần chủng (Thoroughbreds).

# Method

- Sử dụng mô hình tuyến tính tổng quát (GLM - General Linear Model), một dạng tương tự như phân tích phương sai (ANOVA) với phân phối logarit chuẩn.
- Thực hiện phép biến đổi logarit đối với các giá trị xếp hạng ban đầu do biến phụ thuộc (rating) có độ lệch đáng kể so với phân phối chuẩn.
- Sử dụng kiểm định F (F test) để đánh giá mức độ ý nghĩa thống kê.
- Sử dụng kiểm định hậu định Scheffé (Scheffé's post hoc test) để tìm ra sự khác biệt cụ thể giữa các cặp giá trị trung bình của các nhóm.

# Dataset

- Dữ liệu xếp hạng hiệu suất của 6.216 con ngựa đua xuất sắc nhất thế giới. Dữ liệu này chỉ giới hạn ở những con ngựa đạt rating từ 115 trở lên.
- Nguồn dữ liệu được trích xuất từ cơ sở dữ liệu LONGINES World's Best Racehorse của Liên đoàn Cơ quan Đua ngựa Quốc tế (IFHA) trong khoảng thời gian từ năm 2004 đến 2022.
- Các thông tin về gia phả ngựa được thu thập và đối chiếu bổ sung từ Pedigree Online's Thoroughbred Database.

# Evaluation

- Metric đánh giá trung tâm của bài báo là Rating (điểm xếp hạng) do các quan chức và chuyên gia (handicappers) của IFHA thiết lập dựa trên phong độ thực tế của ngựa qua các giải đấu quốc tế.
- Mức điểm rating trung bình của tập dữ liệu này là 117,57, độ lệch chuẩn 3,0458, với mức điểm thấp nhất là 115 và cao nhất là 141.
- Mức độ ý nghĩa thống kê được xác định thông qua giá trị P-value ($p<0.05$, $p<0.01$, $p<0.001$).

# Results

- Toàn bộ 6 yếu tố được khảo sát đều có tác động thống kê đáng kể ($p<0.001$) đến xếp hạng của ngựa.
- **Giới tính:** Ngựa đực (Stallions) đạt rating vượt trội đáng kể (117,85) so với ngựa thiến (117,17) và ngựa cái (117,13). Không có sự khác biệt rõ rệt về hiệu suất giữa ngựa cái và ngựa thiến.
- **Tuổi:** Hơn một nửa số ngựa ưu tú trên thế giới tập trung ở độ tuổi 3-4 tuổi (54,68%). Nhóm tuổi này cũng mang lại kết quả thi đấu tốt nhất (rating 117,80 và 117,74), sau đó phong độ có xu hướng suy giảm rõ rệt ở những con ngựa từ 6 tuổi trở lên.
- **Quốc gia:** Mỹ (USA) dẫn đầu về số lượng ngựa sinh ra (25,92%) và số lượng ngựa được huấn luyện (24,87%). Thế nhưng, xét về chất lượng, ngựa sinh ra và được huấn luyện tại Ireland (IRE) lại đạt điểm trung bình cao nhất (lần lượt là 117,99 và 118,80).
- **Cự ly:** Ngựa thi đấu ở cự ly trung bình (Intermediate) và cự ly dài (Long) đạt điểm rating cao nhất (118,06 và 117,86).
- **Di truyền (Sire):** Galileo (IRE) là con ngựa cha vĩ đại nhất khi có tới 193 hậu duệ lọt vào cơ sở dữ liệu của IFHA. Dòng máu của Sadler's Wells và Mr. Prospector tỏ ra cực kỳ thành công, chiếm phần lớn trong danh sách những ngựa cha tốt nhất.

# Limitations

- Dữ liệu thi đấu thu thập trong hai năm 2020 và 2021 có thể bị sai lệch hoặc nhiễu do ảnh hưởng của đại dịch Covid-19 toàn cầu.
- Nghiên cứu này mới chỉ đánh giá sự ảnh hưởng từ phía ngựa cha (sire) mà chưa tính đến tác động hoặc yếu tố di truyền từ ngựa mẹ (dam).
- Bài báo đã dự định thực hiện phân tích phương sai đa yếu tố kết hợp tương tác chéo (interactions) giữa các biến, tuy nhiên thao tác này không thể đánh giá khách quan do thiếu dữ liệu trầm trọng ở một số cấp độ tương tác.
- Tập dữ liệu chọn lọc khắt khe (chỉ lấy ngựa đạt top rating $\ge$ 115) nên các phát hiện này không đại diện hoặc có thể không đúng với toàn bộ quần thể ngựa đua thuần chủng thông thường.

# Relevance to our topic

Bài báo cung cấp các đặc trưng (features) cốt lõi cực kỳ quan trọng cho bài toán mô hình hóa thể thao: giới tính, độ tuổi, cự ly chuyên môn, quốc gia và dòng máu. Nếu nhóm bạn đang xây dựng các mô hình dữ liệu (như học máy) để phân tích trận đấu hay dự báo kết quả, nghiên cứu này xác nhận tính khả thi của việc dựa vào các thông số nhân khẩu học và di truyền để dự đoán phong độ thi đấu (rating).

# Possible improvement

- **Tích hợp yếu tố môi trường (Track Surface/Condition):** Đưa thêm biến số "điều kiện mặt sân" (Turf/Dirt/Synthetic hoặc Khô/Bùn lầy) vào bộ dữ liệu, vì đây là những yếu tố phân hóa phong độ thi đấu rất rõ rệt nhưng lại hoàn toàn vắng bóng trong bài báo này.
- **Feature Engineering mở rộng:** Bổ sung việc phân tích di truyền nhánh mẹ (broodmare sire) thay vì chỉ đánh giá trên ngựa cha.
- **Áp dụng Machine Learning (Học máy):** Vượt qua rào cản của phân tích thống kê truyền thống (GLM/ANOVA) bằng cách sử dụng các mô hình phi tuyến tính mạnh mẽ hơn như Random Forest hoặc Gradient Boosting (XGBoost, LightGBM). Các mô hình này có khả năng tự động nắm bắt các tương tác phức tạp đa biến (ví dụ: ngựa cái + tuổi cao + cự ly ngắn) mà phương pháp truyền thống trong bài báo đã bó tay do thiếu hụt điểm dữ liệu giao thoa.
- **Kết hợp thông số kỵ sĩ (Jockeys):** Kết hợp các thông số hiệu suất kỵ sĩ (đặc biệt là hệ thống Apprentice Jockeys/Weight Claims từ bài báo trước) cùng với các tính năng của ngựa trong bài này để xây dựng một mô hình đánh giá toàn diện.
