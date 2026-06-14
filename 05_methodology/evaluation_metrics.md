# Các chỉ số đánh giá (Evaluation Metrics)

## Mục tiêu đánh giá

Khung đánh giá được thiết kế để đo lường nền tảng giám sát và bảo trì hạ tầng hỗ trợ AR theo bốn chiều vận hành chính:

- **Độ chính xác giám sát:** hệ thống có phát hiện đúng các sự kiện bất thường theo thời gian với độ chính xác (precision) và độ bao phủ (recall) đáng tin cậy hay không
- **Chất lượng truy xuất ngữ cảnh:** control plane có thể truy xuất đúng tài sản, cảnh báo hoặc ngữ cảnh bảo trì trong một thứ hạng (ranking) hữu ích hay không
- **Hiệu quả tác vụ AR:** WebAR có giúp cải thiện việc thực hiện bảo trì và trải nghiệm người dùng hay không
- **Hiệu năng hệ thống:** pipeline backend có đảm bảo phản hồi nhanh và mở rộng tốt dưới tải thực tế hay không

Các chỉ số được chọn phù hợp với kiến trúc hệ thống. Vì nền tảng kết hợp giám sát chuỗi thời gian, truy xuất dựa trên ranking, tương tác AR và xử lý backend thông lượng cao, nên việc đánh giá phải theo từng module thay vì một điểm số tổng quát.

---

## Phân chia module

Theo hướng dẫn đánh giá, cả bốn module đều liên quan đến hệ thống:

- **Module A: Phát hiện bất thường chuỗi thời gian & giám sát**
  - được kích hoạt vì hệ thống xử lý telemetry liên tục và sự kiện cảnh báo

- **Module B: Truy xuất ngữ cảnh & xếp hạng**
  - được kích hoạt vì control plane và BFF cần trả về ngữ cảnh liên quan

- **Module C: AR & hiệu suất tác vụ con người**
  - được kích hoạt vì giao diện hiện trường là WebAR dựa trên QR marker

- **Module D: Hiệu năng hệ thống & hạ tầng kỹ thuật**
  - bắt buộc vì hệ thống phụ thuộc ingestion, streaming, lưu trữ và truy vấn

Không phải tất cả metric đều được dùng trong mọi thí nghiệm. Mỗi thí nghiệm chỉ sử dụng tập metric phù hợp với module đang đánh giá, trong khi Module D luôn được kích hoạt xuyên suốt.

---

## Chỉ số giám sát và phát hiện bất thường chuỗi thời gian

Module này đánh giá khả năng phát hiện các cửa sổ telemetry bất thường và sự kiện cảnh báo.

### Precision và Recall theo vùng (Range-Based)

Vì bất thường trong hệ thống giám sát thường xảy ra theo khoảng thời gian thay vì một điểm đơn lẻ, nên không thể dùng metric point-wise truyền thống. Do đó sử dụng:

- **Range-Based Precision (P_R):** đo mức độ chồng lấn giữa vùng dự đoán và vùng bất thường thật
- **Range-Based Recall (R_R):** đo mức độ bao phủ của dự đoán lên toàn bộ vùng bất thường thật
- **Range-Based F1:** trung bình điều hòa giữa precision và recall theo vùng

Các metric này phù hợp hơn F1 điểm vì phản ánh đúng bản chất theo thời gian của cảnh báo.

---

### AUCPR và ROC-AUC

Để đánh giá chất lượng ngưỡng trong dữ liệu mất cân bằng:

- **AUCPR (Area Under Precision-Recall Curve):** chỉ số chính, đặc biệt khi anomaly hiếm
- **ROC-AUC:** dùng để so sánh độc lập ngưỡng

Trong dữ liệu telemetry mất cân bằng cao, AUCPR thường quan trọng hơn accuracy.

---

### Độ trễ phát hiện (Detection Delay)

Hệ thống cũng cần đo tính kịp thời:

[
\Delta t = t_{alert} - t_{onset}
]

Trong đó:

- `t_alert`: thời điểm hệ thống phát cảnh báo
- `t_onset`: thời điểm bắt đầu bất thường thực

Độ trễ càng thấp → hệ thống càng hữu ích trong vận hành thực tế.

---

### Tỷ lệ cảnh báo sai (False Alarm Rate)

Đo số cảnh báo không tương ứng với bất thường thật. Chỉ số này quan trọng vì hệ thống cảnh báo quá nhiều sẽ làm giảm độ tin cậy và gây mệt mỏi cho người vận hành.

---

## Chỉ số truy xuất ngữ cảnh và xếp hạng

Module này đánh giá khả năng control plane và BFF truy xuất đúng thông tin ngữ cảnh.

### Recall@k

Đo xem bao nhiêu phần tử đúng có nằm trong top-k kết quả. Quan trọng khi cần đủ bằng chứng cho giải thích cảnh báo hoặc hướng dẫn AR.

---

### HitRate@k

