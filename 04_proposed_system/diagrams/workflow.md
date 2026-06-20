# Competition Workflow Diagram

> Placeholder — xuất file `workflow.png` từ draw.io và đặt vào thư mục này (mục tiêu: Tuần 6).

## Mô tả luồng cuộc thi đầu cuối (để vẽ diagram)

```
[Admin tạo cuộc thi]
        │
        ▼
[Thí sinh đăng ký / nộp dự án]
        │
        ▼
[Timeline Agent kiểm tra deadline (mỗi 60s)]
        │
        ├── Deadline đến → Đóng cổng nộp bài
        │
        ▼
[Admin xét duyệt → LLM sinh email thông báo vào chung kết]
        │
        ▼
[Giám khảo nhận bài → AI sinh câu hỏi từ review]
        │
        ▼
[Buổi vấn đáp → Giám khảo chấm điểm]
        │
        ▼
[Timeline Agent tổng hợp → Admin công bố kết quả]
        │
        ▼
[LLM sinh email thông báo kết quả cuối]
```

## Công cụ vẽ

- draw.io: nhập mô tả trên và xuất PNG với tên `workflow.png`
- Kích thước khuyến nghị: 800 x 1200 px (dọc)
