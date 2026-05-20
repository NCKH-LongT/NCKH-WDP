# AI Study Hub — Topic Proposal

> **Hệ thống Quản lý Tài liệu Học tập AI**
> Nền tảng Web tập trung hỗ trợ sinh viên lưu trữ, phân loại và chia sẻ tài liệu học tập trên nền tảng Cloud, đồng thời tích hợp trợ lý AI thông minh (RAG) giúp tra cứu, tóm tắt và hỏi đáp trực tiếp trên nội dung tài liệu.

---

## 1. Topic (Tên đề tài dự kiến)

* **Tên tiếng Việt:** Hệ thống Quản lý Tài liệu Học tập Tích hợp Trí tuệ Nhân tạo
* **Tên tiếng Anh:** AI-Powered Study Document Management System
* **Tên viết tắt dự án:** **AI Study Hub**

---

## 2. Application Domain (Lĩnh vực ứng dụng)

* **Lĩnh vực chính:** Công nghệ giáo dục (EdTech - Educational Technology).
* **Phạm vi ứng dụng:** Quản lý tri thức cá nhân/đội nhóm (Knowledge Management System) dành cho sinh viên, giảng viên và các cơ sở giáo dục đại học.

---

## 3. Context & Problems (Bối cảnh và Vấn đề thực tế)

### 3.1 Bối cảnh

Trong môi trường đại học, khối lượng tài liệu học tập (slide bài giảng, giáo trình, tài liệu tham khảo, mã nguồn, đề thi cũ) là cực kỳ lớn. Sinh viên có xu hướng lưu trữ phân tán ở nhiều nơi như Google Drive, Messenger, Facebook Group, Email, hoặc USB cá nhân.

### 3.2 Vấn đề thực tế cần giải quyết

* **Tài liệu bị phân tán và thất lạc:** Sinh viên mất quá nhiều thời gian để tìm lại một tài liệu cũ do không nhớ đã lưu ở nền tảng nào.
* **Thiếu cấu trúc phân loại:** Tài liệu chưa được tổ chức một cách hệ thống theo môn học, học kỳ, hay chủ đề rõ ràng.
* **Chia sẻ thủ công, rời rạc:** Việc gửi file qua các ứng dụng chat (Messenger, Zalo) dễ bị trôi tin nhắn, giới hạn thời gian tải file và khó quản lý phiên bản khi làm việc nhóm.
* **Quá tải thông tin (Information Overload):** Tài liệu chuyên ngành thường dài và phức tạp (file PDF hàng trăm trang). Sinh viên gặp khó khăn trong việc chắt lọc kiến thức cốt lõi hoặc tìm nhanh một định nghĩa, công thức cụ thể trong đống tài liệu đó.

---

## 4. Target Users & Primary Actors (Đối tượng người dùng)

| Actor | Mô tả đối tượng |
| --- | --- |
| **Guest** | Người dùng chưa đăng nhập (học sinh, sinh viên trường khác), có thể tìm kiếm và xem các tài liệu được chia sẻ ở chế độ công khai (Public). |
| **User (Sinh viên/Giảng viên)** | Đối tượng chính. Đăng nhập qua tài khoản trường để upload, tổ chức tài liệu cá nhân, chia sẻ nội bộ và sử dụng trợ lý AI để hỗ trợ học tập. |
| **Admin (Quản trị viên)** | Đội ngũ quản trị hệ thống, chịu trách nhiệm duyệt/xóa tài liệu vi phạm bản quyền hoặc quy chế, quản lý tài khoản và giám sát hiệu năng hệ thống. |
| **ChatbotService** | Hệ thống AI chạy ngầm chịu trách nhiệm xử lý ngôn ngữ tự nhiên, truy xuất dữ liệu từ tài liệu và phản hồi người dùng. |

---

## 5. Why AI? (Lý do cần tích hợp AI)

Việc tích hợp AI (cụ thể là kiến trúc RAG - Retrieval-Augmented Generation) không chỉ dừng lại ở tính năng "chat giải trí", mà là **giải pháp cốt lõi** để giải quyết vấn đề quá tải thông tin:

* **Chuyển hóa tài liệu tĩnh thành động:** Thay vì sinh viên phải đọc tuyến tính hàng trăm trang tài liệu để tìm một câu trả lời, AI cho phép họ "giao tiếp trực tiếp với tài liệu".
* **Hỗ trợ học tập cá nhân hóa 24/7:** AI đóng vai trò như một trợ giảng ảo, có khả năng giải thích các khái niệm khó, tóm tắt các chương dài, hoặc tạo câu hỏi ôn tập (quiz) dựa chính xác trên giáo trình mà sinh viên đăng tải.
* **Tối ưu hóa tìm kiếm ngữ nghĩa (Semantic Search):** AI giúp tìm kiếm tài liệu dựa trên ngữ cảnh và ý nghĩa của từ khóa, thay vì chỉ khớp chính xác từng ký tự như các bộ lọc thông thường.

