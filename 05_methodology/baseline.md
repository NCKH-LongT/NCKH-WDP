# Baseline

## Mục đích nghiên cứu

Nghiên cứu này đánh giá nền tảng giám sát và bảo trì hạ tầng hỗ trợ AR được đề xuất bằng cách so sánh với ba baseline tham chiếu, đại diện cho các mức độ khác nhau của sự tham gia con người và hỗ trợ thuật toán. Mục tiêu của việc thiết kế baseline là thiết lập các ngưỡng hiệu năng thấp và trung gian có thể đo lường được đối với các tác vụ phân loại cảnh báo (alert triage), hiểu sự cố (incident understanding) và truy xuất thông tin phục vụ bảo trì trong môi trường trung tâm dữ liệu mô phỏng.

Các baseline được lựa chọn nhằm phản ánh đúng bối cảnh bài toán thực tế của dự án thay vì một tác vụ xử lý văn bản tổng quát. Cụ thể, việc so sánh tập trung vào khả năng của hệ thống trong việc xác định thông tin vận hành liên quan, hỗ trợ ra quyết định bảo trì và duy trì chất lượng đầu ra dưới các khối lượng công việc giám sát thực tế.

## 1. Baseline Đánh giá Thủ công (Manual Review Baseline)

### 1.1. Tổng quan và Mục tiêu

Baseline Đánh giá Thủ công đại diện cho một quy trình hoàn toàn do con người thực hiện. Trong thiết lập này, người đánh giá kiểm tra các bản tóm tắt telemetry, ngữ cảnh tài sản (asset context), mô tả cảnh báo và ghi chú sự cố mà không có cơ chế xếp hạng tự động hoặc làm giàu dữ liệu bằng AI. Baseline này xác định giới hạn trên về khả năng diễn giải của con người và giới hạn dưới thực tế của tự động hóa.

Mục tiêu chính của baseline là xây dựng bộ tham chiếu ground truth cho tập đánh giá. Các chuyên gia đánh giá sẽ xác minh liệu một cảnh báo có cần hành động hay không, tài sản liên quan có được xác định chính xác hay không, và cách diễn giải phục vụ bảo trì có hợp lệ hay không.

### 1.2. Quy trình

Quy trình đánh giá thủ công tuân theo luồng tuyến tính sau:

```text
[Xây dựng hướng dẫn] -> [Lựa chọn mẫu] -> [Đánh giá độc lập] -> [Đối soát] -> [Ground Truth]
```

Các bước thực hiện như sau:

* **Xây dựng hướng dẫn:** Một bộ tiêu chí đánh giá được xác định trước khi bắt đầu gán nhãn. Bộ tiêu chí quy định cách đánh giá mức độ liên quan của cảnh báo, đối sánh tài sản, liên kết sự cố và mức độ ưu tiên bảo trì.
* **Lựa chọn mẫu:** Một tập con đại diện được trích xuất từ toàn bộ dữ liệu. Mẫu phải bao gồm các điều kiện hoạt động bình thường, các giai đoạn telemetry bất thường, các cảnh báo lặp lại và các trường hợp biên liên quan đến bảo trì.
* **Đánh giá độc lập:** Ít nhất hai người đánh giá xem xét từng mẫu một cách độc lập. Họ sử dụng cùng nguồn dữ liệu nhưng không nhìn thấy nhãn của nhau trong lần đánh giá đầu tiên.
* **Đối soát:** Các bất đồng được giải quyết thông qua thảo luận hoặc bởi một chuyên gia cấp cao hơn. Nhãn cuối cùng được thống nhất sẽ trở thành ground truth cho các phép so sánh sau này.

### 1.3. Vai trò trong đánh giá

Baseline này không được thiết kế để tối ưu hiệu suất. Thay vào đó, nó cung cấp nguồn tham chiếu đáng tin cậy nhất về tính chính xác, tính nhất quán của nhãn và khả năng diễn giải ngữ nghĩa. Nó đặc biệt hữu ích để xác định liệu hệ thống đề xuất có thể đưa ra cùng một quyết định với ít thời gian và công sức vận hành hơn hay không.

## 2. Baseline Truy xuất Dựa trên Luật (Rule-Based Retrieval Baseline)

### 2.1. Tổng quan và Mục tiêu

Baseline Truy xuất Dựa trên Luật đại diện cho cách tiếp cận truyền thống không sử dụng mô hình ngôn ngữ lớn (LLM). Hệ thống sử dụng các luật xác định, đối sánh từ khóa và các heuristic cố định để truy xuất thông tin vận hành phù hợp nhất từ dữ liệu hiện có. Baseline này mô phỏng một hệ thống hỗ trợ đơn giản có thể hỗ trợ công tác bảo trì mà không cần khả năng suy luận ngữ nghĩa sâu.

