# Thảo luận (Bản nháp)

## 5.1 Diễn giải Kết quả Chất lượng Email

[Sẽ hoàn thành sau khi có kết quả — dùng cấu trúc này như chỗ trống]

Nếu email AI được đánh giá tương đương email viết tay (trong phạm vi 0,5 điểm trên thang 5 điểm), điều này xác nhận LLM có thể phục vụ như giải pháp thay thế thực tế cho soạn email thủ công trong bối cảnh cuộc thi học thuật. Nghiên cứu trước đây trong lĩnh vực tư vấn (AI-Augmented Advising [TRÍCH DẪN]) phát hiện AI đạt 3,8/5 so với con người 4,2/5 — khoảng cách chủ yếu do độ chính xác thực tế cho nội dung cụ thể quy định. Đối với email cuộc thi, độ chính xác thực tế được quản lý bởi các biến ngữ cảnh có cấu trúc (tên đội, deadline), giảm rủi ro hallucination làm hỏng nội dung email. Điều này gợi ý bộ sinh email của chúng tôi có thể thu hẹp khoảng cách chất lượng hơn so với trường hợp tư vấn.

Một phát hiện dự kiến là email AI có thể đạt điểm cao hơn về tính nhất quán giọng điệu (luôn chuyên nghiệp và khuyến khích), nhất quán với phát hiện của AI-Augmented Advising rằng GPT-4 đạt điểm cao hơn cố vấn con người về giọng điệu (3,8 vs. 3,6). Quản trị viên con người có thể có biến động giọng điệu tùy thuộc vào khối lượng công việc hoặc mệt mỏi.

## 5.2 Diễn giải Kết quả Chất lượng Câu hỏi

Bộ sinh câu hỏi từ bài đánh giá giải quyết tác vụ phức tạp hơn so với công trình sinh quiz trước đây (AI-Powered Quiz Gen [TRÍCH DẪN]), vốn hoạt động trên nội dung khóa học có cấu trúc với câu trả lời thực tế rõ ràng. Bài review dự án là dạng văn bản tự do, đa chiều và đòi hỏi mô hình lý luận về những gì người đánh giá thấy đáng chú ý hoặc có vấn đề. Nếu câu hỏi AI đạt điểm tương đương câu hỏi chuyên gia về bao phủ và liên quan, điều này xác nhận LLM có thể phân tích hiệu quả bài review và xác định chủ đề đáng đánh giá.

Hạn chế có thể xảy ra là chiều sâu: câu hỏi AI có thể bề mặt hơn hoặc hiển nhiên hơn so với câu hỏi do giám khảo có chuyên môn sâu soạn. Điều này phù hợp với hạn chế đã biết của LLM trong sinh câu hỏi tinh tế cho chủ đề nâng cao.

## 5.3 Hiệu quả

Giảm thời gian dự kiến cho tác vụ email admin (~40%) và chuẩn bị câu hỏi giám khảo (~50%+) đại diện cho giá trị thực tiễn cho nhân viên FPT. Với 30 đội trên 3 bảng, giảm thời gian chuẩn bị mỗi đội của giám khảo từ 20 phút xuống gần như tức thì tương đương tiết kiệm hơn 10 giờ thời gian giám khảo mỗi chu kỳ cuộc thi.

## 5.4 Hạn chế

**Rủi ro LLM Hallucination**: Mặc dù có prompt có cấu trúc, LLM đôi khi có thể sinh nội dung không chính xác hoặc không phù hợp. Hệ thống của chúng tôi giảm thiểu điều này qua bước xem xét của admin trước khi gửi email quan trọng (thông báo vào chung kết) và quy tắc kiểm tra đầu ra (độ dài, định dạng, không có placeholder).

**Nhạy cảm Prompt**: Chất lượng đầu ra thay đổi theo cách diễn đạt prompt. Prompt của chúng tôi được tinh chỉnh trên pilot nhỏ; chúng có thể không tổng quát hóa cho cấu trúc cuộc thi hoặc ngôn ngữ khác đáng kể.

**Kích thước Dataset**: 80 cặp email và 30 bộ câu hỏi cung cấp bằng chứng hợp lý nhưng chưa đủ cho xác nhận thống kê quy mô lớn. Khoảng tin cậy sẽ rộng. Công trình tương lai nên đánh giá ở quy mô lớn hơn qua nhiều chu kỳ cuộc thi.

**Đặc thù Domain**: Hệ thống được thiết kế và đánh giá cho định dạng cuộc thi tại Đại học FPT. Thích nghi với các cơ sở giáo dục khác đòi hỏi thay đổi cấu hình và tinh chỉnh lại prompt.

**Thiên kiến Người đánh giá**: Người đánh giá chuyên gia là giảng viên có thể có sở thích ngầm cho nội dung viết theo phong cách con người. Buổi hiệu chỉnh giảm nhưng không loại bỏ hoàn toàn thiên kiến này.

## 5.5 Hàm ý Thực tiễn

ACMS-AI minh chứng hướng tiếp cận thực tế, có thể triển khai cho quản lý cuộc thi tích hợp AI không đòi hỏi huấn luyện model tùy chỉnh. Bằng cách tận dụng LLM thương mại qua API với prompt engineering đặc thù theo lĩnh vực, các cơ sở giáo dục có thể đạt tự động hóa có ý nghĩa với rào cản kỹ thuật thấp. Thiết kế có con người trong vòng lặp (xem xét của admin trước khi gửi thông báo quan trọng) duy trì kiểm soát của tổ chức trong khi vẫn mang lại lợi ích hiệu quả.

## 5.6 Mối đe dọa Tính hợp lệ

| Mối đe dọa | Loại | Biện pháp Giảm thiểu |
|---|---|---|
| Người đánh giá quen với phong cách viết AI | Nội tại | Đánh giá mù; buổi hiệu chỉnh |
| Kích thước mẫu nhỏ | Kết luận | Báo cáo khoảng tin cậy; thừa nhận hạn chế |
| Dữ liệu mô phỏng cho đánh giá câu hỏi | Ngoại tại | Dùng dữ liệu thực nếu có; ghi lại quy trình mô phỏng |
| Bối cảnh một cơ sở | Ngoại tại | Ghi lại cấu trúc cuộc thi FPT; thảo luận khả năng tổng quát hóa |