---

## 6. Proposed AI Models (Model AI dự kiến sử dụng)

Để tối ưu hóa chi phí, tốc độ và độ chính xác, hệ thống dự kiến áp dụng kiến trúc **RAG (Retrieval-Augmented Generation)** với các mô hình sau:

* **Large Language Model (LLM):** - **Google Gemini 1.5 Flash / Pro API:** Lợi thế lớn về Context Window cực rộng (lên đến 1 triệu - 2 triệu tokens), rất phù hợp để xử lý các bộ tài liệu, giáo trình có dung lượng lớn của sinh viên.
* *Dự phòng:* **OpenAI GPT-4o mini** (để tối ưu chi phí và tốc độ phản hồi text).


* **Embedding Model:** **text-embedding-3-small (OpenAI)** hoặc **text-embedding-004 (Gemini)** để chuyển đổi nội dung tài liệu thành các vector tọa độ phục vụ cho việc tìm kiếm ngữ nghĩa.
* **Vector Database:** **Pinecone**, **Milvus** hoặc **Supabase Vector (pgvector)** để lưu trữ và truy xuất các đoạn văn bản có độ tương đồng cao một cách nhanh chóng.

---

## 7. Functional Requirements (Yêu cầu chức năng)

### 7.1 Xác thực & Phân quyền (Authentication & Authorization)

* Đăng ký, đăng nhập, đăng xuất, quên mật khẩu.
* Hỗ trợ đăng nhập nhanh bằng Google/Microsoft Account (Sử dụng Email sinh viên).
* Phân quyền rõ ràng giữa Guest, User, và Admin.

### 7.2 Quản lý tài liệu & Lưu trữ Cloud (Document & Cloud Management)

* Upload đa định dạng file: `.pdf`, `.docx`, `.pptx`, `.txt`.
* Lưu trữ file an toàn trên Cloud (Sử dụng **AWS S3** hoặc **Cloudinary**).
* Hỗ trợ xem trực tiếp (Preview) tài liệu trên trình duyệt mà không cần tải về.
* Quản lý cây thư mục: Tạo thư mục theo Học kỳ -> Môn học -> Chủ đề.
* Gắn thẻ (Tagging) và phân loại tài liệu (Slide, Đề thi, Sách, Note).
* Chia sẻ tài liệu: Cho phép bật/tắt quyền truy cập (Private, View-only với link, Public).

### 7.3 Trợ lý AI Thông minh (AI Chatbot - RAG Space)

* **Hỏi đáp theo ngữ cảnh (Contextual Q&A):** Sinh viên có thể chọn một hoặc nhiều tài liệu cụ thể và đặt câu hỏi, AI sẽ chỉ trả lời dựa trên phạm vi kiến thức của các tài liệu đó (tránh hiện tượng AI "ảo tưởng" - hallucination).
* **Trích dẫn nguồn (Citations):** AI khi trả lời phải chỉ rõ câu trả lời nằm ở trang mấy, đoạn nào của tài liệu gốc để sinh viên đối chiếu.
* **Tóm tắt tự động (Auto-Summarization):** Tính năng một click để AI đưa ra các ý chính (Key takeaways) của toàn bộ file tài liệu vừa upload.
* **Lịch sử trò chuyện (Chat History):** Lưu trữ và quản lý các đoạn chat cũ theo từng phiên học tập.

### 7.4 Quản trị hệ thống (Administration)

* Dashboard thống kê: Tổng số lượng user, dung lượng bộ nhớ đã dùng, các tài liệu được quan tâm nhiều nhất.
* Kiểm duyệt nội dung (Content Moderation): Hệ thống quét từ khóa hoặc Admin duyệt tay để gỡ bỏ tài liệu vi phạm pháp luật, bản quyền hoặc quy chế thi cử.

---

## 8. Expected Outcomes (Kết quả mong muốn)

* **Về mặt sản phẩm:** Xây dựng thành công một nền tảng Web có giao diện trực quan (UI/UX tối ưu cho sinh viên), hệ thống chạy ổn định, tốc độ phản hồi của Chatbot AI dưới 3 giây.
* **Về mặt giá trị cho người dùng:** - Giúp sinh viên tiết kiệm 50% thời gian tìm kiếm và tổng hợp tài liệu.
* Nâng cao hiệu quả tự học thông qua việc tương tác trực tiếp với trợ lý AI.


* **Về mặt công nghệ:** Làm chủ được quy trình xử lý dữ liệu (ETL cho tài liệu), kỹ thuật cắt text (Chunking), nhúng vector (Embedding) và tối ưu hóa câu lệnh prompt (Prompt Engineering) trong kiến trúc RAG.

---

