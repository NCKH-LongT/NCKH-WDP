# Luồng Dữ liệu

## 1. Luồng Thiết lập Cuộc thi

```
Quản trị viên đăng nhập
  → Tạo cuộc thi:
      - Tên, mô tả
      - Mốc timeline (mở/đóng đăng ký, deadline nộp, ngày chung kết)
      - Số bảng (ví dụ: 3)
      - Chủ đề mỗi bảng (Google Drive link hoặc văn bản)
  → Backend lưu vào DB, đặt mốc cho Timeline Agent
  → Form đăng ký được MỞ công khai
```

## 2. Luồng Đăng ký Đội thi

```
Trưởng nhóm truy cập form đăng ký (URL công khai)
  → Điền: tên đội, mô tả dự án, tên + email thành viên
  → Gửi form
  → Backend:
      1. Tạo bản ghi đội trong DB (trạng thái: CHỜ XÁC NHẬN)
      2. Gửi email xác nhận đến TẤT CẢ thành viên
      3. Mỗi thành viên click link xác nhận
      4. Sau khi tất cả xác nhận: trạng thái đội → ĐÃ XÁC NHẬN
  → Số đội được theo dõi; đăng ký đóng vào deadline
```

## 3. Luồng Chia Bảng Tự động

```
Timeline Agent kích hoạt mốc DONG_DANG_KY
  → Backend:
      1. Truy vấn tất cả đội ĐÃ XÁC NHẬN
      2. Phân phối đội đều vào các bảng (ví dụ: 30 đội → 3 bảng × 10 đội)
         Thuật toán: round-robin hoặc phân tầng ngẫu nhiên
      3. Gán chủ đề bảng cho mỗi đội
      4. Cập nhật bản ghi đội với thông tin bảng thi
  → Cổng thông tin thí sinh cập nhật:
      - Mỗi đội thấy bảng, chủ đề và deadline nộp bài
      - Đồng hồ đếm ngược bắt đầu
```

## 4. Luồng Sinh Email AI (Kích hoạt bởi Mốc)

```
Timeline Agent kích hoạt mốc EMAIL (hoặc admin kích hoạt thủ công)
  → Backend chuẩn bị đối tượng ngữ cảnh:
      {
        loai_email: "CHUNG_KET" | "NHAC" | "CHUA_NOP" | "PHAN_CONG_MENTOR",
        ten_cuoc_thi: "...",
        ten_doi: "...",
        [các trường bổ sung theo loại]
      }
  → Backend gọi AI Service: POST /sinh-email
  → AI Service:
      1. Nạp mẫu prompt theo loai_email
      2. Chèn biến ngữ cảnh vào prompt
      3. Gọi LLM API (Gemini Flash hoặc GPT-4o-mini)
      4. Kiểm tra đầu ra (độ dài, định dạng, không có placeholder)
      5. Trả về { tieu_de, noi_dung }
  → Backend lưu bản nháp email vào DB
  → Nếu can_kiem_tra_admin = true:
      Admin xem và duyệt trong dashboard → Email Service gửi
  → Ngược lại (chế độ tự động gửi):
      Email Service gửi ngay lập tức
  → Trạng thái giao hàng cập nhật vào DB
```

## 5. Luồng Dữ liệu Cổng thông tin Thí sinh

```
Thí sinh đăng nhập qua Google OAuth (Gmail)
  → Backend xác minh email đối chiếu danh sách thành viên đội
  → Frontend nhận JWT token
  → Frontend lấy:
      - Thông tin đội (tên, thành viên)
      - Thông tin bảng thi (tên bảng, chủ đề, Google Drive link)
      - Timeline cuộc thi (ngày bắt đầu, deadline nộp)
      - Đồng hồ đếm ngược (tính từ deadline - thời_gian_hiện_tại)
      - Lịch sử thông báo (email đã nhận)
  → Tất cả dữ liệu: CHỈ ĐỌC cho thí sinh
  → Link cổng nộp bài hiển thị (nếu trong cửa sổ nộp bài và cổng đang MỞ)
```

## 6. Luồng Phân công Mentor & Xác thực

