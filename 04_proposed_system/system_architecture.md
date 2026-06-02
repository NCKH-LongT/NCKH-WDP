# System Architecture

## 1. Tong quan kien truc

He thong duoc thiet ke theo kien truc nhieu lop, trong do frontend phuc vu giao dien nguoi dung, backend xu ly nghiep vu, database luu tru du lieu, AI service thuc hien du doan va model storage luu model da huan luyen.

Kien truc tong quat:

```text
User Interface
    |
Backend API
    |
Database
    |
AI Service
    |
XGBoost Model / Feature Store / Model Storage
```

Trong qua trinh van hanh, Backend API la thanh phan dieu phoi chinh. Frontend khong goi truc tiep model AI ma gui yeu cau den Backend API. Backend thu thap du lieu lien quan tu Database, tao bo dac trung can thiet, sau do goi AI Service de lay ket qua du doan.

## 2. Frontend

Frontend cung cap giao dien Web/Mobile cho cac nhom nguoi dung khac nhau.

### Chuc nang frontend

- Dang ky, dang nhap va quan ly tai khoan.
- Giao dien rieng cho chu ngua, nai ngua, trong tai, khan gia va quan tri vien.
- Man hinh quan ly giai dau, cuoc dua, ngua va nai ngua.
- Man hinh dang ky tham gia cuoc dua.
- Man hinh xem lich thi dau va ket qua.
- Man hinh vi ao va ca cuoc ao.
- Man hinh hien thi xac suat thang do AI du doan.
- Dashboard thong ke cho quan tri vien.

### Yeu cau frontend

- Hien thi du lieu ro rang theo tung vai tro.
- Bao ve cac chuc nang nhay cam bang phan quyen.
- Hien thi xac suat AI theo bang va bieu do de nguoi dung de hieu.
- Tach biet ket qua AI voi ket qua chinh thuc do trong tai xac nhan.

## 3. Backend API

Backend API chiu trach nhiem xu ly logic nghiep vu va ket noi cac thanh phan cua he thong.

### Chuc nang backend

- Xac thuc nguoi dung bang JWT.
- Phan quyen theo vai tro.
- Xu ly CRUD cho nguoi dung, ngua, nai ngua, giai dau va cuoc dua.
- Xu ly dang ky tham gia cuoc dua.
- Xu ly vi ao, giao dich, phi tham gia va hoan tien.
- Xu ly ca cuoc ao va thanh toan ket qua cuoc.
- Nhan ket qua chinh thuc tu trong tai.
- Tinh bang xep hang.
- Tong hop du lieu cho dashboard.
- Goi AI Service de lay du doan xac suat chien thang.

## 4. Database

Database luu tru du lieu nghiep vu va du lieu phuc vu huan luyen AI.

### Cac nhom bang du lieu chinh

- `users`: tai khoan va vai tro nguoi dung.
- `horses`: ho so ngua.
- `jockeys`: ho so nai ngua.
- `owners`: thong tin chu ngua.
- `tournaments`: thong tin giai dau.
- `races`: thong tin cuoc dua.
- `race_registrations`: danh sach dang ky tham gia cuoc dua.
- `race_results`: ket qua cuoc dua.
- `wallets`: vi ao cua nguoi dung.
- `transactions`: lich su giao dich.
- `bets`: lich su ca cuoc ao.
- `rankings`: bang xep hang.
- `ai_predictions`: ket qua du doan cua AI.
- `model_training_data`: du lieu tong hop phuc vu huan luyen va danh gia model.

## 5. AI Service

AI Service la mot service rieng, co the trien khai bang Python. Service nay phu trach tien xu ly du lieu, tao dac trung, tai model da huan luyen va tra ve ket qua du doan.

### Chuc nang AI Service

- Nhan `race_id` hoac danh sach ngua tham gia tu Backend API.
- Lay hoac nhan cac dac trung da duoc tong hop.
- Kiem tra du lieu thieu va xu ly gia tri mac dinh.
- Chay XGBoost model de tinh diem du doan.
- Chuan hoa diem bang Softmax thanh xac suat.
- Tra ve danh sach ngua kem xac suat chien thang.
- Luu log phien ban model va thoi gian du doan.

## 6. Model Storage va Feature Store

Model Storage luu model XGBoost da duoc huan luyen, cau hinh feature va thong tin phien ban model. Feature Store hoac bang tong hop dac trung luu cac chi so da tinh san nhu ty le thang, phong do gan day va vi tri ve dich trung binh.

### Thanh phan luu tru AI

- File model: `xgboost_win_probability_model.pkl` hoac dinh dang tuong duong.
- File cau hinh feature: danh sach feature va thu tu feature.
- Thong tin model version.
- Bang du lieu feature da tong hop.
- Ket qua danh gia model theo tung lan huan luyen.

## 7. Kien truc xu ly du doan

```text
Spectator / Admin
    |
Frontend: Request prediction for a race
    |
Backend API: Validate role and race status
    |
Database: Load race, horses, jockeys, historical results
    |
Feature Engineering: Build model input
    |
AI Service: XGBoost prediction
    |
Softmax Normalization
    |
Backend API: Save prediction result
    |
Frontend: Display win probability ranking
```

## 8. Ly do tach AI Service

AI Service nen duoc tach rieng voi Backend API vi:

- De phat trien bang Python va su dung cac thu vien ML nhu scikit-learn, pandas va xgboost.
- De cap nhat model doc lap voi logic nghiep vu.
- De huan luyen va trien khai model theo phien ban.
- De mo rong thanh batch prediction hoac scheduled retraining trong tuong lai.

