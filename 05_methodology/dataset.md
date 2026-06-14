# Kế hoạch Xây dựng Bộ Dữ liệu (Dataset Plan)

## Nguồn Dữ liệu (Data Sources)

Phần này mô tả chiến lược xây dựng bộ dữ liệu được sử dụng để hỗ trợ việc đánh giá nền tảng giám sát và bảo trì hạ tầng hỗ trợ thực tế tăng cường (AR) được đề xuất. Bộ dữ liệu được thiết kế xoay quanh hai trường hợp sử dụng chính:

- Giám sát hệ thống và phân tích cảnh báo
- Bảo trì hỗ trợ AR và nhận diện tài sản

Thay vì phụ thuộc vào một tập dữ liệu tĩnh duy nhất, dự án sử dụng một bộ dữ liệu đa tầng được xây dựng từ telemetry vận hành mô phỏng, metadata tài sản, bản ghi cảnh báo, kịch bản bảo trì và các đầu ra làm giàu dữ liệu bằng AI. Cấu trúc này phản ánh đúng luồng xử lý thực tế của hệ thống, trong đó các collector agent tạo ra sự kiện thô, lớp ingestion chuẩn hóa dữ liệu, Redpanda phân phối dữ liệu dưới dạng luồng sự kiện và các worker phía sau lưu trữ cả dữ liệu vận hành thời gian thực lẫn dữ liệu phân tích phục vụ đánh giá và truy xuất.

### Nguồn gốc và Quá trình Thu thập Dữ liệu

Bộ dữ liệu được tổng hợp từ nhiều nguồn trong môi trường giám sát hạ tầng mô phỏng:

- **Đầu ra từ Collector Agent:** telemetry thô, log hệ thống và các payload sự kiện vận hành được thu thập từ môi trường mô phỏng.
- **Dữ liệu đăng ký tài sản (Asset Registry):** topology hệ thống, metadata thiết bị, ánh xạ vị trí và các mã QR hoặc marker được sử dụng bởi ứng dụng WebAR.
- **Bản ghi cảnh báo và sự cố:** các bản ghi được sinh tự động hoặc biên soạn mô tả các điều kiện bất thường, mức độ nghiêm trọng của cảnh báo và các hành động bảo trì liên quan.
- **Dữ liệu kịch bản bảo trì:** các tình huống tác vụ được cấu trúc phục vụ quy trình kiểm tra và sửa chữa có hỗ trợ AR.
- **Đầu ra làm giàu dữ liệu từ AI hoặc Agent:** tóm tắt nội dung, nhãn phân loại, nhãn rủi ro và các chú thích suy diễn được tạo bởi pipeline phân tích.

Luồng thu thập dữ liệu chính tuân theo kiến trúc hệ thống:

```text
[Collector Agent] -> [API Ingestion Worker] -> [Redpanda]
                                          -> [Worker Pool / ELT]
                                          -> [Telemetry Store / Hot DB]
                                          -> [Cold DB / MinIO]
                                          -> [Analytical / Evaluation Layer]
```

Dịch vụ ingestion nhận các payload được đóng gói từ collector agent, chuyển đổi chúng thành các bản ghi sự kiện chuẩn hóa và công bố lên Redpanda. Các worker phía sau sẽ giải mã, làm phẳng cấu trúc, làm sạch và làm giàu dữ liệu trước khi lưu vào các lớp vận hành và phân tích.

### Phạm vi Dữ liệu

Bộ dữ liệu được thiết kế để bao phủ các bối cảnh vận hành sau:

- Các khoảng thời gian telemetry bình thường
- Các khoảng thời gian telemetry bất thường
- Các đợt cảnh báo lặp lại hoặc bùng phát
- Truy xuất tài sản dựa trên topology
- Tương tác bảo trì AR gắn với một mã QR hoặc marker cụ thể
- Điều tra sau cảnh báo và phân loại sự cố

Phạm vi này đảm bảo bộ dữ liệu có thể hỗ trợ cả đánh giá dạng truy xuất thông tin (retrieval-based evaluation) và đánh giá theo quy trình nghiệp vụ (workflow-oriented evaluation).

---

## Dữ liệu Lịch sử Vận hành (Historical Topic Data)

