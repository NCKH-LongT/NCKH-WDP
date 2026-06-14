# Phương pháp luận

## Thiết kế nghiên cứu

Nghiên cứu này sử dụng phương pháp **Design Science Research (DSR)** kết hợp với **thiết kế đánh giá thực nghiệm**. Dự án tập trung vào việc thiết kế, triển khai và xác thực một nền tảng giám sát và bảo trì hạ tầng hỗ trợ AR trong môi trường trung tâm dữ liệu mô phỏng.

Bài toán nghiên cứu mang tính thực tiễn và hướng hệ thống: các quy trình giám sát truyền thống thường tách rời phân tích telemetry, xử lý cảnh báo và hỗ trợ bảo trì hiện trường thành các công cụ riêng biệt. Sự phân mảnh này khiến người vận hành khó chuyển đổi mượt mà từ phát hiện bất thường sang hiểu ngữ cảnh và thực hiện hành động.

Các phương pháp hiện tại cũng thường gặp hạn chế ở một hoặc nhiều điểm sau:

- phát hiện bất thường nhưng không cung cấp đủ ngữ cảnh vận hành
- truy xuất thông tin liên quan nhưng không hỗ trợ quy trình bảo trì có hướng dẫn AR
- tạo tóm tắt bằng AI nhưng không đảm bảo tính chính xác quy trình hoặc khả năng truy vết hệ thống
- dựa vào các chỉ số điểm rời rạc, không phản ánh hành vi bất thường theo thời gian

Do đó, hệ thống được đề xuất nhằm hợp nhất giám sát, truy xuất ngữ cảnh và bảo trì hỗ trợ AR trong cùng một kiến trúc. Các giả thuyết nghiên cứu chính gồm:

1. Một pipeline kết hợp thu thập theo sự kiện, truy xuất theo ngữ cảnh và tăng cường bằng AI có thể cải thiện chất lượng diễn giải cảnh báo so với các baseline thủ công, rule-based hoặc chỉ dùng LLM.
2. Một client WebAR hỗ trợ neo theo mã QR và phân giải ngữ cảnh từ control plane có thể giảm thời gian hoàn thành tác vụ bảo trì và giảm tải nhận thức của người dùng.
3. Kiến trúc backend dạng module sử dụng Redpanda và ClickHouse có thể hỗ trợ giám sát độ trễ thấp và phân tích lịch sử quy mô lớn mà không làm mờ ranh giới giữa dữ liệu gốc và dữ liệu suy diễn.

---

## Kiến trúc hệ thống mức cao

Hệ thống được tổ chức thành 4 lớp vận hành: client/UI, control plane, lõi xử lý & AI, và hạ tầng dữ liệu.

(Sơ đồ kiến trúc giữ nguyên như bản gốc)

---

Thiết kế thể hiện rõ sự tách biệt trách nhiệm:

- **Web Dashboard** và **WebAR Client** là lớp giao diện
- **Control Plane API và BFF** tổng hợp phản hồi cho client
- các service miền nghiệp vụ quản lý từng bounded context riêng
- ingestion và streaming xử lý luồng telemetry
- phân tích và tăng cường dữ liệu được suy ra từ dữ liệu vận hành, không thay thế dữ liệu gốc

---

## Phương pháp phát triển hệ thống

Nền tảng được xây dựng theo kiến trúc **microservices** với luồng dữ liệu **event-driven**. Việc triển khai theo hướng prototype tăng dần, trong đó mỗi bounded context được phát triển và kiểm thử độc lập trước khi tích hợp.

Nguyên tắc phát triển:

- duy trì tách biệt rõ giữa control plane và data plane
- giữ quyền sở hữu nghiệp vụ trong đúng service
- dùng streaming bất đồng bộ cho telemetry
- AI chỉ là lớp tăng cường, không sở hữu “sự thật” của hệ thống
- tránh truy cập trực tiếp cross-service database

---

## Phương pháp kỹ thuật phần mềm

Mẫu phát triển chính là workflow service-oriented với đặc điểm:

- kiến trúc microservices, giao tiếp event-driven
- điều phối API qua BFF dựa trên NestJS
- Redpanda làm backbone streaming
- ClickHouse lưu trữ và phân tích telemetry
- MongoDB cho dữ liệu nghiệp vụ dạng document
- Redis làm cache và trạng thái tạm
- MinIO lưu trữ batch và dữ liệu lạnh
- WebAR chạy trên trình duyệt, tương tác qua QR marker

---

## Công nghệ và hạ tầng

