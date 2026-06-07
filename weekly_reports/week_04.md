# Weekly Report - Week 04

## Group Information

Class: SE1823

Group: G09

Project: AR-based Infrastructure Monitoring and Maintenance System

Leader: [Phan Võ Đức Huy]

Members:

- [Phan Võ Đức Huy] - [Leader]
- [Nguyễn Khánh Ngân] - [Member]
- [Lê Trần Anh Duy] - [Member]

## Tasks Completed This Week

| Member              | Task                                                                                                                                                                | Result     |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| [Phan Võ Đức Huy]   | Bổ sung workload collector cho collector agent để thu thập thông số container; xây dựng MVP cho identity service và asset context service backend, nghiên cứu WebAR | Hoàn thành |
| [Nguyễn Khánh Ngân] | Setup frontend, chọn theme và thử nghiệm UI layout; nghiên cứu hướng thay thế native AR bằng WebAR; tiếp tục thực hiện UI                                           | Hoàn thành |
| [Lê Trần Anh Duy]   | Cập nhật activity diagram, cập nhật SRS và tiếp tục thực hiện UI                                                                                                    | Hoàn thành |

## Git Commits

| Commit ID | Message                             | Author            |
| --------- | ----------------------------------- | ----------------- |
| 747e64a   | docs: add proposal system documents | [Phan Võ Đức Huy] |
| 2735aa4   | docs: add week 3 report             | [Phan Võ Đức Huy] |

## Current Problems

- **Phần WebAR mới dừng ở mức nghiên cứu và định hướng**, nhóm chưa có spike thực tế với `8th Wall` hoặc các thư viện WebAR liên quan để xác nhận khả năng chạy trên thiết bị hiện có.
- **Pipeline xử lý dữ liệu vẫn chưa được plan đủ sâu**: hiện mới rõ collector, identity service và asset context service ở mức đầu, nhưng luồng ingest -> message broker -> storage -> query/read model vẫn chưa được chốt cụ thể.
- **Frontend đã có theme và layout thử nghiệm nhưng chưa gắn chặt với data flow thật**, nên nguy cơ là UI đi trước contract backend và sau đó phải sửa nhiều.
- **Tuần tới có nhiều đầu việc nền tảng cùng lúc** như gateway, control plane, Redpanda, ClickHouse, UI và WebAR spike; nếu không chốt ưu tiên rõ thì rất dễ dàn trải.

## Plan for Next Week

### 1) Dựng nền backend và control plane

- Bắt đầu dựng `gateway` và `control plane` để tạo khung giao tiếp chung cho các service chính.
- Chốt phạm vi MVP backend trước khi mở rộng thêm service: ưu tiên `identity`, `asset context`, `user management` và `asset management`.
- Xác định rõ luồng request/response và các API tối thiểu phục vụ UI tuần tới.

### 2) Chốt baseline data pipeline

- Setup `Redpanda` cho event backbone ban đầu và xác định các topic tối thiểu cho telemetry/workload events.
- Setup `ClickHouse` cho hướng lưu trữ telemetry/time-series nếu nhóm tiếp tục chọn hướng này.
- Viết lại plan pipeline ở mức implementable: collector -> ingest/gateway -> broker -> storage -> query layer.
- Làm rõ phần nào là bắt buộc cho MVP, phần nào có thể để sau để tránh ôm quá nhiều hạ tầng sớm.

### 3) Làm web UI cơ bản

- Hoàn thiện web UI cơ bản cho `user management` và `asset management`.
- Đồng bộ UI layout với API contract và entity thực tế để tránh làm giao diện quá sớm so với backend.
- Nếu kịp, bắt đầu nối mock data hoặc API tạm cho các màn hình chính.

### 4) Thử nghiệm WebAR

- Thực hiện một spike nhỏ với `WebAR`, ưu tiên xác minh được khả năng mở trên mobile browser và thử marker-based flow cơ bản.
- So sánh nhanh giữa `8th Wall` và phương án nhẹ hơn nếu cần, nhưng mục tiêu tuần tới chỉ nên là kiểm tra tính khả thi chứ chưa cần tối ưu hoàn chỉnh.
- Nếu spike thành công, chốt luôn luồng tối thiểu cho PoC: `scan marker -> resolve asset -> hiển thị thông tin cơ bản`.

### 5) Giảm rủi ro triển khai

- Chốt thứ tự ưu tiên rõ: `backend foundation + UI cơ bản + WebAR spike` trước, các thành phần nâng cao xử lý sau.
- Ghi lại quyết định kỹ thuật ngắn gọn cho từng lựa chọn quan trọng như broker, telemetry store và WebAR stack để các tuần sau không phải tranh luận lại từ đầu.

## Questions for Instructor

- Với tiến độ hiện tại, instructor có đồng ý để nhóm ưu tiên hoàn thiện `web UI cơ bản + backend foundation + WebAR spike` trước, thay vì cố mở rộng đồng thời toàn bộ pipeline và AR flow hoàn chỉnh không?
- Nếu nhóm sử dụng `Redpanda` và `ClickHouse` ở mức nền tảng cho MVP, mức độ này có phù hợp với phạm vi môn học không, hay nên giảm xuống một kiến trúc đơn giản hơn ở giai đoạn đầu?
- Đối với phần AR, instructor có đồng ý việc tuần tới chỉ thực hiện `feasibility spike` cho WebAR trước khi commit hoàn toàn vào một stack cụ thể không?
