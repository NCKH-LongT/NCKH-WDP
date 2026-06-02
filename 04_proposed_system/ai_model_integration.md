# AI Model Integration

## 1. Model duoc su dung

Model chinh cua he thong la **XGBoost** cho bai toan du doan xac suat chien thang cua ngua trong tung cuoc dua.

Loai model:

- Machine Learning model.
- Gradient Boosting Decision Trees.
- Supervised learning.
- Tabular data prediction.

XGBoost duoc su dung de tinh diem chien thang cho tung ngua dua tren cac dac trung lich su. Sau do, he thong dung Softmax de chuan hoa diem cua tat ca ngua trong cung mot cuoc dua thanh xac suat chien thang.

## 2. Vi sao chon XGBoost

XGBoost phu hop voi bai toan cua de tai vi:

1. Du lieu dau vao cua he thong chu yeu la du lieu dang bang, nhu ty le thang, diem, so lan thi dau, vi tri ve dich trung binh va thanh tich nai ngua.
2. XGBoost xu ly tot quan he phi tuyen giua cac dac trung.
3. Model hoat dong tot voi tap du lieu vua va nho, phu hop giai doan dau khi du lieu dua ngua chua qua lon.
4. XGBoost thuong dat hieu qua cao trong cac bai toan phan loai va xep hang tren du lieu co cau truc.
5. Model co the cung cap feature importance, giup giai thich cac yeu to anh huong den du doan.
6. So voi neural network, XGBoost de huan luyen, de tinh chinh va it yeu cau du lieu lon hon.

## 3. Co so lua chon tu cac nghien cuu lien quan

Nhieu nghien cuu truoc da chung minh rang du lieu lich su co the dung de du doan ket qua dua ngua:

- Bolton va Chapman su dung Multinomial Logit de uoc luong xac suat thang.
- Chapman mo rong Multinomial Logit tren 2,000 cuoc dua Hong Kong.
- Pudaruth va cong su dung Weighted Probabilistic Approach.
- Davoodi va Khanteymoori, Williams va Li su dung neural network.
- Gupta va Singh so sanh nhieu thuat toan Machine Learning va nhan manh vai tro cua feature selection.

Tuy nhien, phan lon nghien cuu tap trung vao du doan hoac ca cuoc, chua tich hop model vao mot he thong quan ly giai dua ngua day du. Vi vay, de tai chon XGBoost lam model chinh va dat model nay vao kien truc full-stack gom frontend, backend, database, AI service, vi ao, ca cuoc ao va dashboard.

## 4. Model lay tu dau

Model khong duoc xay dung tu dau ve mat thuat toan. He thong su dung XGBoost tu thu vien open-source:

- Thu vien chinh: `xgboost`.
- Thu vien ho tro: `pandas`, `numpy`, `scikit-learn`.
- Moi truong tich hop de xuat: Python AI Service.

Model se duoc huan luyen lai tren du lieu lich su cua he thong hoac du lieu gia lap co kiem soat trong giai doan thuc nghiem.

## 5. Input cua model

Input cua model la du lieu dang bang, moi dong tuong ung voi mot ngua trong mot cuoc dua.

### Cac feature de xuat

| Nhom feature | Feature |
|---|---|
| Horse performance | horse_win_rate, horse_total_races, horse_recent_form, horse_average_finish_position |
| Horse ranking | horse_total_points, horse_total_earnings, horse_current_rank |
| Jockey performance | jockey_win_rate, jockey_total_races, jockey_average_finish_position |
| Race information | race_distance, race_type, number_of_participants, entry_fee, prize_amount |
| Pair history | horse_jockey_past_races, horse_jockey_win_rate |
| Recent result | last_3_finish_average, last_5_finish_average, days_since_last_race |

### Vi du input

```text
race_id = RACE_001
horse_id = HORSE_005
jockey_id = JOCKEY_002
horse_win_rate = 0.32
horse_total_races = 25
horse_recent_form = 0.70
horse_average_finish_position = 2.8
jockey_win_rate = 0.28
race_distance = 1600
number_of_participants = 8
```

## 6. Output cua model

Output truc tiep cua XGBoost la diem du doan hoac xac suat thang rieng le cho tung ngua, tuy theo cau hinh bai toan.

Output cuoi cung cua AI Service la:

- `race_id`
- `horse_id`
- `horse_name`
- `predicted_score`
- `win_probability`
- `predicted_rank`
- `top_influencing_features`

