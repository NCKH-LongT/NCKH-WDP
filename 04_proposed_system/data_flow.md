# Data Flow

## 1. Tong quan luong du lieu

He thong co bon nhom luong du lieu chinh:

1. Luong du lieu quan ly giai dau.
2. Luong du lieu dang ky tham gia cuoc dua.
3. Luong du lieu AI du doan xac suat chien thang.
4. Luong du lieu ket qua, xep hang, vi ao va ca cuoc ao.

AI prediction khong hoat dong doc lap. Ket qua du doan duoc tao tu du lieu nghiep vu da luu trong database, sau do quay lai he thong de hien thi cho nguoi dung va luu vao bang `ai_predictions`.

## 2. Luong du lieu tong quat

```text
User
  |
Frontend
  |
Backend API
  |
Database
  |
Feature Engineering
  |
AI Service
  |
XGBoost Model
  |
Prediction Result
  |
Backend API
  |
Database + Frontend
```

## 3. Luong quan ly giai dau

```text
Admin
  |
Create tournament / season / race
  |
Backend API validates data
  |
Database stores tournament and race information
  |
Frontend displays schedule and race details
```

### Mo ta

Quan tri vien tao giai dau, mua giai va cac cuoc dua. Backend kiem tra tinh hop le cua du lieu nhu thoi gian, so luong ngua, phi tham gia, giai thuong va dieu kien tham gia. Sau khi luu thanh cong, thong tin duoc hien thi cho chu ngua, nai ngua va khan gia.

## 4. Luong dang ky tham gia cuoc dua

```text
Horse Owner
  |
Select horse and jockey
  |
Backend checks race conditions
  |
Wallet service deducts entry fee
  |
Database stores race registration
  |
Notification sent to related users
```

### Mo ta

Chu ngua chon ngua va nai ngua de dang ky vao cuoc dua. Backend kiem tra dieu kien tham gia nhu trang thai ngua, so luong slot, lich thi dau cua nai ngua va so du vi ao. Neu hop le, he thong tru phi tham gia va luu ban ghi dang ky.

## 5. Luong AI du doan xac suat chien thang

```text
Spectator / Admin
  |
Request race prediction
  |
Backend loads race participants
  |
Backend loads historical race results
  |
Feature Engineering creates model input
  |
AI Service runs XGBoost model
  |
Softmax converts scores to probabilities
  |
Backend saves predictions
  |
Frontend displays predicted ranking
```

### Buoc xu ly chi tiet

1. Nguoi dung truy cap man hinh chi tiet cuoc dua.
2. Frontend gui request lay du doan den Backend API.
3. Backend xac dinh `race_id` va danh sach ngua tham gia.
4. Backend truy van database de lay:
   - Ho so ngua.
   - Ho so nai ngua.
   - Lich su thi dau cua ngua.
   - Lich su thi dau cua nai ngua.
   - Ket qua cac cuoc dua truoc.
   - Thong tin cuoc dua hien tai.
5. He thong tao cac feature:
   - Horse Win Rate.
   - Jockey Win Rate.
   - Average Finish Position.
   - Total Points.
   - Total Earnings.
   - Recent Form.
   - Number of Participated Races.
6. AI Service nhan feature va chay XGBoost.
7. Ket qua diem du doan cua tung ngua duoc chuan hoa bang Softmax.
8. Backend luu ket qua vao `ai_predictions`.
9. Frontend hien thi xac suat thang va bang xep hang du doan.

## 6. Luong xac nhan ket qua cuoc dua

```text
Referee
  |
Submit official race result
  |
Backend validates result
  |
Database stores official result
  |
Ranking service updates points
  |
Betting service settles virtual bets
  |
Notifications sent to users
```

### Mo ta

Sau khi cuoc dua ket thuc, trong tai nhap va xac nhan ket qua chinh thuc. Backend kiem tra ket qua co day du vi tri ve dich va co trung voi danh sach tham gia hay khong. Sau khi ket qua duoc xac nhan, he thong cap nhat bang xep hang, tinh tien thuong va thanh toan ca cuoc ao.

## 7. Luong ca cuoc ao

```text
Spectator
  |
Place virtual bet
  |
Backend checks wallet balance and race status
  |
Wallet service deducts virtual amount
  |
Database stores bet
  |
After official result, betting service calculates outcome
  |
Wallet service pays reward or marks bet as lost
```

### Mo ta

Khan gia dat cuoc ao truoc khi cuoc dua bat dau. He thong chi cho phep dat cuoc neu cuoc dua con mo va nguoi dung du so du vi ao. Sau khi trong tai xac nhan ket qua, betting service tu dong tinh thang thua cho cac loai cuoc Win, Place va Show.

## 8. Luong dashboard va thong ke

```text
Admin
  |
Request dashboard
  |
Backend aggregates statistics
  |
Database returns tournament, race, bet, wallet and ranking data
  |
Backend calculates summary metrics
  |
Frontend displays dashboard
```

### Chi so dashboard

- Tong so nguoi dung.
- Tong so giai dau.
- Tong so cuoc dua.
- Tong so luot cuoc ao.
- Tong giao dich vi ao.
- Ngua co thanh tich cao.
- Nai ngua co thanh tich cao.
- Do chinh xac AI theo cac cuoc dua da co ket qua.

## 9. Du lieu dau vao va dau ra theo module

| Module | Input | Output |
|---|---|---|
| User Management | Thong tin dang ky, dang nhap, vai tro | Tai khoan, token, quyen truy cap |
| Horse Management | Ho so ngua, giay to, chu ngua | Danh sach ngua, lich su thi dau |
| Jockey Management | Ho so nai ngua, loi moi | Trang thai loi moi, lich thi dau |
| Race Management | Thong tin cuoc dua, dieu kien, giai thuong | Lich dua, danh sach cuoc dua |
| Registration | Ngua, nai ngua, cuoc dua, phi tham gia | Ban ghi dang ky |
| AI Prediction | Race data, historical data, engineered features | Xac suat thang, xep hang du doan |
| Referee Result | Ket qua chinh thuc, vi pham | Bang ket qua, bien ban |
| Virtual Betting | Loai cuoc, so tien, ngua duoc chon | Ket qua cuoc, giao dich vi ao |
| Dashboard | Du lieu tong hop | Bieu do, so lieu thong ke |

## 10. Diem kiem soat chat luong du lieu

He thong can kiem soat chat luong du lieu o cac diem sau:

- Khong cho dang ky ngua khong du dieu kien.
- Khong cho nai ngua tham gia hai cuoc dua trung thoi gian.
- Khong cho dat cuoc sau khi cuoc dua da bat dau.
- Chi trong tai duoc phan cong moi co quyen xac nhan ket qua.
- AI chi du doan khi cuoc dua co danh sach tham gia hop le.
- Neu du lieu lich su thieu, he thong can dung gia tri mac dinh hoac hien canh bao do tin cay thap.
- Moi ket qua du doan can luu model version de phuc vu danh gia lai sau nay.

