# Tóm tắt Bài báo 02

## Trích dẫn

Xu, F., Nguyen, T., & Du, J. (2023). *Augmented Reality for Maintenance Tasks with ChatGPT for Automated Text-to-Action*. arXiv. https://arxiv.org/abs/2307.03351

## Vấn đề nghiên cứu

Các tác vụ vận hành và bảo trì thường bao gồm chuỗi bước phức tạp, khó ghi nhớ, đặc biệt đối với người mới hoặc trong điều kiện áp lực. Bài báo khảo sát liệu việc kết hợp AR với mô hình ngôn ngữ lớn có thể làm giảm độ khó khi thực thi công việc, đồng thời cải thiện mức độ tin cậy và hiệu quả trong quá trình bảo trì hay không.

## Phương pháp

Hệ thống đề xuất kết hợp `AR`, `OCR` và mô hình ngôn ngữ `GPT`. OCR được sử dụng để trích xuất văn bản hoặc nhãn liên quan từ bối cảnh vật lý; GPT chuyển đổi phần văn bản đó thành hướng dẫn bảo trì có thể hành động; và giao diện AR trình bày các chỉ dẫn trong một môi trường tương tác xây dựng trên Unity nhằm kết nối giữa ngữ cảnh ảo và ngữ cảnh thực.

## Dữ liệu

Bài báo sử dụng nghiên cứu tình huống thay vì bộ dữ liệu chuẩn công khai. Phần đánh giá thực nghiệm được tiến hành dựa trên một nghiên cứu người dùng với `N = 15` người tham gia thực hiện các tác vụ bảo trì có độ khó tương đương.

## Đánh giá

Việc đánh giá tập trung vào thời gian hoàn thành tác vụ, tải nhận thức và mức độ tin cậy của người dùng. Nghiên cứu so sánh quá trình thực hiện công việc có và không có hỗ trợ AR + AI nhằm xác định liệu giao diện lai này có cải thiện năng lực thực hiện của con người hay không.

## Kết quả

Bài báo cho thấy người dùng hoàn thành các tác vụ có độ khó tương đương trong thời gian ngắn hơn khi sử dụng hệ thống AR + AI. Nghiên cứu cũng ghi nhận sự suy giảm tải nhận thức và gia tăng độ tin cậy so với điều kiện đối chứng, khiến đây trở thành một trong những công trình liên quan trực tiếp nhất tới hướng dẫn bảo trì có hỗ trợ AI.

## Hạn chế

Nghiên cứu dựa trên mẫu nghiên cứu tình huống tương đối nhỏ và không nhắm trực tiếp tới hạ tầng trung tâm dữ liệu. Trọng tâm của bài báo nghiêng về chất lượng hướng dẫn tác vụ và kết quả tương tác nhiều hơn là phân tích telemetry phía backend hoặc cơ chế chấm điểm bất thường.

## Mức độ liên quan tới đề tài của nhóm

Bài báo có mức độ tương đồng rất cao với tính năng hướng dẫn bảo trì theo ngữ cảnh mà nhóm đề xuất. Công trình cung cấp tiền lệ vững chắc cho việc sử dụng AI không chỉ để phát hiện sự cố mà còn để sinh hoặc chuyển hóa tri thức bảo trì thành các chỉ dẫn AR có thể thực thi cho kỹ thuật viên tại hiện trường.

## Hướng cải tiến khả dĩ

Đối với đề tài của nhóm, có thể điều chỉnh cùng ý tưởng tương tác này nhưng để cơ chế hướng dẫn được điều khiển bởi telemetry hạ tầng và điểm bất thường, thay vì chỉ từ văn bản bảo trì tổng quát. Nhóm cũng có thể so sánh hướng dẫn do AI sinh ra với playbook bảo trì dựa trên luật để kiểm chứng liệu lớp AI thực sự tạo thêm giá trị hay không.
