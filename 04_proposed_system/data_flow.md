# Data Flow

## 1. Overview

Mô tả luồng dữ liệu tổng quan trong hệ thống.

## 2. Data Flow Diagram

> Chèn hình luồng dữ liệu tại đây (xem `diagrams/workflow.png`).

## 3. Step-by-Step Data Flow

| Step | Actor      | Action             | Output                      |
| ---- | ---------- | ------------------ | --------------------------- |
| 1    | User       | Nhập dữ liệu       | Form data                   |
| 2    | Backend    | Validate & lưu     | Database record             |
| 3    | Backend    | Gửi đến AI Service | Processed input             |
| 4    | AI Service | Xử lý model        | Prediction / Recommendation |
| 5    | Backend    | Nhận kết quả       | AI response                 |
| 6    | Frontend   | Hiển thị kết quả   | User view                   |

## 4. Input Data

Mô tả các loại dữ liệu đầu vào:

-
-

## 5. Output Data

Mô tả các loại dữ liệu đầu ra:

-
-