Baseline này có giá trị vì đại diện cho một phương pháp truyền thống dễ triển khai, dễ giải thích và chi phí vận hành thấp. Tuy nhiên, nó gặp hạn chế khi xử lý các mô tả telemetry nhiễu, các cảnh báo có cách diễn đạt mơ hồ và các mối quan hệ liên thực thể giữa tài sản, sự cố và các quan sát lịch sử.

### 2.2. Quy trình

Pipeline dựa trên luật bao gồm các bước:

1. **Chuẩn hóa văn bản và metadata:** Các bản ghi đầu vào được chuẩn hóa thông qua chuyển thành chữ thường, làm sạch token và chuẩn hóa các trường dữ liệu.
2. **Đối sánh heuristic:** Hệ thống áp dụng các quy tắc xác định để đối chiếu cảnh báo hoặc truy vấn với tên tài sản, thẻ (tag), loại sự kiện và các mẫu lỗi đã biết.
3. **Chấm điểm ưu tiên:** Một hàm chấm điểm cố định xếp hạng các kết quả ứng viên dựa trên mức độ trùng khớp văn bản, sự hiện diện của trường dữ liệu và các quy tắc nghiệp vụ được xác định trước.
4. **Lựa chọn kết quả:** Ứng viên có điểm cao nhất được trả về như câu trả lời dự đoán hoặc bản ghi được đề xuất.

### 2.3. Vai trò trong đánh giá

Baseline này cung cấp một chuẩn tham chiếu mạnh về tính minh bạch. Nó giúp đo lường mức độ cải thiện khi hệ thống được đề xuất vượt ra ngoài logic cố định để tận dụng các thành phần kiến trúc nâng cao như event streaming, phân tích dữ liệu suy diễn và làm giàu bằng AI.

## 3. Baseline Chỉ Sử dụng LLM (LLM-Only Baseline)

### 3.1. Tổng quan và Mục tiêu

Baseline Chỉ Sử dụng LLM đại diện cho cách tiếp cận AI sinh sinh hiện đại nhưng không sử dụng cơ chế truy xuất dữ liệu bên ngoài hoặc điều phối hệ thống. Mô hình nhận trực tiếp đầu vào của bài toán và tạo ra câu trả lời cuối cùng chỉ dựa trên kiến thức tham số nội tại cùng ngữ cảnh được cung cấp trong prompt.

Trong phạm vi dự án này, baseline được sử dụng để đo lường khả năng của một mô hình ngôn ngữ độc lập trong việc diễn giải văn bản liên quan đến giám sát hệ thống, tóm tắt trạng thái vận hành hoặc đề xuất kết luận phục vụ bảo trì mà không có quyền truy cập vào toàn bộ kiến trúc control plane và data plane.

### 3.2. Quy trình

Quy trình LLM-only được tổ chức như sau:

```text
[Xây dựng Prompt] -> [Suy luận một lần] -> [Chuẩn hóa đầu ra] -> [So sánh chỉ số]
```

Các giả định triển khai bao gồm:

* **Xây dựng Prompt:** Prompt áp đặt vai trò cụ thể, định dạng trả lời cố định và yêu cầu chỉ tạo một phản hồi duy nhất.
* **Suy luận một lần:** Mỗi mẫu đánh giá được gửi độc lập đến mô hình, không truy xuất dữ liệu từ hệ thống lưu trữ, không sử dụng công cụ hỗ trợ và không ghi nhớ các câu trả lời trước đó.
* **Chuẩn hóa đầu ra:** Văn bản trả về được chuyển đổi sang định dạng chuẩn để có thể so sánh với ground truth.

### 3.3. Vai trò trong đánh giá

Baseline này đo lường khả năng suy luận và tóm tắt thuần túy của mô hình. Nó cung cấp một điểm tham chiếu hữu ích khi so sánh với hệ thống đề xuất vì cho phép tách biệt giá trị của kiến trúc nền tảng, đặc biệt là lợi ích đến từ lưu trữ telemetry, xử lý sự kiện và truy xuất ngữ cảnh.

## 4. Baseline Hệ thống Đề xuất (Proposed System Baseline)

### 4.1. Tổng quan và Mục tiêu

Baseline Hệ thống Đề xuất là kiến trúc hoàn chỉnh được phát triển trong dự án này. Đây không phải là một mô hình tối giản mà là một nền tảng tích hợp kết hợp điều phối control plane, event streaming, phân tích telemetry, làm giàu dữ liệu bằng AI và truy cập vận hành thông qua AR.

Hệ thống được xây dựng dựa trên các lựa chọn kiến trúc sau:

* `NestJS` đóng vai trò control plane và lớp BFF
* `Redpanda` làm nền tảng event backbone cho truyền tải bất đồng bộ
* `ClickHouse` làm kho dữ liệu phân tích cho lịch sử telemetry và dữ liệu vận hành có thể truy vấn
* `MongoDB` lưu trữ dữ liệu vận hành theo phạm vi dịch vụ khi phù hợp
* `Redis` lưu trạng thái suy diễn phục vụ truy cập nhanh và bộ nhớ đệm nóng (hot cache)
* WebAR kết hợp tương tác dựa trên mã QR làm giao diện cho nhân sự hiện trường

