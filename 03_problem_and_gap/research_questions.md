# Research Questions (Câu hỏi nghiên cứu)

Để định hướng chi tiết cho các thử nghiệm kỹ thuật và đánh giá thực nghiệm của dự án **SmartStay AI**, nhóm nghiên cứu thiết lập **3 Câu hỏi nghiên cứu (Research Questions - RQs)** cốt lõi dưới đây. Mỗi câu hỏi nghiên cứu đều đi kèm với lý do khoa học, phương pháp đo lường và kỳ vọng kết quả:

---

## RQ1. Độ chính xác của Chatbot RAG (Accuracy & Hallucination Prevention)

> [!NOTE]
> **English:** *How accurately can the proposed RAG-based booking chatbot answer hotel-specific queries and prevent information hallucination compared to a standard LLM-only chatbot?*
> 
> **Vietnamese:** *Mô hình chatbot đặt phòng dựa trên kiến trúc RAG đề xuất có thể trả lời các câu hỏi đặc thù của khách sạn và ngăn chặn ảo tưởng thông tin chính xác đến mức nào so với chatbot chỉ sử dụng LLM tiêu chuẩn?*

### 1. Bối cảnh & Lý do (Context & Motivation)
Khách hàng đặt phòng khách sạn luôn yêu cầu thông tin tuyệt đối chính xác về giá phòng, trạng thái phòng trống và các tiện ích đi kèm (Bài 06). Chatbot LLM thông thường rất dễ tự sinh (ảo tưởng) các thông số này dựa trên trọng số huấn luyện, gây ra hiểu lầm nghiêm trọng. RQ1 được đặt ra để kiểm chứng tính hiệu quả của pipeline RAG (đồng bộ database thời gian thực) trong việc kiểm soát độ chính xác của câu trả lời.

### 2. Phương pháp đánh giá (Evaluation Methodology)
Chúng tôi sẽ xây dựng một bộ câu hỏi kiểm thử (ví dụ: 150 - 200 câu hỏi đa dạng về đặt phòng, hỏi giá, kiểm tra tiện ích) và chạy thử nghiệm đối chiếu chéo giữa hai cấu hình:
- **Hệ thống đề xuất:** Chatbot RAG kết nối Database thời gian thực qua Vector DB (Pinecone) sử dụng mô hình nhúng kích thước lớn (Multilingual-E5-Large) kết hợp GPT-4.1-mini.
- **Hệ thống so sánh (Baseline):** Chatbot sử dụng LLM thuần túy (GPT-4o-mini hoặc Claude Haiku) với prompt hướng dẫn thông thường không có dữ liệu RAG.

### 3. Metric đo lường (Metrics)
- **Retrieval Phase:** Precision, Recall, F1-Score của tài liệu ngữ cảnh được truy xuất.
- **Generation Phase:** BERTScore F1 (độ tương đồng ngữ nghĩa), BLEU-2 (độ khớp từ vựng).
- **Hiệu suất thời gian:** Avg Latency (Thời gian phản hồi trung bình tính bằng giây).

---

## RQ2. Hiệu quả của Phân tích cảm xúc khía cạnh (Aspect-Based Sentiment Analysis)

> [!NOTE]
> **English:** *How effectively can the integrated aspect-based sentiment analysis model identify customer experience trends and operational pain points from raw reviews compared to manual categorization?*
> 
> **Vietnamese:** *Mô hình phân tích cảm xúc theo khía cạnh tích hợp trong hệ thống có thể nhận diện các xu hướng trải nghiệm và điểm nghẽn vận hành từ các đánh giá thô của khách hàng hiệu quả như thế nào so với việc phân loại thủ công của con người?*

