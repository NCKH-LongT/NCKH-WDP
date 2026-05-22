# Tóm tắt Bài báo 04

## Trích dẫn

Zhao, A. Y., Gunturu, A., Do, E. Y.-L., & Suzuki, R. (2025). *Guided Reality: Generating Visually-Enriched AR Task Guidance with LLMs and Vision Models*. arXiv. https://arxiv.org/abs/2508.03547

## Vấn đề nghiên cứu

Các hệ thống hướng dẫn AR dựa trên LLM gần đây có thể sinh ra chỉ dẫn từng bước, nhưng thường chưa gắn kết phong phú các chỉ dẫn này vào ngữ cảnh không gian. Điều đó khiến hướng dẫn trở nên kém trực quan đối với các tác vụ thực tế, nơi người dùng không chỉ cần biết phải làm gì mà còn cần hiểu phải thao tác ở đâu và theo cách nào.

## Phương pháp

Hệ thống tích hợp `LLMs` và `vision models` để thực hiện bốn tác vụ liên kết: sinh hướng dẫn nhiều bước từ truy vấn của người dùng, phân loại kiểu hướng dẫn trực quan phù hợp, trích xuất thông tin không gian từ môi trường thực và nhúng hướng dẫn trực quan động trực tiếp vào không gian AR. Bài báo cũng xác lập năm nhóm hướng dẫn trực quan được rút ra từ một tập hợp sổ tay hướng dẫn người dùng.

## Dữ liệu

Công trình sử dụng một tập hợp sổ tay hướng dẫn người dùng để phục vụ quá trình thiết kế hướng dẫn. Phần đánh giá thực nghiệm dựa trên nghiên cứu người dùng với `N = 16` người tham gia thực hiện các tác vụ ngoài thực tế, cùng phản hồi từ bốn giảng viên về tiềm năng ứng dụng trong đào tạo.

## Đánh giá

Đánh giá nhấn mạnh việc thực thi tác vụ trong bối cảnh thực địa và quá trình khảo sát hệ thống "in the wild". Thay vì chỉ đo lường chất lượng mô hình ở chế độ ngoại tuyến, bài báo kiểm tra liệu hướng dẫn AR được sinh ra có hữu dụng và có ý nghĩa trong các bối cảnh tác vụ gắn với hành động thân thể hay không.

## Kết quả

Bài báo chứng minh tính khả thi của cơ chế tự động sinh hướng dẫn AR bằng AI với mức độ trực quan cao hơn so với các lớp phủ chỉ có văn bản. Kết quả nghiên cứu người dùng và phản hồi từ giảng viên cho thấy cách tiếp cận này đầy hứa hẹn cho đào tạo và hỗ trợ thao tác theo từng bước, đặc biệt trong các bối cảnh đòi hỏi hướng dẫn được neo bám theo không gian.

## Hạn chế

Bài báo tập trung vào hướng dẫn tác vụ theo quy trình hơn là giám sát hạ tầng hoặc phân tích bất thường. Đây cũng là một công trình mới và mang tính thăm dò, do đó đóng góp mạnh nhất nằm ở thiết kế tương tác và tự động hóa sinh hướng dẫn hơn là triển khai vận hành ở mức trưởng thành.

## Mức độ liên quan tới đề tài của nhóm

Bài báo đặc biệt hữu ích cho lớp "AI suggestion" trong đề xuất của nhóm. Hệ thống mà nhóm hướng tới cũng bao gồm hỗ trợ bảo trì theo ngữ cảnh trong AR, và công trình này cho thấy AI có thể chuyển từ vai trò giải thích thụ động sang vai trò chủ động sinh hướng dẫn vận hành theo từng bước và gắn kết với không gian.

## Hướng cải tiến khả dĩ

Nhóm có thể điều chỉnh ý tưởng này bằng cách sinh hướng dẫn AR từ ngữ cảnh bất thường, log và trạng thái node thay vì từ các truy vấn người dùng mang tính tổng quát. Một mở rộng hữu ích là kết hợp cơ chế sinh hướng dẫn với mức độ tin cậy để kỹ thuật viên biết khi nào gợi ý của AI chỉ mang tính thăm dò và khi nào đạt độ tin cậy cao.