Baseline này được đưa vào nhằm đo lường lợi ích tổng thể của toàn bộ kiến trúc thay vì chỉ đánh giá đóng góp của một thuật toán đơn lẻ.

### 4.2. Quy trình

Hệ thống đề xuất xử lý các mẫu đánh giá theo chuỗi sau:

```text
[Đầu vào / Truy vấn] -> [Điều phối Control Plane] -> [Truy xuất ngữ cảnh]
-> [Truy cập dữ liệu hoặc sự kiện]
-> [Làm giàu bằng AI khi cần] -> [Phản hồi cuối cùng]
```

Hệ thống có thể tham chiếu:

* ngữ cảnh tài sản và dữ liệu topology
* lịch sử telemetry được lưu trữ để phục vụ truy vấn phân tích
* các monitoring read model và trạng thái cảnh báo
* hồ sơ quy trình xử lý sự cố
* tín hiệu rủi ro hoặc dữ liệu làm giàu do AI tạo ra

### 4.3. Vai trò trong đánh giá

Đây là đối tượng nghiên cứu chính của đề tài. Hệ thống được so sánh với các baseline thủ công, dựa trên luật và LLM-only nhằm xác định liệu kiến trúc có cải thiện được:

* độ chính xác của câu trả lời
* độ trễ vận hành
* thông lượng dưới tải thực tế
* tính nhất quán của định dạng đầu ra
* mức độ hữu ích đối với các tác vụ giám sát và bảo trì

## 5. Tiêu chí So sánh

Bốn baseline được so sánh theo các khía cạnh sau.

### 5.1. Độ chính xác và Chất lượng Quyết định

Độ chính xác được đo lường dựa trên ground truth đã được chuyên gia xác nhận. Tùy thuộc vào loại tác vụ, các chỉ số có thể bao gồm:

* Precision
* Recall
* F1-score
* Exact Match
* Top-k Retrieval Accuracy

Các chỉ số này được sử dụng để đánh giá liệu hệ thống có xác định đúng tài sản, cảnh báo, sự cố hoặc diễn giải bảo trì hay không.

### 5.2. Độ trễ và Thông lượng

Hiệu năng được đánh giá thông qua:

* độ trễ phản hồi trung bình
* thời gian xử lý đầu cuối (end-to-end)
* thông lượng dưới các yêu cầu theo lô hoặc lặp lại

Các chỉ số này đặc biệt quan trọng đối với hệ thống đề xuất vì kiến trúc phụ thuộc vào event streaming và khả năng truy vấn phân tích.

### 5.3. Chi phí Vận hành

Chi phí vận hành được so sánh theo tương quan:

* chi phí đánh giá thủ công được đo bằng công sức con người
* chi phí của hệ thống dựa trên luật chủ yếu là tài nguyên tính toán nhẹ
* chi phí LLM-only phụ thuộc vào mức sử dụng mô hình
* chi phí của hệ thống đề xuất được đo bằng tài nguyên tính toán, lưu trữ và chi phí truy vấn của nền tảng

### 5.4. Tính Vững chắc và Chất lượng Đầu ra

Tính vững chắc được đánh giá dựa trên:

* mức độ tuân thủ định dạng
* tính ổn định trên các đầu vào lặp lại
* khả năng chống hiện tượng hallucination hoặc các khẳng định không có cơ sở
* khả năng duy trì thuật ngữ chuyên ngành

Khía cạnh này đặc biệt quan trọng vì hệ thống được kỳ vọng hỗ trợ ra quyết định vận hành, nơi mà các đầu ra thiếu nhất quán hoặc không đầy đủ có thể làm giảm mức độ tin cậy.

## 6. Bảng Tóm tắt So sánh Baseline

| Baseline                | Vai trò trong nghiên cứu                | Điểm mạnh                                         | Hạn chế                                                   |
| ----------------------- | --------------------------------------- | ------------------------------------------------- | --------------------------------------------------------- |
| Đánh giá thủ công       | Xây dựng ground truth                   | Khả năng diễn giải và độ tin cậy nhãn cao nhất    | Chậm và tốn kém                                           |
| Truy xuất dựa trên luật | Chuẩn tham chiếu heuristic truyền thống | Minh bạch và chi phí thấp                         | Kém hiệu quả với dữ liệu mơ hồ và ngữ cảnh phức tạp       |
| Chỉ sử dụng LLM         | Chuẩn tham chiếu AI sinh sinh thuần túy | Suy luận ngữ nghĩa linh hoạt                      | Không có truy xuất dữ liệu hoặc nền tảng kiến trúc hỗ trợ |
| Hệ thống đề xuất        | Giải pháp chính được đánh giá           | Tích hợp ngữ cảnh, phân tích dữ liệu và hỗ trợ AI | Độ phức tạp kiến trúc cao                                 |
