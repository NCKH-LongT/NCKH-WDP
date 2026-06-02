# System Overview

## 1. Ten he thong

**AI-Integrated Horse Racing Tournament Management System with Win Probability Prediction**

Tieng Viet:

**He thong quan ly giai dua ngua tich hop AI du doan xac suat chien thang**

## 2. Muc tieu he thong

He thong duoc de xuat nham quan ly toan bo quy trinh cua mot giai dua ngua, bao gom dang ky tham gia, quan ly ngua, quan ly nai ngua, lap lich cuoc dua, xac nhan ket qua, bang xep hang, vi ao, ca cuoc ao va thong ke. Diem khac biet chinh cua he thong la tich hop AI de du doan xac suat chien thang cua tung ngua truoc moi cuoc dua dua tren du lieu lich su.

He thong khong tap trung vao viec xay dung mot mo hinh AI moi tu dau. Thay vao do, he thong ung dung cac thuat toan Machine Learning da duoc chung minh hieu qua trong bai toan du doan dua ngua, dac biet la XGBoost, de tao ra module ho tro ra quyet dinh trong nen tang quan ly giai dau.

## 3. Nguoi dung chinh

### 3.1. Chu ngua

Chu ngua su dung he thong de quan ly ho so ngua, dang ky ngua tham gia cuoc dua, moi hoac thue nai ngua, theo doi lich su thi dau va tien thuong.

### 3.2. Nai ngua

Nai ngua su dung he thong de quan ly ho so ca nhan, xem loi moi thi dau, chap nhan hoac tu choi loi moi, theo doi lich thi dau va thanh tich ca nhan.

### 3.3. Trong tai

Trong tai su dung he thong de kiem tra dieu kien thi dau, diem danh ngua truoc cuoc dua, ghi nhan vi pham, xac nhan ket qua va lap bien ban cuoc dua.

### 3.4. Khan gia

Khan gia su dung he thong de xem thong tin giai dau, xem lich thi dau, xem ho so ngua va nai ngua, nap tien vao vi ao, dat cuoc ao va xem du doan xac suat chien thang cua AI.

### 3.5. Quan tri vien

Quan tri vien su dung he thong de quan ly tai khoan, giai dau, cuoc dua, trong tai, giao dich, thong ke va dashboard van hanh.

## 4. Chuc nang chinh

He thong bao gom cac chuc nang chinh sau:

1. Quan ly nguoi dung va phan quyen theo vai tro.
2. Quan ly ho so ngua.
3. Quan ly ho so nai ngua.
4. Quan ly giai dau, mua giai va lich thi dau.
5. Quan ly cuoc dua, dieu kien tham gia, khoang cach dua, phi tham gia va giai thuong.
6. Dang ky ngua va nai ngua tham gia cuoc dua.
7. Kiem tra dieu kien thi dau va xac nhan ket qua boi trong tai.
8. Vi ao, thanh toan phi tham gia, hoan tien va lich su giao dich.
9. Ca cuoc ao voi cac loai cuoc Win, Place va Show.
10. AI du doan xac suat chien thang cua tung ngua.
11. Bang xep hang ngua, nai ngua va chu ngua.
12. Dashboard thong ke cho quan tri vien.
13. He thong thong bao cho lich dua, ket qua, loi moi va ket qua cuoc.

## 5. Du lieu dau vao

Du lieu dau vao cua he thong gom:

- Thong tin nguoi dung: vai tro, tai khoan, thong tin lien he.
- Ho so ngua: ten, tuoi, giong, chu ngua, trang thai, giay to chung nhan.
- Ho so nai ngua: kinh nghiem, thanh tich, ty le thang, lich su thi dau.
- Thong tin giai dau: ten giai, mua giai, thoi gian, dia diem.
- Thong tin cuoc dua: khoang cach, dieu kien tham gia, phi tham gia, giai thuong, danh sach ngua.
- Lich su thi dau: vi tri ve dich, diem, tien thuong, ket qua cuoc dua.
- Lich su ca cuoc ao: loai cuoc, so tien, ngua duoc chon, trang thai thanh toan.
- Du lieu thong ke dung cho AI: ty le thang cua ngua, ty le thang cua nai ngua, phong do gan day, diem xep hang, so lan tham gia, vi tri ve dich trung binh va tong tien thuong.

## 6. AI model su dung

Model chinh duoc de xuat la **XGBoost** cho bai toan du doan xac suat chien thang cua ngua. XGBoost phu hop vi:

- Xu ly tot du lieu dang bang.
- Hoat dong hieu qua voi du lieu vua va nho.
- Hoc duoc quan he phi tuyen giua cac dac trung.
- Co the tinh feature importance de giai thich ket qua.
- Phu hop voi cac dac trung nhu win rate, recent form, average finish position va jockey performance.

Ket qua cua XGBoost duoc chuan hoa bang Softmax trong pham vi tung cuoc dua de tao phan phoi xac suat hop le, tong xac suat cua cac ngua trong cung cuoc dua bang 1.

## 7. Output cua he thong

Output cua he thong bao gom:

- Danh sach giai dau, cuoc dua va lich thi dau.
- Ho so ngua, ho so nai ngua va lich su thi dau.
- Danh sach dang ky tham gia cuoc dua.
- Ket qua cuoc dua da duoc trong tai xac nhan.
- Bang xep hang ngua, nai ngua va chu ngua.
- Lich su giao dich vi ao va ket qua ca cuoc ao.
- Dashboard thong ke cho quan tri vien.
- Xac suat chien thang cua tung ngua truoc cuoc dua.
- Bang xep hang du doan truoc cuoc dua.
- Cac chi so giai thich du doan nhu phong do gan day, ty le thang va diem xep hang.

