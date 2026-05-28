**Tên bài:** Multimodal Intelligent Perception at an Intersection: Pedestrian and Vehicle Flow Dynamics Using a Pipeline-Based Traffic Analysis System.

**Tác giả:** Bao Rong Chang, Hsiu-Fen Tsai, và Chen-Chia Chen.

**Năm:** 2026.

**Nguồn:** Tạp chí Electronics, thuộc nhà xuất bản MDPI.

**DOI/Link:** https://doi.org/10.3390/electronics15020353.

**Problem**
**Bài báo giải quyết vấn đề gì?**
Bài báo giải quyết những **hạn chế của các hệ thống giám sát giao thông truyền thống** tại các nút giao, bao gồm chi phí cao, khó bảo trì, phạm vi bao phủ không đủ, khả năng tích hợp dữ liệu đa phương thức kém và hạn chế trong việc phân tích thông tin giao thông. Ngoài ra, các mô hình dựa trên quy tắc hoặc thống kê truyền thống thường thất bại trong việc đưa ra các quyết định chính xác, theo thời gian thực dưới các điều kiện giao thông phức tạp và thay đổi liên tục.

**Method**
**Bài báo dùng phương pháp/model/hệ thống nào?**
Nghiên cứu đề xuất một **Hệ thống phân tích giao thông dựa trên quy trình (Pipeline-based Traffic Analysis System - PTAS)** dựa trên AI, tích hợp nhiều công nghệ tiên tiến:
*   **Thị giác máy tính (Computer Vision):** Sử dụng mô hình nhận diện đối tượng YOLOv11, cụ thể là phiên bản cải tiến **DuCRG-YOLOv11n** kết hợp cấu trúc Reparameterization Ghost (RG) để giảm tính toán dư thừa, Dual Convolution (DuC), và hàm kích hoạt mới $\beta_{silu}$ nhằm tăng tốc độ và độ nhạy nhận diện đối tượng nhỏ.
*   **Theo dõi đa đối tượng (Multi-Object Tracking):** Sử dụng thuật toán **ByteTrack** và **DeepSORT** để thiết lập quỹ đạo di chuyển liên tục của xe cộ và người đi bộ.
*   **Xử lý ngôn ngữ tự nhiên và Dữ liệu:** Ứng dụng kỹ thuật **Tạo lập tăng cường truy xuất (RAG thông qua Vertex AI)** kết hợp với các **Mô hình ngôn ngữ lớn (LLMs)** như GPT-4o, Claude Sonnet 4, Gemini-2.5-flash để phân tích ngữ nghĩa, giải thích ngữ cảnh ùn tắc từ dữ liệu đa phương thức.

**Dataset**
**Bài báo dùng dữ liệu gì?**
Bài báo sử dụng sự kết hợp của nhiều nguồn dữ liệu:
*   **Dữ liệu tiền huấn luyện (Pre-training):** Bộ dữ liệu Traffic Detection Project từ Kaggle với **6.633 hình ảnh** giám sát giao thông chất lượng cao (nhận diện xe cộ, người đi bộ, biển báo) ở nhiều điều kiện môi trường.
*   **Dữ liệu học chuyển giao (Transfer learning):** **1.000 hình ảnh** giao thông thực tế được thu thập trong giờ cao điểm (tháng 6 đến tháng 7 năm 2025) tại hai nút giao ở thành phố Cao Hùng, Đài Loan.
*   **Dữ liệu môi trường và đô thị:** Các dữ liệu thời gian thực về sự cố tai nạn giao thông, thông tin đào đường/công trình, chất lượng không khí (chỉ số AQI, PM2.5/PM10), và dữ liệu quan trắc tiếng ồn (dB) từ các API nền tảng dữ liệu mở của thành phố Cao Hùng.

**Evaluation**
**Bài báo đánh giá bằng metric nào?**
*   **Mô hình nhận diện (Object Detection):** Đánh giá qua Tốc độ khung hình/giây (**FPS**), Độ chính xác (**Precision**), Độ phủ (**Recall**), và Điểm F1 (**F1-score**).
*   **Theo dõi đối tượng (Tracking):** Đánh giá qua Độ chính xác theo dõi đa đối tượng (**MOTA**), Điểm F1 nhận diện duy trì (**IDF1**), và Độ chuẩn xác theo dõi đa đối tượng (**MOTP**).
*   **Mô hình LLMs:** Đánh giá dựa trên 10 yếu tố định tính bao gồm: Mô tả dữ liệu, Phân tích giờ cao điểm, Nguyên nhân ùn tắc, Phân tích tai nạn, Tác động của công trình, Chất lượng không khí, Tiếng ồn, Nhận diện dữ liệu thiếu sót, Cấu trúc logic, và Các đề xuất cải thiện.

