# Giới thiệu (Bản nháp)

## 1.1 Bối cảnh

Các cuộc thi học thuật — bao gồm hackathon, cuộc thi nghiên cứu và triển lãm dự án — đóng vai trò quan trọng trong giáo dục đại học, khuyến khích tinh thần đổi mới và kỹ năng ứng dụng của sinh viên. Tại Đại học FPT (Việt Nam), các cuộc thi này thường có hàng chục đội thi phân thành nhiều bảng, được điều phối bởi quản trị viên, mentor và giám khảo qua nhiều vòng thi kéo dài vài tuần.

## 1.2 Vấn đề

Mặc dù có giá trị giáo dục, việc quản lý các cuộc thi này vẫn phụ thuộc nặng nề vào quy trình thủ công. Dựa trên quan sát từ các cuộc thi tại Đại học FPT, bốn điểm đau vận hành cụ thể được xác định:

**V1: Thực thi Timeline Không Chính xác.** Các mốc cuộc thi — deadline nộp bài, chuyển vòng thi và cửa sổ thông báo — được quản trị viên giám sát thủ công. Điều này tạo ra sai lệch về thời gian và cơ sở cho tranh cãi về sự công bằng khi deadline không được thực thi đúng giờ.

**V2: Chi phí Truyền thông và Không Nhất quán.** Quản trị viên phải soạn và gửi email thông báo cho từng mốc cuộc thi: thông báo vào chung kết, nhắc deadline, cảnh báo chưa nộp bài và phân công mentor. Với hơn 30 đội thi, quy trình này chiếm nhiều thời gian nhân viên và tạo ra email với chất lượng, giọng điệu và độ đầy đủ thông tin khác nhau.

**V3: Chuẩn bị Giám khảo Tốn thời gian và Không Nhất quán.** Trước mỗi buổi vấn đáp, từng giám khảo phải tự đọc báo cáo dự án và soạn câu hỏi phỏng vấn phù hợp. Quy trình này tốn 30–60 phút mỗi dự án và tạo ra chất lượng câu hỏi rất khác nhau giữa các giám khảo, dẫn đến điều kiện đánh giá không bình đẳng.

**V4: Thiếu Nền tảng Tích hợp.** Dữ liệu cuộc thi được quản lý trên các công cụ rời rạc — bảng tính, email và form nhập điểm riêng lẻ — không có hệ thống thống nhất nào tích hợp đăng ký, chấm điểm, truyền thông và chuẩn bị giám khảo.

## 1.3 Động lực Tích hợp AI

Những tiến bộ gần đây trong các mô hình ngôn ngữ lớn (LLM) như GPT-4 và Gemini đã chứng minh khả năng mạnh mẽ trong sinh văn bản phù hợp ngữ cảnh, chuyên nghiệp cho các bối cảnh tổ chức [TRÍCH DẪN Tư vấn AI], và trong tổng hợp câu hỏi đánh giá từ nội dung giáo dục [TRÍCH DẪN Sinh quiz]. Những khả năng này gợi ý một ứng dụng hấp dẫn: (1) sinh thông báo cuộc thi cá nhân hóa từ ngữ cảnh có cấu trúc, và (2) tổng hợp câu hỏi phỏng vấn có mục tiêu từ bài đánh giá dự án của giám khảo. Đối với thực thi timeline, scheduling tự động là giải pháp tự nhiên — xác định, dựa trên quy tắc và tự động hóa được.

## 1.4 Đóng góp

Bài báo đưa ra các đóng góp cụ thể sau:

1. **ACMS-AI**: Nền tảng web quản lý cuộc thi học thuật đầy đủ bao phủ toàn bộ vòng đời cuộc thi với ba module AI tích hợp.
2. **Bộ sinh Email LLM**: Pipeline tự động sinh bốn loại email thông báo cuộc thi sử dụng prompt LLM phù hợp ngữ cảnh đặc thù theo loại.
3. **Bộ sinh Câu hỏi từ Bài đánh giá**: Module AI mới đọc bài đánh giá dự án dạng văn bản tự do và tổng hợp 5–7 câu hỏi phỏng vấn bằng LLM — ứng dụng đầu tiên của khái niệm này trong quản lý cuộc thi học thuật.
4. **Timeline AI Agent**: Scheduler tự động thực thi các mốc cuộc thi đúng giờ, loại bỏ lỗi giám sát thủ công.
5. **Đánh giá Thực nghiệm**: Nghiên cứu đánh giá mù chuyên gia so sánh email (80 cặp) và câu hỏi phỏng vấn (30 bộ) do AI tạo với đầu ra viết tay, kết hợp đo hiệu quả thời gian và đánh giá khả năng sử dụng SUS.

## 1.5 Phạm vi

Nghiên cứu này không nhằm đề xuất một mô hình AI hoàn toàn mới. Thay vào đó, nghiên cứu khảo sát cách các LLM hiện có có thể được tích hợp vào một luồng quản lý cuộc thi đặc thù theo lĩnh vực và đánh giá hiệu quả trong việc tự động hóa truyền thông và hỗ trợ chuẩn bị giám khảo.

## 1.6 Cấu trúc Bài báo

Mục 2 tổng quan tài liệu liên quan về hệ thống quản lý tích hợp AI, sinh văn bản bằng LLM và sinh câu hỏi AI. Mục 3 mô tả kiến trúc hệ thống ACMS-AI và ba module AI. Mục 4 trình bày phương pháp đánh giá. Mục 5 mô tả thiết lập thực nghiệm. Mục 6 báo cáo kết quả. Mục 7 thảo luận về phát hiện, hạn chế và hàm ý. Mục 8 kết luận với hướng nghiên cứu tương lai.