| Lớp hạ tầng         | Công nghệ  | Vai trò                           |
| ------------------- | ---------- | --------------------------------- |
| Backend core        | NestJS     | điều phối control plane và API    |
| Gateway/BFF         | NestJS BFF | tổng hợp dữ liệu cho client       |
| Kho phân tích chính | ClickHouse | lưu telemetry, truy vấn phân tích |
| Kho nghiệp vụ       | MongoDB    | lưu dữ liệu theo service          |
| Message backbone    | Redpanda   | luồng sự kiện bất đồng bộ         |
| Cache               | Redis      | dữ liệu nóng và trạng thái nhanh  |
| Lưu trữ lạnh        | MinIO      | file batch và dữ liệu lưu trữ     |

---

## Luồng dữ liệu hệ thống

1. Collector gửi telemetry đến ingestion API
2. Worker validate và publish event vào Redpanda
3. Worker xử lý stream, làm sạch và chuẩn hóa dữ liệu
4. ClickHouse lưu dữ liệu phân tích
5. MongoDB lưu dữ liệu nghiệp vụ
6. Redis lưu trạng thái truy xuất nhanh
7. Control plane tổng hợp và trả dữ liệu cho client

Luồng này đảm bảo xử lý gần thời gian thực và giữ ranh giới dữ liệu rõ ràng.

---

## Tích hợp AI

AI được dùng như một lớp **tăng cường (enrichment)**, không phải nguồn dữ liệu gốc.

### Chuẩn bị dữ liệu

Đầu vào AI gồm:

- cửa sổ telemetry từ ClickHouse
- ngữ cảnh tài sản từ control plane
- cảnh báo và incident
- ngữ cảnh bảo trì AR

Dữ liệu được gom thành “context bundle” trước khi gửi vào AI để tránh nhiễu.

---

### Luồng xử lý

1. Người dùng gửi yêu cầu
2. Control plane xác định context liên quan
3. Truy xuất telemetry và dữ liệu nghiệp vụ
4. Tạo context bundle
5. AI tạo output (tóm tắt, cảnh báo, gợi ý…)
6. Trả kết quả về control plane
7. Control plane định dạng lại cho client

---

### Kiểm soát output

AI chỉ được tạo:

- tóm tắt vận hành
- danh sách gợi ý
- nhãn rủi ro / bất thường
- hỗ trợ bảo trì

Không sử dụng output tự do không kiểm soát để đảm bảo tính nhất quán.

---

### Vai trò truy xuất

Hệ thống hiện chủ yếu dùng truy xuất dựa trên metadata và dữ liệu có cấu trúc. Vector database chưa được dùng ở giai đoạn này để giữ kiến trúc đơn giản và rõ ràng.

---

## Quy trình đánh giá

So sánh hệ thống với baseline trong `baseline.md` theo các metric trong `evaluation_metrics.md`, gồm 4 nhóm:

- giám sát và phát hiện cảnh báo
- truy xuất ngữ cảnh
- AR và hiệu suất con người
- hiệu năng hệ thống

---

### Môi trường thử nghiệm

Cần ghi lại:

- hệ điều hành
- CPU
- RAM
- lưu trữ
- phiên bản Node.js, Python
- phiên bản Redpanda, ClickHouse, MongoDB, Redis

---

### Cơ chế đánh giá

1. **Tự động**

- tính AUCPR, Recall@k, MRR@k, nDCG@k
- đo latency, throughput

2. **Có con người tham gia**

- đo thời gian hoàn thành task
- workload (NASA-TLX)
- usability (SUS)
- đánh giá định tính

---

### So sánh

- monitoring so với manual / rule-based / LLM-only
- retrieval theo ranking quality
- AR theo workflow con người
- hệ thống đo độc lập để kiểm chứng tính khả thi

---

## Threats to validity (đe doạ tính hợp lệ)

### Nội bộ

- sai lệch do người gán nhãn
- rò rỉ dữ liệu theo thời gian
- lựa chọn ngưỡng ảnh hưởng kết quả

Giảm thiểu bằng rubric rõ ràng và chia tách dữ liệu theo thời gian.

---

### Bên ngoài

- môi trường mô phỏng không phản ánh thực tế
- khó tổng quát hóa sang hệ thống khác
- phụ thuộc topology và quy trình vận hành

---

### Khái niệm

- metric có thể không phản ánh đúng thực tế nếu chọn sai
- dùng range-based metrics thay vì point-wise
- dùng ranking metrics thay vì accuracy đơn thuần
- dùng SUS và NASA-TLX cho yếu tố con người
- dùng percentile latency thay vì trung bình
