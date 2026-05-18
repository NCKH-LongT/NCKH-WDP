# System Architecture

## 1. Overview

Mô tả tổng quan hệ thống.

## 2. Main Components

| Component         | Description                      |
| ----------------- | -------------------------------- |
| Frontend          | Giao diện người dùng             |
| Backend API       | Xử lý nghiệp vụ                  |
| Database          | Lưu dữ liệu hệ thống             |
| AI Service        | Chạy model AI hoặc gọi API model |
| Vector Database   | Lưu embedding nếu dùng RAG       |
| External Services | API hoặc công cụ bên ngoài       |

## 3. Architecture Diagram

> Chèn hình kiến trúc tại đây (xem `diagrams/architecture.png`).

## 4. Data Flow

1. User nhập dữ liệu.
2. Backend lưu dữ liệu.
3. Backend gửi dữ liệu đến AI Service.
4. AI Service xử lý bằng model.
5. Kết quả trả về hệ thống.
6. User xem kết quả hoặc khuyến nghị.

## 5. AI Integration

Mô tả model AI được tích hợp ở bước nào trong hệ thống.