Trong mẫu gốc, phần này được sử dụng để lưu trữ các chủ đề nghiên cứu lịch sử. Trong dự án này, nó được chuyển đổi thành kho dữ liệu vận hành lịch sử dùng để đánh giá hành vi giám sát và bảo trì theo thời gian.

### Cấu trúc Dữ liệu

Tập dữ liệu con này chứa các bản ghi lịch sử bao gồm:

- Các khoảng telemetry trong quá khứ
- Các đợt cảnh báo đã xảy ra
- Dấu vết sự cố (incident traces)
- Các kịch bản bảo trì

Đây là nguồn dữ liệu chính phục vụ đối sánh ngữ nghĩa, phân tích dòng thời gian và so sánh bất thường.

Các thuộc tính chính bao gồm:

- `record_id`: định danh duy nhất của mẫu dữ liệu lịch sử
- `asset_id`: mã tài sản hạ tầng liên quan
- `timestamp_range`: khoảng thời gian được bao phủ bởi mẫu dữ liệu
- `event_sequence`: chuỗi sự kiện telemetry hoặc cảnh báo theo thứ tự thời gian
- `summary`: mô tả ngắn gọn về tình trạng được quan sát
- `labels`: các nhãn đánh giá hoặc phân loại đã chuẩn hóa
- `tags`: từ khóa được gán hoặc trích xuất mô tả tình huống
- `scenario_type`: bình thường, cảnh báo, sự cố hoặc bảo trì

Kho dữ liệu lịch sử này đặc biệt hữu ích cho:

- So sánh các mẫu cảnh báo lặp lại
- Đánh giá khả năng xử lý ngữ cảnh thời gian của hệ thống
- Xác minh khả năng truy xuất các tình huống tương tự trong quá khứ

---

## Dữ liệu Hồ sơ Chuyên gia Đánh giá (Supervisor Profile Data)

Trong mẫu gốc, phần này mô tả hồ sơ giảng viên hướng dẫn. Trong dự án này, nó được sử dụng để lưu thông tin về các chuyên gia và người gán nhãn tham gia xây dựng và đánh giá bộ dữ liệu.

### Cấu trúc Dữ liệu

Tập dữ liệu con này lưu trữ hồ sơ năng lực của các chuyên gia lĩnh vực, chuyên gia bảo trì hoặc người gán nhãn đánh giá đầu ra của hệ thống.

Các thuộc tính chính bao gồm:

- `reviewer_id`: định danh duy nhất của chuyên gia hoặc người gán nhãn
- `role_type`: chuyên gia lĩnh vực, người đánh giá hoặc người xác thực
- `expertise_area`: giám sát hệ thống, bảo trì hạ tầng, quy trình AR hoặc phân loại cảnh báo
- `review_scope`: phạm vi dữ liệu mà người đánh giá được phép xem xét
- `annotation_history`: lịch sử hoạt động gán nhãn
- `consistency_score`: chỉ số phản ánh độ ổn định trong việc gán nhãn

Thông tin này giúp minh bạch hóa quá trình xây dựng ground truth và đảm bảo chuyên môn của người đánh giá phù hợp với từng phần của bộ dữ liệu.

---

## Dữ liệu Rubric và Đánh giá (Rubric and Evaluation Data)

Phần này xác định khung đánh giá chuẩn hóa được sử dụng để đánh giá các mẫu dữ liệu và đầu ra của hệ thống. Nó thay thế rubric chấm điểm học thuật trong mẫu gốc bằng một bộ tiêu chí đánh giá phù hợp với các tác vụ giám sát và bảo trì có hỗ trợ AR.

### Cấu trúc Dữ liệu

Các thuộc tính chính bao gồm:

- `rubric_id`: mã định danh của phiếu đánh giá
- `criteria_weights`: trọng số của từng tiêu chí đánh giá
- `historical_scores`: điểm số được gán cho các mẫu hoặc đầu ra trước đó
- `reviewer_comments`: nhận xét định tính từ người đánh giá
- `label_standard`: bộ phân loại chuẩn cho cảnh báo, tài sản hoặc hành động bảo trì
- `agreement_status`: trạng thái đồng thuận của mẫu dữ liệu (được chấp nhận, tranh chấp hoặc chỉnh sửa)

