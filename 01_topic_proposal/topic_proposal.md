# ĐỀ XUẤT ĐỀ TÀI

## 1. Thông tin nhóm

- Lớp: SE1820

- Nhóm: G03

- Nhóm trưởng: Châu Thành

- Thành viên:Chu Phúc Minh Vương,Trương Gia Bảo,La Quang Phụng,Võ Trường Thành Phát

---

# 2. Tên đề tài

### Tên tiếng Anh

**AI-Integrated Horse Racing Tournament Management System with Win Probability Prediction**

### Tên tiếng Việt

**Hệ thống quản lý giải đua ngựa tích hợp AI dự đoán xác suất chiến thắng**

---

# 3. Lĩnh vực ứng dụng

Đề tài thuộc các lĩnh vực:

- Trí tuệ nhân tạo (Artificial Intelligence)

- Hệ thống quản lý thể thao

- Hệ thống quản lý giải đấu

- Phân tích dữ liệu dự đoán

- Hệ thống cá cược ảo

Hệ thống hỗ trợ quản lý toàn bộ vòng đời của một giải đua ngựa từ đăng ký tham gia, quản lý ngựa và nài ngựa, tổ chức cuộc đua, quản lý kết quả, bảng xếp hạng đến dự đoán xác suất chiến thắng bằng AI và cá cược ảo.

---

# 4. Bài toán thực tế

Đua ngựa là một môn thể thao có nhiều bên tham gia như chủ ngựa, nài ngựa, trọng tài, ban tổ chức và khán giả.

Hiện nay việc quản lý giải đua ngựa còn gặp nhiều hạn chế:

### Các vấn đề chính

1. Việc đăng ký tham gia giải đấu, quản lý lịch thi đấu và công bố kết quả vẫn còn thực hiện thủ công.

2. Chủ ngựa và nài ngựa không có hệ thống tập trung để quản lý thông tin, lịch sử thi đấu và thành tích.

3. Ban tổ chức gặp khó khăn trong việc theo dõi số lượng đăng ký, xếp hạng và giải thưởng.

4. Khán giả không có công cụ hỗ trợ đánh giá khả năng chiến thắng của từng ngựa trước khi đặt cược.

5. Việc thống kê dữ liệu, doanh thu và kết quả thi đấu tốn nhiều thời gian và dễ xảy ra sai sót.

6. Hệ thống hiện tại chưa tận dụng dữ liệu lịch sử để hỗ trợ ra quyết định.

Do đó cần xây dựng một nền tảng quản lý giải đua ngựa hiện đại tích hợp AI để tăng hiệu quả quản lý, tính minh bạch và trải nghiệm người dùng.

---

# 5. Động lực thực hiện

Đề tài kết hợp nhiều kiến thức quan trọng trong lĩnh vực Công nghệ thông tin:

- Phát triển hệ thống Web/Mobile

- Quản lý dữ liệu lớn

- Phân quyền người dùng

- Trí tuệ nhân tạo

- Thanh toán điện tử

- Dashboard và Data Analytics

Hệ thống giúp:

- Tự động hóa quy trình quản lý giải đấu.

- Hỗ trợ khán giả đưa ra quyết định dựa trên dữ liệu.

- Cung cấp công cụ phân tích hiệu quả cho ban tổ chức.

- Ứng dụng AI vào một bài toán thực tế trong lĩnh vực thể thao.

---

# 6. Đối tượng sử dụng

## 1. Chủ ngựa (Horse Owner)

Chủ ngựa có thể:

- Đăng ký tài khoản

- Quản lý hồ sơ ngựa

- Thuê hoặc mời nài ngựa

- Đăng ký ngựa tham gia cuộc đua

- Theo dõi lịch sử thi đấu

- Theo dõi tiền thưởng

---

## 2. Nài ngựa (Jockey)

Nài ngựa có thể:

- Quản lý hồ sơ cá nhân

- Nhận hoặc từ chối lời mời

- Xem lịch thi đấu

- Theo dõi thành tích cá nhân

---

## 3. Trọng tài (Race Referee)

Trọng tài có thể:

- Kiểm tra điều kiện thi đấu

- Điểm danh ngựa trước cuộc đua

- Ghi nhận vi phạm

- Xác nhận kết quả thi đấu

- Lập biên bản cuộc đua

---

## 4. Khán giả (Spectator)

Khán giả có thể:

- Xem thông tin giải đấu

- Theo dõi lịch thi đấu

- Xem hồ sơ ngựa

- Xem hồ sơ nài ngựa

- Nạp tiền vào ví ảo

- Đặt cược ảo

- Xem dự đoán xác suất chiến thắng

---

## 5. Quản trị viên (Administrator)

Quản trị viên có thể:

- Quản lý tài khoản

- Quản lý giải đấu

- Quản lý cuộc đua

- Quản lý trọng tài

- Theo dõi giao dịch

- Theo dõi thống kê hệ thống

---

# 7. Mô hình AI đề xuất

Đề tài không xây dựng mô hình AI từ đầu mà sử dụng các thuật toán Machine Learning đã được chứng minh hiệu quả.

## 1. XGBoost

XGBoost được sử dụng để dự đoán xác suất chiến thắng của từng ngựa trong một cuộc đua.

### Dữ liệu đầu vào

- Tỷ lệ thắng của ngựa

- Số lần tham gia thi đấu

- Thành tích gần đây

- Điểm xếp hạng

- Tỷ lệ thắng của nài ngựa

- Thành tích của nài ngựa

- Đặc điểm cuộc đua

### Kết quả đầu ra

- Xác suất chiến thắng của từng ngựa

- Bảng xếp hạng dự đoán trước cuộc đua

---

## 2. Feature Engineering