```
Admin phân công mentor cho bảng:
  → Admin chọn bảng + nhập email FPT của mentor
  → Backend xác minh domain email FPT (@fpt.edu.vn)
  → Tạo bản ghi mentor trong DB với phân công bảng
  → Bộ sinh Email AI được kích hoạt: email PHAN_CONG_MENTOR
      → Mentor nhận email với thông tin bảng, danh sách đội, deadline chấm
  → Mentor đăng nhập qua Google OAuth (phải dùng email FPT)
  → Giao diện giám khảo mở khóa: hiển thị bảng + đội được phân công
```

## 7. Luồng Chấm điểm và Sinh Câu hỏi AI

```
Giám khảo chọn đội để chấm:
  → Gửi: văn bản review (bắt buộc) + điểm từng tiêu chí rubric + điểm tổng
  → Backend lưu review + điểm vào DB
  → Backend đánh dấu đội là ĐÃ CHẤM cho giám khảo này
  → Backend kích hoạt AI Service bất đồng bộ:
      POST /sinh-cau-hoi {van_ban_review, rubric, mo_ta_du_an}
  → AI Service:
      1. Gửi review + rubric đến LLM (Gemini Pro / GPT-4)
      2. LLM trả về 5–7 câu hỏi định dạng JSON
      3. Hậu xử lý: loại trùng lặp, sắp xếp theo rubric
      4. Lưu câu hỏi đã tạo vào DB
  → Giao diện giám khảo cập nhật:
      Thông báo "Câu hỏi phỏng vấn đã sẵn sàng"
      Câu hỏi hiển thị trong phần có thể mở rộng

Theo dõi tiến độ:
  → Dashboard hiển thị: X / N đội đã chấm mỗi giám khảo
  → Admin xem: tiến độ tất cả giám khảo (ví dụ: GK A: 5/10, GK B: 3/10)
  → Tất cả điểm phải nộp đầy đủ trước khi chạy tổng hợp
```

## 8. Luồng Tổng hợp Điểm và Chọn Đội Vào Chung kết

```
Sau khi tất cả giám khảo hoàn thành chấm điểm cho một bảng:
  → Admin kích hoạt tổng hợp (hoặc Timeline Agent kích hoạt tự động)
  → Backend:
      1. Tính điểm trung bình có trọng số mỗi đội qua tất cả giám khảo
      2. Sắp xếp đội theo điểm (giảm dần)
      3. Chọn N đội đầu (ví dụ: top 2 mỗi bảng → đội vào chung kết)
      4. Cập nhật trạng thái đội: VÀO_CHUNG_KẾT hoặc BỊ_LOẠI
  → Timeline Agent kích hoạt mốc THONG_BAO_CHUNG_KET:
      → Bộ sinh Email AI: gửi email thông báo vào chung kết cho đội vượt qua
  → Chung kết:
      → Hội đồng giám khảo riêng được phân công cho bảng chung kết
      → Quy trình chấm điểm tương tự → xếp hạng cuối cùng được tính
      → Kết quả công bố
```

## 9. Luồng Xử lý Khiếu nại

```
Thí sinh hoặc đội nộp khiếu nại:
  → Điền form có cấu trúc: id_cuoc_thi, id_doi, loai_khieu_nai, mô tả
  → Backend lưu khiếu nại vào DB
  → Admin nhận thông báo
  → Admin xem xét, cập nhật trạng thái (ĐÃ NHẬN → ĐANG XEM XÉT → ĐÃ GIẢI QUYẾT)
  → Ghi chú giải quyết lưu vào DB
  → Thí sinh có thể xem trạng thái khiếu nại (chỉ đọc)
```

## 10. Luồng Truy cập Dữ liệu Lịch sử

```
Nhân viên/Admin yêu cầu dữ liệu lịch sử:
  → Xác thực nhân viên có quyền truy cập (không phải vai trò thí sinh)
  → Truy vấn: cuộc thi cũ, điểm, xếp hạng đội, log email
  → Chế độ xem chỉ đọc dữ liệu cuộc thi đã lưu trữ
  → Thí sinh KHÔNG THỂ truy cập dữ liệu cuộc thi khác hoặc điểm số
```
