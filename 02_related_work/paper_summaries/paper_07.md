# Tóm tắt Bài báo 19

## Trích dẫn

Norouzi, R., et al. (2025). *Capturing causal claims: A fine-tuned text mining model for extracting causal sentences from social science papers*. Research Synthesis Methods.
doi.org/10.1017/rsm.2024.13

## Vấn đề nghiên cứu

Bài báo giải quyết một thách thức quan trọng trong tổng hợp kiến thức khoa học: **các tuyên bố về nhân quả thường mơ hồ trong văn phong khoa học**, dẫn đến:
- Khó khăn trong việc tổng hợp lý thuyết một cách chính xác
- Khó khăn trong việc kiểm chứng và so sánh các giả thuyết giữa các tác giả khác nhau
- Mất mát thông tin cấu trúc về cách các khái niệm liên kết với nhau

Ví dụ, một câu như "Sự hợp tác có liên quan đến kết quả tốt" có thể được diễn giải theo nhiều cách khác nhau. Câu hỏi đặt ra là: làm sao có thể **tự động trích xuất và chuẩn hóa các tuyên bố nhân quả** từ các bài báo khoa học để phục vụ cho tổng hợp lý thuyết và xây dựng kiến thức toàn cầu?

## Phương pháp

Tác giả đề xuất một phương pháp sử dụng **tinh chỉnh các mô hình Transformer hiện đại** với các bước sau:

1. **Chọn các mô hình nền tảng**:
   - **BERT**: Mô hình Transformer tiêu chuẩn
   - **SciBERT**: Mô hình BERT được đào tạo lại trên dữ liệu khoa học
   - **RoBERTa**: Phiên bản cải tiến của BERT với hiệu suất tốt hơn

2. **Sử dụng kỹ thuật tinh chỉnh hiệu quả (Efficient Fine-tuning)**:
   - **QLoRA (Quantized Low-Rank Adaptation)**: Một kỹ thuật giảm bớt số lượng tham số cần được tinh chỉnh, giúp giảm yêu cầu bộ nhớ GPU
   - Cho phép tinh chỉnh các mô hình lớn trên phần cứng giới hạn

3. **Nhiệm vụ phân loại**:
   - Phân loại mỗi câu thành hai lớp: **chứa khẳng định nhân quả** hoặc **không chứa**
   - Trích xuất từ toàn văn bài báo, không chỉ từ tóm tắt

## Dữ liệu

Nghiên cứu sử dụng:
- **Tập dữ liệu CODA (Cooperation Databank)**: Một kho dữ liệu được thiết kế đặc biệt cho các nghiên cứu khoa học xã hội
- **1.058 câu được chú thích thủ công** phân thành:
  - Câu chứa khẳng định nhân quả (causal sentences)
  - Câu không chứa khẳng định nhân quả (non-causal sentences)
- Dữ liệu từ các bài báo khoa học xã hội trong nhiều miền khác nhau

## Đánh giá

Phương pháp được đánh giá thông qua:
- **F1 Macro Score**: Trung bình F1 của cả hai lớp, đảm bảo đánh giá công bằng cho các lớp dữ liệu không cân bằng
- **Phân tích sai số (Error Analysis)**: Kiểm tra chi tiết các trường hợp mà mô hình dự đoán sai, đặc biệt là các câu mơ hồ
- **Xác thực chéo (Cross-validation)**: Kiểm tra hiệu suất trên các tập dữ liệu khác nhau
- **So sánh các mô hình**: So sánh hiệu suất giữa BERT, SciBERT, và RoBERTa

## Kết quả

Bài báo đạt được những kết quả quan trọng:

- **SciBERT tinh chỉnh là mô hình tốt nhất**: **SciBERT được tinh chỉnh trên dữ liệu gộp (pooled data) đạt hiệu suất cân bằng nhất với F1 macro score = 0.85**

- **Hiệu suất vượt trội**: Kết quả này cho thấy rằng:
  - Việc sử dụng mô hình được đào tạo lại trên dữ liệu khoa học (SciBERT) tốt hơn các mô hình tổng quát (BERT)
  - QLoRA là một kỹ thuật tinh chỉnh hiệu quả cho phép huấn luyện tốt hơn

- **Phát hiện hiện tượng "lệch miền" (Domain Shift Bias)**:
  - Mô hình hoạt động khác nhau trên dữ liệu từ các miền khác nhau của khoa học xã hội
  - Phát hiện này rất quan trọng vì chỉ ra rằng trích xuất nhân quả phụ thuộc vào ngữ cảnh miền

- **Khả năng xử lý câu mơ hồ**: Phân tích sai số cho thấy mô hình có thể phân biệt được giữa các câu nhân quả rõ ràng và mơ hồ

## Hạn chế

Bài báo có một số hạn chế cần lưu ý:

- **Chỉ nhận diện ở mức độ câu**: Phương pháp chỉ xác định xem một câu có chứa khẳng định nhân quả hay không, nhưng chưa xác định được:
  - Loại nhân quả (ví dụ: dẫn đến, gây ra, ảnh hưởng đến)
  - Độ mạnh của mối quan hệ
  - Điều kiện hoặc hạn chế của nhân quả