Kiểm tra xem phần tử đúng có xuất hiện trong top-k hay không. Dùng khi chỉ có một kết quả đúng chính.

---

### Mean Reciprocal Rank (MRR@k)

Đo vị trí xuất hiện của kết quả đúng đầu tiên:

[
MRR = \frac{1}{|Q|} \sum_{i=1}^{|Q|} \frac{1}{r_i}
]

Trong đó `r_i` là thứ hạng của kết quả đúng đầu tiên.

MRR quan trọng khi UI chỉ hiển thị một số ít kết quả.

---

### nDCG@k

Dùng khi mức độ liên quan có nhiều cấp độ:

- rất liên quan
- liên quan một phần
- không liên quan

Phù hợp với bài toán truy xuất context trong bảo trì vì không phải tất cả kết quả đều quan trọng như nhau.

---

## Chỉ số hiệu suất AR và tác vụ con người

Module này đánh giá WebAR có giúp cải thiện hiệu suất và trải nghiệm hay không.

---

### Thời gian hoàn thành tác vụ (Task Completion Time)

Đo thời gian từ lúc bắt đầu đến lúc hoàn thành nhiệm vụ. Đây là chỉ số trực tiếp nhất về hiệu quả workflow.

---

### Tỷ lệ hoàn thành tác vụ

Đo tỷ lệ nhiệm vụ được hoàn thành đúng mà không bị bỏ dở hoặc cần can thiệp lớn.

---

### Tỷ lệ lỗi

Đếm các lỗi vận hành như:

- thực hiện sai bước
- chọn sai tài sản
- bỏ sót bước kiểm tra
- hiểu sai ngữ cảnh

---

### Độ chính xác theo bước

Đo việc người dùng có làm đúng chuỗi bước hướng dẫn hay không trong workflow AR.

---

### NASA-TLX

Đo tải nhận thức theo 6 yếu tố:

- nhu cầu tinh thần
- nhu cầu thể chất
- áp lực thời gian
- hiệu suất
- mức độ nỗ lực
- mức độ khó chịu

Phù hợp vì AR nhằm giảm tải nhận thức khi bảo trì.

---

### System Usability Scale (SUS)

Thang đo khả năng sử dụng (0–100). Dùng để so sánh giữa WebAR và phương pháp truyền thống (giấy hướng dẫn hoặc non-AR).

---

### Đánh giá chuyên gia

Chuyên gia đánh giá mức độ hữu ích của context và hướng dẫn AR bằng thang Likert kèm nhận xét định tính.

---

## Chỉ số hiệu năng hệ thống

Module bắt buộc vì hệ thống dựa trên pipeline ingestion → streaming → storage.

---

### Độ trễ đầu-cuối (End-to-End Latency)

Đo thời gian từ lúc gửi telemetry hoặc request đến khi nhận kết quả cuối cùng.

---

### Thông lượng ingestion

Số sự kiện hệ thống xử lý được trong một đơn vị thời gian.

---

### Độ trễ xử lý stream

Đo khoảng thời gian từ lúc event vào Redpanda đến khi dữ liệu xử lý xong ở downstream.

---

### Độ trễ truy vấn

Đo thời gian phản hồi của control plane/BFF cho dashboard, AR lookup hoặc truy vấn telemetry.

---

### Phân vị độ trễ

Báo cáo:

- p50
- p95
- p99

Phân vị quan trọng hơn trung bình vì phản ánh “đuôi độ trễ” (tail latency).

---

### Thông lượng dưới tải

Kiểm tra hệ thống chịu được bao nhiêu request đồng thời trước khi hiệu năng giảm.

---

### Sử dụng tài nguyên

Trong tải cao, đo:

- CPU
- RAM
- áp lực lưu trữ
- độ đầy hàng đợi (queue/backlog)

---

## Quy trình báo cáo đánh giá

Kết quả nên được trình bày theo cấu trúc:

1. hiệu suất baseline
2. hiệu suất hệ thống đề xuất
3. mức cải thiện (delta)
4. giải thích ý nghĩa vận hành

Cách này giúp người đọc hiểu rõ giá trị thực tiễn.

---

## Ma trận tổng hợp benchmark

| Module        | Metric chính                                   | Baseline                     | Hệ thống đề xuất             |
| :------------ | :--------------------------------------------- | :--------------------------- | :--------------------------- |
| A: Monitoring | Range P/R, AUCPR, ROC-AUC, Detection Delay     | so sánh phát hiện cảnh báo   | đo chất lượng và độ kịp thời |
| B: Retrieval  | Recall@k, HitRate@k, MRR@k, nDCG@k             | so sánh chất lượng truy xuất | đo độ đúng ngữ cảnh          |
| C: AR Task    | TCT, Success Rate, Error Rate, NASA-TLX, SUS   | so sánh workflow người dùng  | đo hiệu quả AR               |
| D: System     | latency p50/p95/p99, throughput, lag, resource | so sánh overhead hệ thống    | đo khả năng chạy real-time   |
