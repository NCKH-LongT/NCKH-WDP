# System Overview

## 1. System Name

**AI Study Hub** — Hệ thống Quản lý Tài liệu Học tập Tích hợp Trí tuệ Nhân tạo  
_(AI-Powered Study Document Management System)_

## 2. Purpose

Xây dựng một nền tảng web tập trung giúp sinh viên và giảng viên **lưu trữ, phân loại, chia sẻ** tài liệu học tập trên cloud, đồng thời tích hợp **trợ lý AI thông minh (RAG)** cho phép người dùng tương tác trực tiếp với nội dung tài liệu thông qua hỏi đáp ngữ cảnh, tóm tắt tự động và tìm kiếm ngữ nghĩa — thay thế việc lưu trữ phân tán trên các nền tảng chat và giảm thiểu tình trạng quá tải thông tin cho sinh viên.

## 3. Target Users

| User Role                         | Description                                                                                                         |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Guest**                         | Người dùng chưa đăng nhập, có thể tìm kiếm và xem tài liệu được chia sẻ công khai (Public).                         |
| **User (Sinh viên / Giảng viên)** | Đối tượng chính. Đăng nhập để upload, tổ chức tài liệu cá nhân, chia sẻ nội bộ và sử dụng trợ lý AI hỗ trợ học tập. |
| **Admin (Quản trị viên)**         | Quản lý tài khoản, kiểm duyệt nội dung vi phạm bản quyền/quy chế, giám sát hiệu năng hệ thống.                      |
| **ChatbotService (AI Agent)**     | Hệ thống AI chạy ngầm, xử lý ngôn ngữ tự nhiên, truy xuất vector và phản hồi người dùng qua kiến trúc RAG.          |

## 4. Main Features

1. **Document Management**: Upload đa định dạng (PDF, PPTX, DOCX, TXT), tổ chức theo cây thư mục (Học kỳ → Môn học → Chủ đề), gắn tag và phân loại tài liệu.
2. **Cloud Storage & Sharing**: Lưu trữ file trên cloud (AWS S3 / Cloudinary), xem preview tài liệu trực tiếp trên trình duyệt, phân quyền chia sẻ (Private / View-only link / Public).
3. **AI Chatbot (RAG Q&A)**: Hỏi đáp theo ngữ cảnh trực tiếp trên nội dung tài liệu được chọn, kèm trích dẫn nguồn (trang, đoạn văn) để đối chiếu.
4. **Auto-Summarization**: Tóm tắt toàn bộ tài liệu bằng một click, trích xuất key takeaways từ file PDF/PPTX dài.
5. **Semantic Search**: Tìm kiếm tài liệu theo ngữ nghĩa (vector similarity) thay vì chỉ khớp từ khóa chính xác.
6. **Admin Dashboard**: Thống kê số lượng user, dung lượng lưu trữ, tài liệu phổ biến; kiểm duyệt nội dung vi phạm.

## 5. AI Capabilities

Mô tả khả năng AI trong hệ thống:

- **RAG Pipeline**: Xử lý tài liệu qua chunking → embedding → lưu vào vector database (Pinecone / Supabase pgvector) → truy xuất đoạn liên quan → sinh câu trả lời bằng LLM (Google Gemini 1.5 Flash / GPT-4o mini).
- **Semantic Embedding**: Sử dụng `text-embedding-3-small` (OpenAI) hoặc `text-embedding-004` (Gemini) để chuyển nội dung tài liệu thành vector tọa độ phục vụ tìm kiếm ngữ nghĩa.
- **Contextual Q&A với Citations**: AI chỉ trả lời dựa trên phạm vi tài liệu được chọn (giảm hallucination), đồng thời trả về thông tin trích dẫn nguồn chính xác (trang, đoạn).
- **Auto-Summarization**: Áp dụng kỹ thuật map-reduce summarization để tóm tắt tài liệu dài mà không mất ý chính.
- **Chat History Management**: Lưu trữ lịch sử hội thoại theo từng phiên học tập, gắn với tài liệu tương ứng.

## 6. Expected Output

**Về sản phẩm (System Deliverable):**

- Nền tảng web AI Study Hub hoạt động đầy đủ với giao diện trực quan, hỗ trợ upload tài liệu, quản lý thư mục, chia sẻ và chatbot RAG tích hợp.
- Chatbot AI phản hồi trong **dưới 3 giây** với câu trả lời có trích dẫn nguồn chính xác.

**Về nghiên cứu (Research Artifact):**

- Báo cáo đánh giá hiệu năng RAG vs. LLM baseline theo bộ metrics RAGAS (Faithfulness, Answer Relevancy, Citation Precision).
- Báo cáo so sánh các chiến lược chunking (fixed-size / sentence-based / semantic-based) đo bằng MRR và Recall@k trên tập tài liệu học thuật.
- Kết quả user study với sinh viên đại học (Task Completion Time, NASA-TLX cognitive load score, SUS usability score).

**Về giá trị người dùng (User Impact):**

- Sinh viên tiết kiệm ≥ **50% thời gian** tìm kiếm và tổng hợp tài liệu so với phương pháp lưu trữ thủ công hiện tại.
- SUS score ≥ **70/100** (ngưỡng "Good" theo chuẩn đánh giá quốc tế).