- **Chưa xác định hướng nhân quả**: Mô hình không phân biệt được:
  - Nhân quả tích cực (X dẫn đến Y tốt)
  - Nhân quả tiêu cực (X dẫn đến Y xấu)
  - Hoặc đơn giản là không xác định được hướng (X ảnh hưởng đến Y, nhưng chiều hướng không rõ)

- **Phụ thuộc vào chất lượng dữ liệu chú thích**: Hiệu suất phụ thuộc vào độ chính xác của các chú thích thủ công trong CoDa

- **Giới hạn địa chỉ miền**: Được huấn luyện chủ yếu trên khoa học xã hội, có thể cần điều chỉnh cho các miền khác

## Mức độ liên quan tới đề tài của nhóm

Bài báo có **mức độ liên quan cao** tới đề xuất của nhóm vì những lý do sau:

- **Vượt ra ngoài từ khóa**: Cho phép hệ thống của nhóm **theo dõi sự thay đổi trong các giả thuyết và cơ chế lý thuyết** (không chỉ là từ khóa), cung cấp cái nhìn sâu hơn về sự tiến hóa của một lĩnh vực

- **Hiểu rõ hơn về mối quan hệ**: Thay vì chỉ biết rằng "Công nghệ X đang hot", hệ thống có thể biết "Công nghệ X được giả thuyết là giải pháp cho Vấn đề Y"

- **Xây dựng các mối liên kết khái niệm**: Những tuyên bố nhân quả được trích xuất có thể được sử dụng để xây dựng các liên kết giữa các khái niệm, công nghệ và vấn đề

- **Ứng dụng cho bảo trì công nghiệp**: Tương tự, hệ thống có thể trích xuất các khẳng định nhân quả từ báo cáo bảo trì, tài liệu kỹ thuật để hiểu cơ chế và nguyên nhân của các vấn đề

- **Kỹ thuật QLoRA**: Phương pháp tinh chỉnh hiệu quả này có thể được áp dụng cho các mô hình ngôn ngữ lớn khác để tinh chỉnh chúng trên dữ liệu miền cụ thể mà không cần GPU siêu mạnh

## Hướng cải tiến khả dĩ

Để mở rộng và cải thiện phương pháp này cho dự án của nhóm, có thể xem xét:

- **Tích hợp nhận diện nhân quả xuyên câu (Cross-sentence Causal Recognition)**:
  - Mở rộng từ phân loại mức độ câu sang nhận diện các mối quan hệ nhân quả xuyên nhiều câu
  - Ví dụ: "Phương pháp A được đề xuất. Nó cải thiện hiệu suất B." → Nhận diện "A dẫn đến cải thiện B"
  - Sử dụng các kỹ thuật như coreference resolution, semantic role labeling

- **Xác định hướng và loại nhân quả**:
  - Mở rộng từ phân loại nhị nguyên (causal vs non-causal) sang phân loại đa lớp (dẫn đến, gây ra, liên quan đến, v.v.)
  - Xác định hướng nhân quả (tích cực hay tiêu cực)
  - Ước tính độ mạnh của mối quan hệ

- **Xây dựng Đồ thị có hướng không chu trình (DAG - Directed Acyclic Graph)**:
  - Sử dụng các tuyên bố nhân quả được trích xuất để xây dựng các DAG thể hiện mối quan hệ nhân quả toàn diện giữa các khái niệm
  - Cho phép phân tích nguyên nhân tổng hợp (causal inference) và xác định các điểm can thiệp quan trọng
  - Có thể sử dụng các công cụ như pgmpy, CausalML

- **Phân tích sự tiến hóa của các mối quan hệ nhân quả theo thời gian**:
  - Theo dõi cách các giả thuyết nhân quả thay đổi theo thời gian trong một lĩnh vực
  - Xác định các giả thuyết đã bị bác bỏ, được xác nhận hoặc vẫn chưa được giải quyết
  - Phát hiện các "lỗ hổng" nhân quả mà chưa có giả thuyết nào giải thích

- **Ứng dụng cho bảo trì công nghiệp**:
  - Điều chỉnh phương pháp để trích xuất các khẳng định nhân quả từ báo cáo bảo trì: "Lỗi X được gây ra bởi Nguyên nhân Y"
  - Xây dựng các mô hình nhân quả về các lỗi phổ biến và cách khắc phục

- **Kết hợp với các mô hình ngôn ngữ lớn (LLM)**:
  - Sử dụng các LLM hiện đại (GPT-4, Claude) để cải thiện chất lượng trích xuất nhân quả
  - Áp dụng prompt engineering để hướng dẫn LLM trích xuất các loại tuyên bố nhân quả cụ thể
  - Sử dụng in-context learning để học mẫu từ các ví dụ

- **Xác thực chuyên gia và phản hồi người dùng**:
  - Thiết lập quy trình cho các chuyên gia miền để xác thực các tuyên bố nhân quả được trích xuất
  - Sử dụng phản hồi để tiếp tục cải thiện mô hình