Các đặc trưng được xây dựng từ dữ liệu lịch sử:

- Horse Win Rate

- Jockey Win Rate

- Average Finish Position

- Total Points

- Total Earnings

- Recent Form

- Number of Participated Races

---

## 3. Multinomial Logit Inspired Approach

Kết quả từ mô hình được chuẩn hóa bằng Softmax để tạo ra phân phối xác suất chiến thắng hợp lệ cho toàn bộ ngựa tham gia cuộc đua.

---

# 8. Chức năng hệ thống

## 1. Quản lý người dùng

- Đăng ký

- Đăng nhập

- Quên mật khẩu

- JWT Authentication

- Phân quyền theo vai trò

---

## 2. Quản lý ngựa

- Thêm ngựa

- Chỉnh sửa thông tin ngựa

- Quản lý giấy tờ chứng nhận

- Theo dõi lịch sử thi đấu

- Xem thành tích

---

## 3. Quản lý nài ngựa

- Quản lý hồ sơ

- Quản lý lời mời

- Theo dõi lịch sử thi đấu

- Xem thành tích

---

## 4. Quản lý giải đấu

- Tạo giải đấu

- Chỉnh sửa giải đấu

- Quản lý mùa giải

- Quản lý lịch thi đấu

---

## 5. Quản lý cuộc đua

- Tạo cuộc đua

- Thiết lập khoảng cách đua

- Thiết lập lệ phí tham gia

- Thiết lập giải thưởng

- Thiết lập số lượng ngựa tham gia

- Thiết lập điều kiện tham gia

---

## 6. Đăng ký tham gia cuộc đua

- Đăng ký ngựa

- Chọn nài ngựa

- Thanh toán lệ phí

- Hủy đăng ký

- Hoàn phí theo quy định

---

## 7. Chức năng trọng tài

- Kiểm tra điều kiện ngựa

- Điểm danh trước cuộc đua

- Ghi nhận vi phạm

- Loại ngựa không đủ điều kiện

- Xác nhận kết quả

- Xuất biên bản cuộc đua

---

## 8. Ví điện tử và thanh toán

- Nạp tiền

- Trừ tiền lệ phí

- Trừ tiền cược

- Hoàn tiền

- Lịch sử giao dịch

Tích hợp:

- Stripe Sandbox

- VNPay Sandbox (tùy chọn)

---

## 9. AI Dự đoán xác suất chiến thắng

Trước mỗi cuộc đua hệ thống hiển thị:

- Xác suất thắng của từng ngựa

- Bảng xếp hạng dự đoán

- Các chỉ số thống kê liên quan

---

## 10. Cá cược ảo

Các loại cược:

- Win (Về nhất)

- Place (Top 2)

- Show (Top 3)

Hệ thống tự động thanh toán kết quả cược sau khi trọng tài xác nhận kết quả cuộc đua.

---

## 11. Bảng xếp hạng

Xếp hạng:

- Ngựa

- Nài ngựa

- Chủ ngựa

Tiêu chí:

- Điểm tích lũy

- Số lần chiến thắng

- Tổng tiền thưởng

---

## 12. Dashboard và thống kê

Dashboard quản trị hiển thị:

- Tổng số người dùng

- Tổng số giải đấu

- Tổng số cuộc đua

- Tổng số lượt cược

- Doanh thu hệ thống

- Ngựa nổi bật

- Nài ngựa nổi bật

---

## 13. Hệ thống thông báo

- Cuộc đua sắp diễn ra

- Kết quả thi đấu

- Lời mời nài ngựa

- Kết quả cược

- Thông báo giải đấu

---

# 9. Đóng góp kỳ vọng

1. Xây dựng nền tảng quản lý giải đua ngựa hoàn chỉnh cho nhiều vai trò người dùng.

2. Tích hợp AI dự đoán xác suất chiến thắng dựa trên dữ liệu lịch sử.

3. Xây dựng hệ thống cá cược ảo minh bạch và tự động.

4. Tích hợp ví điện tử và thanh toán giả lập.

5. Hỗ trợ thống kê và báo cáo theo thời gian thực.

6. Ứng dụng thực tế Machine Learning vào lĩnh vực thể thao.

7. Tạo nền tảng có khả năng mở rộng cho các giải đấu thể thao khác trong tương lai.

---

# 10. Kế hoạch đánh giá

## Dữ liệu

- Hồ sơ ngựa

- Hồ sơ nài ngựa

- Kết quả cuộc đua

- Lịch sử thi đấu

- Dữ liệu đặt cược

- Dữ liệu giả lập phục vụ huấn luyện AI

---

## Baseline

- Dự đoán ngẫu nhiên

- Xếp hạng theo tỷ lệ thắng

- Xếp hạng theo điểm số

---

## Chỉ số đánh giá AI

### Prediction

- Accuracy

- Top-1 Accuracy

- Top-3 Accuracy

- Log Loss

- Brier Score

### Hiệu năng hệ thống

- API Response Time

- Throughput

- Concurrent Users

- Uptime

---

## Đánh giá chuyên gia

Giảng viên và chuyên gia đánh giá:

- Tính hợp lý của dự đoán

- Quy trình quản lý giải đấu

- Chất lượng hệ thống

---

## Khảo sát người dùng

Đánh giá:

- Dễ sử dụng

- Hữu ích của AI

- Độ tin cậy của dự đoán

- Mức độ hài lòng tổng thể

---

# 11. Các nghiên cứu liên quan

- Searching for Positive Returns at the Track

- Horse Racing Prediction at the Champ de Mars

- XGBoost: A Scalable Tree Boosting System

- Optimal Model of Horse Racing Competition Decision Management Based on Association Rules and Neural Network