**Results**
**Kết quả chính là gì?**
*   **Nhận diện ấn tượng:** Mô hình cải tiến **DuCRG-YOLOv11n** đạt hiệu suất tổng thể tốt nhất với tốc độ khung hình **68,25 FPS** và độ chính xác (**Precision**) đạt **91,4%**.
*   **Theo dõi ổn định:** Khi kết hợp cùng ByteTrack, hệ thống có thể theo dõi hơn 90% phương tiện trong kịch bản giao thông mật độ thấp đến trung bình, đạt mức **MOTA 0,7195**, **MOTP 0,08735** và **IDF1 0,851**, đồng thời giảm hiệu quả các lỗi chuyển đổi ID (ID switches).
*   **Phân tích sâu sắc nhờ LLM:** Đánh giá cho thấy **Claude Sonnet 4** là mô hình LLM mang lại góc nhìn toàn diện nhất, diễn giải chính xác nguyên nhân ùn tắc giao thông, và bù đắp hiệu quả các thiếu sót của dữ liệu bằng cách phân tích bối cảnh.

**Limitations**
**Hạn chế của bài báo là gì?**
*   **Thiếu hụt dữ liệu đầu vào:** Tập dữ liệu quan trắc chưa bao phủ liên tục cả ngày/nhiều ngày và hệ thống thiếu các thông tin nền quan trọng như chu kỳ đèn tín hiệu giao thông, tốc độ xe, hay cấu trúc hình học của nút giao, làm hạn chế độ chính xác trong phân tích.
*   **Ảnh hưởng của phần cứng và môi trường:** Độ phân giải thấp hoặc nhiễu từ camera ảnh hưởng đến độ ổn định khi nhận diện. Bên cạnh đó, điều kiện ánh sáng yếu (ban đêm, chói sáng), góc khuất, hoặc mật độ giao thông quá cao vẫn gây ra lỗi nhận diện sai, bỏ sót và lỗi thay đổi ID đối tượng.

**Relevance to our topic**
**Bài báo liên quan gì đến đề tài của nhóm?**
*(Ghi chú: Vì truy vấn không nêu rõ chủ đề hiện tại của nhóm bạn, dưới đây là mức độ liên quan dựa trên các keyword của bài)*
Bài báo này có tính liên quan trực tiếp và chặt chẽ nếu đề tài của nhóm tập trung vào: **Giao thông thông minh (ITS)**, **Thị giác máy tính (Computer Vision/YOLO)**, **Nhận diện và phân tích luồng phương tiện qua camera giám sát**, hoặc việc tích hợp các **Mô hình ngôn ngữ lớn (LLMs) và RAG** để tự động hóa việc đưa ra các quyết định, cảnh báo tình hình thực tế thông qua phân tích dữ liệu đa phương thức.

**Possible improvement**
**Nhóm có thể cải tiến hoặc mở rộng điểm nào?**
Dựa trên những hạn chế và gợi ý hướng phát triển tương lai từ chính bài báo, nhóm có thể mở rộng nghiên cứu ở các điểm sau:
*   **Mở rộng bộ dữ liệu (Dataset Expansion):** Thu thập dữ liệu video camera xuyên suốt 24/7 trong nhiều ngày để có góc nhìn toàn diện, và bổ sung thêm các vector dữ liệu về cấu trúc hình học nút giao và các tiện ích xung quanh.
*   **Cải tiến phần cứng & Tăng cường hình ảnh:** Áp dụng hệ thống camera đa góc độ (multi-angle cameras) kết hợp với thuật toán tăng cường hình ảnh trong điều kiện ánh sáng yếu để khắc phục điểm yếu nhận diện vào ban đêm và chống che khuất.
*   **Tối ưu hóa kiến trúc AI:** Nâng cấp lên các phiên bản YOLO cao hơn trong tương lai (ví dụ YOLOv13 nếu ra mắt) qua tinh chỉnh trọng số nhẹ hơn, đồng thời kết hợp thiết bị biên (edge devices) với điện toán đám mây để phân tích và phản hồi tức thời tình trạng bất thường trong giao thông.