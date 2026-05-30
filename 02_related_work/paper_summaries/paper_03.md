# Tóm tắt Bài báo 3

## DiTTO-LLM: Framework for Discovering Topic-based Technology Opportunities via Large Language Model (Khung khám phá cơ hội công nghệ dựa trên chủ đề thông qua LLM)

## Trích dẫn

Kim, W., Seo, S., & Lee, J. (2025). *DiTTO-LLM: Framework for Discovering Topic-based Technology Opportunities via Large Language Model*. arXiv. https://arxiv.org/

## Vấn đề nghiên cứu

Bài báo giải quyết một thách thức quan trọng trong dự báo công nghệ: việc xác định các cơ hội công nghệ mới (bao gồm các khoảng trống chưa được khám phá và các hội tụ giữa các lĩnh vực) gặp khó khăn do sự đa dạng và tiến hóa phức tạp của các lĩnh vực công nghệ. Các phương pháp truyền thống dựa vào chuyên gia hoặc phân tích thủ công, trong khi nhu cầu là các phương pháp tự động hóa có thể xử lý khối lượng lớn dữ liệu công nghệ. Câu hỏi đặt ra là làm thế nào có thể sử dụng các mô hình ngôn ngữ lớn (LLM) hiện đại để tự động phát hiện, phân loại và đặt tên các chủ đề công nghệ, từ đó gợi ý các cơ hội phát triển mới.

## Phương pháp

Tác giả đề xuất khung **DiTTO-LLM** bao gồm ba bước chính:

1. **Trích xuất chủ đề bằng BERTopic**: Sử dụng BERTopic để tự động trích xuất các chủ đề từ bộ dữ liệu bằng sáng chế lớn, xác định các cụm công nghệ liên quan

2. **Tinh chỉnh LLM cho phân loại công nghệ**: Áp dụng các kỹ thuật tinh chỉnh (fine-tuning) để đào tạo LLM nhằm phân loại các công nghệ vào các chủ đề và lĩnh vực phù hợp

3. **Sử dụng Chat-based LLM để gợi ý cơ hội**: Tận dụng các mô hình LLM có khả năng hội thoại (ví dụ: GPT-4) để:
   - Đặt tên các chủ đề một cách có ý nghĩa
   - Gợi ý các cơ hội công nghệ tiềm năng dựa trên các khoảng trống hoặc sự hội tụ

## Dữ liệu

Nghiên cứu sử dụng hai nguồn dữ liệu lớn về bằng sáng chế:
- **Bằng sáng chế AI từ USPTO**: Khoảng thời gian 1976-2020
- **Dữ liệu từ PatentsView**: Khoảng thời gian 2019-2023

Các bộ dữ liệu này cung cấp một tập hợp toàn diện về sự phát triển công nghệ AI qua các thập kỷ, bao gồm mô tả chi tiết, tác giả, thời gian đăng ký và phân loại.

## Đánh giá

Phương pháp được đánh giá thông qua:
- **Kiểm định giả thuyết thống kê**: Xác nhận các giả thuyết về xu hướng tăng trưởng tuyến tính của các cụm công nghệ theo từng chủ đề
- **Phân tích xu hướng thời gian**: Theo dõi sự phát triển của các lĩnh vực công nghệ qua các giai đoạn khác nhau
- **Đánh giá chất lượng chủ đề**: Kiểm tra xem các chủ đề được trích xuất có ý nghĩa và phân biệt được hay không
- **Xác thực cơ hội được gợi ý**: Xem xét xem các cơ hội được gợi ý bởi LLM có hợp lý và có tiềm năng hay không

## Kết quả

