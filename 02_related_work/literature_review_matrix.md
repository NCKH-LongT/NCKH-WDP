# Literature Review Matrix

**Topic:** Nghiên cứu phương pháp luận tối ưu hóa tổ hợp, học máy dự đoán thứ hạng và kiến trúc phân tầng xử lý dữ liệu thời gian thực ứng dụng trong hệ thống **Quản lý giải đua ngựa (Horse Racing Tournament Management System)**.

| STT | Bài báo / Tác giả | Năm / Nguồn | Lĩnh vực | Vấn đề nghiên cứu | AI / Phương pháp | Dataset / Context | Metrics | Đóng góp cho dự án | Hạn chế | Relevance |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 01 | Mu-Chun Su et al. | 2025 / IJITDM | Scheduling | Lập lịch giải đấu nhiều ràng buộc | GA (POX-Heuristic) | Giải đấu giả lập | Xung đột = 0; Fitness | Thuật toán lõi lập lịch thi đấu | Chưa tính thời tiết cực đoan | Core / Algorithm |
| 02 | Elnaz Davoodi et al. | 2010 / WSEAS | Prediction | Dự đoán kết quả phi tuyến | ANN (MLP) | Đua ngựa Iran, Châu Á | MSE; Accuracy Top 1-3 | Dự báo thời gian về đích | Nhạy cảm dữ liệu nhiễu | Supporting / AI |
| 03 | Yubin So et al. | 2025 / JKSCI | Learning-to-Rank | Dự đoán thứ hạng Top-k | CatBoost / XGBoost Ranker | Đua ngựa Hàn Quốc (KRA) | NDCG; MAP; MRR | Xếp hạng Top 3/5 chiến mã | Cold Start ngựa mới | Core / AI |
| 04 | NYC Data Science | 2023 / Blog | Data Pipeline | Pipeline dữ liệu | Random Forest / XGBoost | Hồng Kông (HKJC) | Log Loss; ROC-AUC; F1 | Pipeline ETL trích xuất đặc trưng | Batch, chưa Streaming | High / Impl |
| 05 | Eva Sobotková et al. | 2023 / Acta Agr | Domain Analytics | Yếu tố sinh học ảnh hưởng thành tích | ANOVA; GLM | Thoroughbred (Séc) | P-value; R-squared | Tiêu chí Feature Engineering | Không dự đoán AI | Domain / FE |
| 06 | ZhiGuo Zhu | 2025 / PeerJ | Architecture | Kiến trúc streaming | WSN / Mạng Nơ-ron | Cảm biến sinh học | Throughput; Latency | Kiến trúc phân tầng 7 lớp | Chi phí WSN cao | High / Design |
| 07 | William Benter | 1994 / World Sci | Betting Strategy | Phong độ + tỷ lệ thị trường | Multinomial Logit | Cá cược HK lịch sử | Info Coefficient; R² | Lai ghép AI + đám đông | Mô hình tĩnh | Supporting |
| 08 | Graham Kendall et al. | 2010 / Comp & OR | Theory | Điều kiện biên lập lịch | Constraint Logic | Giải thể thao chuyên nghiệp | Vi phạm ràng buộc mềm | Khung lý thuyết cứng/mềm | Thiếu source code | Supporting |
| 09 | Faten K. Karim et al. | 2025 / THERMAL | Optimization | Tối ưu hạ tầng cloud | Horse Herd Optimization | Mô phỏng đám mây | Makespan; Utilization | Tối ưu hạ tầng, giảm trễ | HHO phức tạp | Supporting |
| 10 | Shuang Zhang | 2022 / Sci Prog | Decision Mgmt | Quản lý quyết định vận hành | Web App (B/S) + BPNN | CSDL trường đua | Response Time; Accuracy | Kiến trúc Web đa tác nhân | Thuật toán cũ | High / Web |

---

## Kết luận: Nghiên cứu Khoa học & Đóng góp của Dự án

### 1. Research Gap (Khoảng trống nghiên cứu)

Các nghiên cứu hiện tại về quản lý giải đua ngựa hoặc AI dự đoán thường tồn tại dưới dạng các module rời rạc, chưa có sự kết nối chặt chẽ:

* **Thiếu tính đồng bộ:** Các mô hình dự đoán (bài 02, 03, 07) tập trung vào bài toán toán học thuần túy, tách rời khỏi quy trình nghiệp vụ thực tế.
* **Quy trình vận hành lạc hậu:** Các hệ thống quản lý thể thao hiện đại (bài 06, 10) đã áp dụng kiến trúc tiên tiến, nhưng phần lớn trường đua vẫn vận hành thủ công.
* **Thách thức lập lịch:** Chưa có giải pháp nào kết hợp ràng buộc logic (Hard/Soft Constraints - bài 08) với thuật toán tối ưu hóa động (POX-Heuristic GA - bài 01) trong thời gian thực.

### 2. Đóng góp của dự án (Our Contributions)

Hệ thống được thiết kế để lấp đầy các khoảng trống trên bằng một giải pháp tích hợp toàn diện (All-in-one platform):

* **Tối ưu hóa Vận hành:** Áp dụng **POX-Heuristic GA** để tự động hóa lập lịch, đảm bảo công bằng và an toàn sức khỏe ngựa (Bài 01 & 08).
* **Hỗ trợ Ra quyết định:** Module Admin dựa trên kiến trúc B/S (Bài 10), tích hợp logic phân công trọng tài thông minh.
* **Trải nghiệm Dự đoán thông minh:** Tích hợp **Learning-to-Rank** và **Ensemble Learning** (Bài 03, 04) dự đoán Top-k. Cung cấp "AI + Crowd Prediction Matrix" (Bài 07).
* **Tiêu chuẩn hóa Dữ liệu:** Database Schema dựa trên yếu tố ảnh hưởng thành tích ngựa (Bài 05).

**Tổng kết:** Dự án là một hệ sinh thái thông minh kết hợp tối ưu hóa tổ hợp và học máy để hiện đại hóa toàn diện quy trình vận hành giải đua ngựa.