### 1. Bối cảnh & Lý do (Context & Motivation)
Phản hồi của khách hàng thường chứa các ý kiến hỗn hợp (ví dụ: khen phòng ngủ sạch sẽ nhưng chê phục vụ chậm). Phân tích cảm xúc văn bản thông thường (Bài 02) chỉ dán nhãn tích cực/tiêu cực chung chung, không thể chỉ ra chính xác vấn đề vận hành nằm ở đâu. RQ2 kiểm tra năng lực của LLM trong việc tự động phân tách và dán nhãn cảm xúc theo từng khía cạnh dịch vụ cụ thể trên Dashboard.

### 2. Phương pháp đánh giá (Evaluation Methodology)
Thu thập một tập mẫu bài đánh giá thực tế (khoảng 300 - 500 bài review thô trên các trang OTA). Tiến hành đối chiếu chéo kết quả phân tích giữa:
- **Hệ thống đề xuất:** Module AI tự động phân loại cảm xúc theo 4 khía cạnh: *Vệ sinh phòng*, *Thái độ phục vụ*, *Tiện nghi phòng*, và *Giá cả*.
- **Hệ thống so sánh (Baseline):** Kết quả dán nhãn thủ công độc lập bởi hai chuyên gia/lễ tân khách sạn làm chuẩn (Ground Truth).

### 3. Metric đo lường (Metrics)
- **Độ chính xác phân loại khía cạnh:** Precision, Recall, F1-Score cho từng nhãn khía cạnh và nhãn cảm xúc tương ứng.
- **Độ tin cậy xuyên đánh giá viên:** Chỉ số Cohen's Kappa để đo độ đồng thuận giữa AI và con người.

---

## RQ3. Tính tối ưu hóa quy trình và hiệu quả kinh tế (Operational & Economic Efficiency)

> [!NOTE]
> **English:** *How much time and cost can the proposed SaaS platform save for small and mid-sized hotel operations compared to traditional manual booking and customer care workflows?*
> 
> **Vietnamese:** *Nền tảng SaaS đề xuất có thể tiết kiệm bao nhiêu thời gian và chi phí cho các hoạt động vận hành của khách sạn vừa và nhỏ so với các quy trình quản lý bằng sổ sách và chăm sóc khách hàng thủ công truyền thống?*

### 1. Bối cảnh & Lý do (Context & Motivation)
Mục tiêu tối thượng của bất kỳ ứng dụng công nghệ nào là mang lại giá trị kinh tế thực tiễn (Bài 03, 11). Đối với các khách sạn vừa và nhỏ có ngân sách eo hẹp, việc chứng minh hệ thống giúp giảm khối lượng công việc, hạn chế overbooking và tối ưu hóa chi phí vận hành là điều kiện tiên quyết để họ chấp nhận cài đặt phần mềm.

### 2. Phương pháp đánh giá (Evaluation Methodology)
Thực hiện chạy thử nghiệm mô phỏng quy trình vận hành thực tế tại 2 - 3 khách sạn đối tác quy mô vừa và nhỏ trong vòng 2 tuần:
- **Tuần 1 (Manual Workflow):** Khách sạn vận hành theo cách truyền thống (trực chat thủ công, ghi sổ sách đặt phòng, cập nhật phòng tay).
- **Tuần 2 (SmartStay AI Workflow):** Kích hoạt hệ thống SmartStay AI (Chatbot AI trực tin nhắn 24/7, tự động đồng bộ phòng trống, Dashboard báo cáo tự động).

### 3. Metric đo lường (Metrics)
- **Workload Reduction:** Tổng số giờ nhân viên phải dành ra để trực chat và giải đáp câu hỏi của khách (kỳ vọng giảm 40% - 50%).
- **Response Speed:** Thời gian trung bình để khách hàng nhận được câu trả lời hoàn chỉnh (kỳ vọng giảm từ vài chục phút xuống dưới 2 giây).
- **Error Rate:** Số lỗi trùng phòng (overbooking) xảy ra trong quá trình vận hành (kỳ vọng giảm về 0).
- **Direct Booking Rate:** Tỷ lệ đơn đặt phòng trực tiếp qua kênh app/web của khách sạn so với kênh OTA (kỳ vọng tăng 15% - 20%).