Rubric được sử dụng để đánh giá:

- Mức độ liên quan của cảnh báo
- Độ chính xác trong nhận diện tài sản
- Mức độ hữu ích của ngữ cảnh bảo trì
- Tính nhất quán của đầu ra
- Mức độ phù hợp giữa phản hồi hệ thống và ground truth

---

## Các Bước Chuẩn bị Dữ liệu (Data Preparation Steps)

Pipeline chuẩn bị dữ liệu chuyển đổi các bản ghi thô từ nhiều nguồn thành bộ dữ liệu sạch phục vụ lưu trữ, truy xuất và đánh giá.

```text
[Raw Enveloped Events]
-> [Deserialize]
-> [Parse and Flatten]
-> [Cleanse and Normalize]
-> [Annotate / Enrich]
-> [Split]
```

### Làm sạch Dữ liệu (Data Cleaning)

Giai đoạn làm sạch loại bỏ hoặc sửa chữa:

- Các bản ghi sự kiện trùng lặp
- Payload không hợp lệ
- Tên trường dữ liệu không nhất quán
- Dấu thời gian không hợp lệ
- Thiếu định danh quan trọng
- Các trường dữ liệu nhiễu không cần thiết cho đánh giá

### Chuẩn hóa Văn bản và Metadata

Để đảm bảo khả năng sử dụng trong quá trình đánh giá và so sánh baseline, các thành phần sau được chuẩn hóa:

- Định dạng timestamp
- Hệ phân loại mức độ nghiêm trọng
- Quy ước đặt tên tài sản
- Định dạng tham chiếu QR hoặc marker
- Nhãn trạng thái cảnh báo và sự cố
- Đơn vị đo lường và thang giá trị khi cần thiết

### Chuyển đổi và Phân chia Dữ liệu

Sau khi xử lý, bộ dữ liệu được chia thành:

- **Tập huấn luyện hoặc hiệu chỉnh (Training/Calibration Set):** sử dụng khi cần tinh chỉnh mô hình hoặc thành phần xếp hạng.
- **Tập xác thực (Validation Set):** sử dụng để kiểm tra prompt, luật hoặc hành vi truy xuất trong quá trình phát triển.
- **Tập đánh giá (Evaluation Set):** dành riêng cho việc so sánh baseline và đánh giá cuối cùng.

Đối với telemetry phụ thuộc thời gian, việc phân chia dữ liệu phải tuân thủ thứ tự thời gian để tránh rò rỉ thông tin giữa các khoảng thời gian liền kề. Điều này đặc biệt quan trọng trong đánh giá cảnh báo và bất thường.

### Gán nhãn và Làm giàu Dữ liệu

Sau khi làm sạch dữ liệu, các bước xác thực thủ công và làm giàu bằng AI được áp dụng. Giai đoạn này tạo ra các nhãn ground truth hoặc nhãn tham chiếu dùng trong quy trình đánh giá.

Khi cần thiết, đầu ra của AI hoặc agent được giữ lại như các nhãn hỗ trợ, không được xem là sự thật cuối cùng (ground truth).

---

## Lưu ý về Quyền riêng tư và Đạo đức

Vì dự án được triển khai trong môi trường giám sát hạ tầng mô phỏng, bộ dữ liệu cần tránh tiết lộ thông tin cá nhân hoặc dữ liệu vận hành nhạy cảm. Các nguyên tắc sau được áp dụng:

- Sử dụng định danh tài sản giả lập hoặc đã được ẩn danh hóa khi có thể.
- Loại bỏ mọi thông tin nhận dạng cá nhân khỏi log và chú thích.
- Không lưu trữ mật khẩu, khóa bí mật hoặc token truy cập trong bộ dữ liệu.
- Xem các nhãn do AI sinh ra như thông tin hỗ trợ, không phải nguồn sự thật vận hành chính thức.
- Đảm bảo khả năng truy vết bằng cách duy trì mối liên kết rõ ràng giữa dữ liệu thô, dữ liệu đã chuyển đổi và nhãn đánh giá cuối cùng.

Nếu dữ liệu vận hành thực tế được sử dụng trong tương lai, dữ liệu đó phải được ẩn danh hóa hoàn toàn trước khi đưa vào tập đánh giá.
