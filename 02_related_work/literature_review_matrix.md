# Ma trận Tổng quan Tài liệu (Literature Review Matrix)

| STT | Tên bài báo | Năm | Hội thảo/Tạp chí | Lĩnh vực | Phương pháp AI | Dữ liệu | Chỉ số đánh giá | Đóng góp chính | Hạn chế | Liên quan đến đề tài |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Smart Event Management System Using Machine Learning | 2023 | Intl. Conf. IT Mgmt | Quản lý sự kiện | ML (phân loại, lập lịch, phân tích hành vi) | Log sự kiện, phản hồi người tham gia | Độ chính xác, mức độ hài lòng, thời gian tiết kiệm | Tối ưu hóa lịch sự kiện bằng ML và phân tích hành vi người tham gia | Không có LLM; chỉ tập trung vào lập lịch, không có tự động hóa truyền thông | **Cao** — xác nhận quản lý sự kiện là lĩnh vực ứng dụng AI; cung cấp kiến trúc baseline |
| 2 | Aduvia: A Multi-Purpose AI-Powered Learning Management System | 2025 | NILES 2025 | Giáo dục / LMS | LLM, chatbot AI, hệ thống gợi ý | Dữ liệu LMS, nội dung khóa học | Mức độ hài lòng người dùng, tỷ lệ hoàn thành, thời gian tiết kiệm | Hệ thống quản lý tích hợp nhiều module AI: chatbot, sinh quiz, gợi ý cá nhân hóa | Không phải về cuộc thi; không có luồng thông báo hay chấm điểm | **Cao** — mô hình kiến trúc tương đương trực tiếp; phương pháp đánh giá có thể áp dụng |
| 3 | AI-Powered Quiz Generation for LMS: A Full-Stack Implementation for Canvas LMS | 2025 | CEUR Workshop | Giáo dục / LMS | LLM (GPT/Gemini), RAG | PDF khóa học, đánh giá chuyên gia | Điểm chuyên gia (liên quan, rõ ràng, độ khó), tỷ lệ chấp nhận, thời gian tiết kiệm | Sinh câu hỏi quiz bằng LLM tích hợp vào Canvas LMS | Chỉ sinh câu hỏi trắc nghiệm từ nội dung có cấu trúc; không sinh câu hỏi phỏng vấn mở từ bài đánh giá | **Cao** — phương pháp sinh câu hỏi bằng LLM và khung đánh giá chuyên gia áp dụng trực tiếp cho module sinh câu hỏi phỏng vấn |
| 4 | AI-Powered Academic Advising Using Large Language Models | 2024 | Intl. Conf. AI in Education | Giáo dục đại học | LLM (GPT-4), RAG | Hồ sơ sinh viên, tài liệu quy định | Điểm chuyên gia vs. con người, mức độ hài lòng, độ chính xác | LLM sinh phản hồi tư vấn cá nhân hóa từ ngữ cảnh tổ chức | Rủi ro hallucination; không xử lý được tình huống phức tạp về cảm xúc; lo ngại riêng tư | **Cao** — minh chứng LLM sinh văn bản thể chế; khung đánh giá mù (AI vs. con người) áp dụng trực tiếp để đánh giá email |
| 5 | AI-Augmented Advising | 2025 | J. Learning Analytics | Giáo dục đại học | GPT-4 | Bản ghi buổi tư vấn | So sánh điểm (AI vs. cố vấn con người) | So sánh có hệ thống GPT-4 với cố vấn học thuật con người | Chỉ là nghiên cứu đánh giá, không phải hệ thống hoàn chỉnh | **Trung bình** — cung cấp phương pháp đánh giá mù mạnh mẽ để so sánh AI vs. con người |
| 6 | Research Supervisor Recommendation System Based on Topic Conformity | 2023 | Research Conference | Giáo dục đại học | TF-IDF, cosine similarity | Mô tả đề tài, hồ sơ giảng viên | Precision, Recall, F1 | Ghép đề tài với giảng viên bằng similarity văn bản | TF-IDF hạn chế về ngữ nghĩa; không có LLM; không cân bằng tải | **Trung bình** — khái niệm phân công mentor liên quan đến module phân công mentor-bảng thi |
| 7 | Research Supervisor Recommendation System Using a Hybrid Filtering Approach | 2025 | ICAITech 2025 | Giáo dục đại học | Hybrid filtering (cộng tác + nội dung) | Dữ liệu đề tài và giảng viên | Precision, Recall, mức độ hài lòng | Kết hợp hai phương pháp cải thiện độ chính xác | Vẫn dựa trên đặc trưng có cấu trúc; không có embedding ngữ nghĩa | **Trung bình** — cung cấp baseline cho phân công mentor; cho thấy kết hợp phương pháp hiệu quả hơn |
| 8 | Smart Inventory Management System with Real-Time Package Tracking Using ML | 2026 | IEEE ICoECIT 2026 | Logistics / Supply Chain | ML (phân loại, tracking) | Dữ liệu tồn kho, log tracking | Response time, độ chính xác, throughput | Quản lý tồn kho và tracking thời gian thực bằng ML | Đặc thù lĩnh vực logistics; không có LLM | **Thấp** — tham khảo mô hình kiến trúc hệ thống và phương pháp đánh giá |

## Nhận xét Tổng hợp

### Phương pháp AI trong các bài báo liên quan

| Phương pháp | Bài báo sử dụng | Ghi chú |
|---|---|---|
| LLM (GPT/Gemini) | P02 (Aduvia), P03 (sinh quiz), P04 (tư vấn) | Xu hướng mới nhất; hỗ trợ lựa chọn của chúng tôi |
| RAG | P03 (sinh quiz), P04 (tư vấn) | Hướng mở rộng tiềm năng cho hệ thống |
| TF-IDF + cosine | P06 (supervisor) | Baseline có thể cải tiến bằng embedding |
| ML classifiers | P01 (sự kiện), P08 (kho) | Dùng trong lĩnh vực quản lý; ít liên quan đến các thành phần AI của chúng tôi |

### Phương pháp Đánh giá trong các bài báo liên quan

| Phương pháp | Bài báo sử dụng | Áp dụng cho chúng tôi |
|---|---|---|
| Đánh giá chuyên gia (Likert) | P03, P04, P05 | CÓ — chất lượng email và câu hỏi |
| So sánh mù (AI vs. con người) | P04, P05 | CÓ — thiết kế đánh giá cốt lõi |
| Đo thời gian tiết kiệm | P02, P03 | CÓ — hiệu quả hỗ trợ AI |
| Khảo sát SUS / mức độ hài lòng | P01, P02 | CÓ — khả năng sử dụng tổng thể |
| Precision / Recall / F1 | P06, P07 | Áp dụng cho module phân công mentor |

### Khoảng trống Nghiên cứu Đã xác định

1. Không có bài báo nào sinh email bằng LLM cho 4 loại thông báo đặc thù của cuộc thi học thuật
2. Không có bài báo nào sinh câu hỏi phỏng vấn từ bài đánh giá dự án bằng LLM
3. Không có nền tảng tích hợp nào kết hợp đăng ký, quản lý đa bảng, truyền thông AI và hỗ trợ chuẩn bị giám khảo
4. Không có nghiên cứu thực nghiệm nào so sánh email cuộc thi do LLM tạo với email viết tay