Bài báo đạt được các kết quả quan trọng:
- **Phát hiện cơ hội công nghệ chính**: Xác định **Edge AI** (Trí tuệ nhân tạo tại biên) là cơ hội công nghệ tương lai **quan trọng nhất** trong lĩnh vực AI
- **Cấu trúc chủ đề rõ ràng**: Khung được phát triển có khả năng tạo ra các chủ đề có cấu trúc tốt và dễ hiểu
- **Tự động hóa thành công**: Khung DiTTO-LLM cho thấy khả năng tự động hóa quy trình phát hiện cơ hội công nghệ mà không cần can thiệp chuyên gia quá nhiều
- **Sự hội tụ công nghệ**: Xác định các khu vực mà các công nghệ khác nhau (ví dụ: học sâu + cạnh) đang hội tụ để tạo ra các cơ hội mới

## Hạn chế

Bài báo có một số hạn chế cần lưu ý:
- **Giới hạn về nguồn dữ liệu**: Hiện tại chỉ giới hạn ở dữ liệu bằng sáng chế, chưa kết hợp tài liệu học thuật hoặc báo cáo công nghệ từ các nguồn khác
- **Thiếu prompt engineering chuyên sâu**: Kỹ thuật thiết kế gợi ý (prompt engineering) cho GPT-4 chưa được tối ưu hóa hoàn toàn, có thể dẫn đến chất lượng gợi ý không nhất quán
- **Phụ thuộc vào chất lượng BERTopic**: Hiệu quả của chủ đề trích xuất phụ thuộc vào các siêu tham số của BERTopic và có thể cần điều chỉnh cho các lĩnh vực khác nhau
- **Thiếu xác thực chuyên gia**: Chưa có sự xác nhận từ các chuyên gia công nghệ liệu các cơ hội được gợi ý có thực sự khả thi hay không

## Mức độ liên quan tới đề tài của nhóm

Bài báo có **mức độ liên quan cao** tới đề xuất của nhóm vì những lý do sau:

- **Quy trình tự động hóa**: Khung DiTTO-LLM cung cấp một quy trình hoàn chỉnh để tự động hóa việc phát hiện, phân loại và gợi ý các xu hướng hoặc cơ hội dựa trên dữ liệu lớn
- **Ứng dụng của LLM**: Bài báo minh chứng cách sử dụng hiệu quả các mô hình ngôn ngữ lớn (đặc biệt là chat-based LLM) trong việc đặt tên và giải thích các kết quả khai thác dữ liệu
- **Kỹ thuật phân tích chủ đề**: Các kỹ thuật BERTopic có thể được áp dụng cho các miền khác, bao gồm phân tích các xu hướng bảo trì công nghiệp hoặc phát triển công nghệ
- **Phát hiện khoảng trống**: Phương pháp có thể được điều chỉnh để phát hiện các khoảng trống hoặc cơ hội trong các hệ thống bảo trì, giám sát hoặc quản lý AI

## Hướng cải tiến khả dĩ

Để mở rộng và cải thiện khung này cho dự án của nhóm, có thể xem xét:

- **Mở rộng sang dữ liệu bài báo và hội nghị**: Tích hợp dữ liệu từ các bài báo khoa học (ví dụ: từ arXiv, ACM Digital Library, IEEE Xplore) và báo cáo hội nghị để kết hợp hiểu biết từ cả giới hàn lâm và công nghiệp

- **Kết hợp nhiều nguồn dữ liệu**: Sử dụng dữ liệu từ các tài liệu bảo trì, báo cáo kỹ thuật, diễn đàn kỹ sư và cộng đồng trực tuyến để có cái nhìn toàn diện về các xu hướng công nghệ

- **Tối ưu hóa prompt engineering**: Phát triển các chiến lược prompt engineering chuyên sâu cho các lĩnh vực cụ thể để cải thiện chất lượng gợi ý từ LLM

- **Tích hợp với hệ thống giám sát**: Kết nối khung phát hiện cơ hội với các hệ thống giám sát công nghiệp thực tế để cung cấp các gợi ý hành động theo thời gian thực

- **Xác thực chuyên gia**: Thiết lập một quy trình xác thực với các chuyên gia miền để đánh giá và cải thiện chất lượng của các cơ hội và chủ đề được phát hiện
