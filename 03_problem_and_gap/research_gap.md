# Khoảng trống nghiên cứu (Research Gap)

## 1. Tổng quan các nghiên cứu tiền đề (Literature Review)

Dự đoán kết quả đua ngựa là một bài toán kinh điển trong lý thuyết xác suất và khoa học dữ liệu thể thao. Qua khảo sát hệ thống tài liệu học thuật quốc tế, các hướng tiếp cận chính bao gồm:

- **Mô hình Logit đa biến (Multinomial Logit Model):** Hướng tiếp cận nền tảng được định hình bởi _Bolton & Chapman (1986)_ trong việc ước lượng xác suất thắng cuộc dựa trên các biến độc lập của thực thể tham gia.
- **Mô hình toán học nâng cao:** Hệ thống tính toán dựa trên xác suất có điều kiện và kỹ thuật hiệu chuẩn trọng số được phát triển toàn diện bởi _William Benter (1994)_ — công trình kinh điển chứng minh tính hiệu quả vượt trội của các hệ thống máy tính so với các chuyên gia phân tích truyền thống tại Hong Kong.
- **Học máy hiện đại (Modern Machine Learning):** Các nghiên cứu gần đây dịch chuyển mạnh mẽ sang cấu trúc phi tuyến tính như Mạng thần kinh nhân tạo (ANN), Rừng ngẫu nhiên (Random Forest), và đặc biệt là thuật toán tăng cường độ dốc **XGBoost** nhờ khả năng xử lý xuất sắc dữ liệu dạng bảng (Tabular Data) và các mối quan hệ tương tác phức tạp giữa các đặc trưng (Features).

## 2. Hạn chế của các nghiên cứu trước và Khoảng trống nghiên cứu

Mặc dù các mô hình dự đoán ngày càng đạt độ chính xác cao, việc rà soát tài liệu cho thấy tồn tại một **khoảng trống lớn (Research Gap)** giữa lý thuyết mô hình và thực tế vận hành:

| Hạn chế từ các nghiên cứu trước                                                                                                                                                                  | Hệ quả / Khoảng trống kỹ thuật                                                                                                                                                         |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tính cô lập của mô hình (Model Isolation):** Phần lớn nghiên cứu chỉ tập trung tối ưu thuật toán AI (độ chính xác, hàm mất mát) trên các tập dữ liệu tĩnh (Static Datasets) được đóng gói sẵn. | Thiếu một kiến trúc hệ thống hoàn chỉnh để đưa mô hình này vào môi trường vận hành thực tế (Production Environment) với dòng dữ liệu biến động liên tục.                               |
| **Bỏ sót các đối tượng tương tác (Stakeholder Neglect):** Các nghiên cứu thường phục vụ mục đích duy nhất là hỗ trợ người đặt cược hoặc các quỹ đầu tư tài chính đầu cơ.                         | Chưa có hệ thống nào bao quát và phân quyền đầy đủ cho toàn bộ các thực thể trong hệ sinh thái giải đấu bao gồm: Chủ ngựa, Nài ngựa, Trọng tài, và Ban tổ chức trên cùng một nền tảng. |
| **Đứt gãy quy trình nghiệp vụ (Business Process Disruption):** Các tính năng quản lý cốt lõi (Đăng ký, Phân lịch, Quản lý kết quả) bị tách rời hoàn toàn khỏi module dự đoán AI.                 | Người điều hành không thể khai thác dữ liệu dự báo để phân tích tính bất thường của giải đấu, còn khán giả phải sử dụng nhiều công cụ rời rạc để vừa cập nhật thông tin vừa phân tích. |

## 3. Giải pháp đề xuất và Đóng góp của đề tài

Để lấp đầy khoảng trống nghiên cứu trên, đề tài đề xuất phát triển một **Nền tảng Web quản lý giải đua ngựa toàn diện tích hợp Module AI (XGBoost)**.

Hệ thống sẽ đồng bộ hóa dòng dữ liệu từ khâu quản lý hành chính (vòng đời giải đấu, hồ sơ nài/ngựa), xử lý tài chính ảo (Ví điện tử, cá cược mô phỏng phục vụ nghiên cứu), cho đến công cụ phân tích nâng cao (Dashboard thống kê, dự báo xác suất AI).

**Đóng góp cụ thể của nghiên cứu:**

1.  **Đóng góp kiến trúc:** Thiết kế và triển khai một hệ thống hướng dịch vụ giải quyết bài toán tích hợp giữa phần mềm quản lý phân quyền đa vai trò và pipeline thực thi mô hình Học máy.
2.  **Đóng góp ứng dụng:** Ứng dụng thuật toán XGBoost để đưa ra dự báo xác suất dưới dạng phân phối (Probability Distribution) cho toàn bộ các cá thể tham gia trong một lượt đua, thay vì chỉ đưa ra dự đoán phân loại nhị phân (Thắng/Thua) đơn giản.
3.  **Đóng góp thực nghiệm:** Cung cấp môi trường mô phỏng (Sandbox) với ví điện tử và hệ thống cá cược ảo để kiểm chứng hành vi người dùng và tính hiệu quả của công cụ hỗ trợ quyết định bằng AI trong điều kiện thực tế.

## 4. Tài liệu tham khảo (References)

- Benter, W. (1994). Computer based horse race handicapping and betting systems. _Efficiency of Racetrack Betting Markets_, 183-198.
- Bolton, R. N., & Chapman, R. G. (1986). Searching for Positive Returns at the Track: A Multinomial Logit Model for Predicting Horse Race Outcomes. _Management Science_, 32(8), 1040-1060.