Vi du output:

```text
Race: RACE_001
1. Horse A - Win Probability: 31.5%
2. Horse B - Win Probability: 22.4%
3. Horse C - Win Probability: 15.8%
```

## 7. Cach tich hop vao app

He thong tich hop AI theo huong **Python AI Service + REST API**.

### Luong tich hop

1. Nguoi dung mo man hinh chi tiet cuoc dua tren frontend.
2. Frontend gui request den Backend API de lay du doan.
3. Backend kiem tra trang thai cuoc dua va quyen truy cap.
4. Backend lay du lieu ngua, nai ngua, cuoc dua va lich su thi dau tu Database.
5. Backend tao feature hoac goi AI Service tao feature.
6. Backend gui request den AI Service qua REST API.
7. AI Service tai model XGBoost da huan luyen.
8. AI Service thuc hien prediction va Softmax normalization.
9. AI Service tra ket qua cho Backend API.
10. Backend luu ket qua vao bang `ai_predictions`.
11. Frontend hien thi bang xac suat chien thang va xep hang du doan.

### Vi du API

```text
POST /api/ai/predict-race
```

Request:

```json
{
  "race_id": "RACE_001"
}
```

Response:

```json
{
  "race_id": "RACE_001",
  "model": "XGBoost",
  "model_version": "v1.0",
  "predictions": [
    {
      "horse_id": "HORSE_001",
      "win_probability": 0.315,
      "predicted_rank": 1
    },
    {
      "horse_id": "HORSE_002",
      "win_probability": 0.224,
      "predicted_rank": 2
    }
  ]
}
```

## 8. Training va retraining

Model duoc huan luyen theo batch, khong huan luyen lai sau moi request.

### Quy trinh training

1. Lay du lieu lich su tu database.
2. Lam sach du lieu va xu ly gia tri thieu.
3. Tao feature tu lich su thi dau cua ngua va nai ngua.
4. Tao label dua tren ket qua thuc te: thang hoac khong thang.
5. Chia du lieu thanh train, validation va test set.
6. Huan luyen XGBoost.
7. Danh gia bang Accuracy, Top-1 Accuracy, Top-3 Accuracy, Log Loss va Brier Score.
8. Luu model tot nhat vao Model Storage.
9. Trien khai model vao AI Service.

### Retraining

Model co the duoc huan luyen lai theo lich:

- Hang tuan.
- Hang thang.
- Sau khi co them mot so luong cuoc dua moi du lon.

## 9. Baseline

He thong can co baseline de so sanh voi XGBoost.

### Baseline de xuat

| Baseline | Mo ta |
|---|---|
| Random prediction | Gan xac suat bang nhau cho moi ngua trong mot cuoc dua |
| Win-rate ranking | Xep hang dua tren ty le thang lich su cua ngua |
| Point-based ranking | Xep hang dua tren diem tich luy cua ngua |
| Weighted probabilistic approach | Gan trong so thu cong cho cac yeu to nhu phong do, nai ngua va diem so |
| Multinomial Logit | Mo hinh thong ke truyen thong da duoc dung trong nghien cuu dua ngua |
| Random Forest | Baseline Machine Learning dang ensemble |

XGBoost duoc ky vong tot hon baseline vi co kha nang hoc quan he phi tuyen va ket hop nhieu dac trung hieu qua hon.

## 10. Metric danh gia

### Metric cho AI

- Accuracy.
- Top-1 Accuracy.
- Top-3 Accuracy.
- Log Loss.
- Brier Score.
- Calibration curve.

### Metric cho he thong

- API Response Time.
- Throughput.
- Concurrent Users.
- Uptime.
- Prediction latency.

### Danh gia nguoi dung va chuyen gia

- Tinh hop ly cua du doan.
- Muc do de hieu cua xac suat AI.
- Muc do huu ich doi voi khan gia va ban to chuc.
- Muc do tin cay cua he thong.

## 11. Luu y dao duc va pham vi

Module ca cuoc trong he thong la **ca cuoc ao**, phuc vu muc dich mo phong va danh gia he thong. Ket qua AI chi la cong cu ho tro tham khao, khong phai bao dam ket qua thuc te. He thong can hien thi ro rang rang xac suat chien thang la du doan dua tren du lieu lich su va co the sai lech khi du lieu thieu, du lieu moi thay doi hoac co yeu to ngoai le trong cuoc dua.

