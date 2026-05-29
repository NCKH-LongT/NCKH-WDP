# Khoảng trống nghiên cứu

## Các hướng tiếp cận hiện có

Các nghiên cứu hiện có cung cấp nền tảng hữu ích từ hai hướng chính. Hướng thứ nhất là `AR-assisted maintenance`, trong đó các công trình trước đây cho thấy Augmented Reality có thể cải thiện hướng dẫn thao tác, trực quan hóa theo ngữ cảnh, khả năng sử dụng và hỗ trợ bảo trì trong môi trường kỹ thuật hoặc công nghiệp. Tuy nhiên, phần lớn các nghiên cứu này tập trung vào manufacturing, servicing thiết bị hoặc procedural guidance, thay vì giám sát và bảo trì hạ tầng theo bối cảnh data center.

Hướng thứ hai là `AI-based anomaly detection for infrastructure operations`, trong đó các công trình trước đây chứng minh rằng log, telemetry và monitoring data có thể được phân tích để phát hiện các trạng thái bất thường trong server farm hoặc data center. Nhóm nghiên cứu này rất liên quan đến lớp phân tích backend của đề tài, nhưng thường tập trung vào hiệu năng phát hiện, xử lý luồng dữ liệu hoặc kết hợp nhiều nguồn monitoring hơn là tương tác bảo trì hoặc kiểm tra có hỗ trợ AR.

## Các hạn chế quan sát được

Mặc dù cả hai hướng trên đều liên quan, literature hiện tại vẫn cho thấy một số hạn chế.

Thứ nhất, nhiều nghiên cứu về AR maintenance nhấn mạnh chất lượng hướng dẫn, trải nghiệm người dùng hoặc hỗ trợ thực hiện tác vụ, nhưng không tích hợp một pipeline phân tích bất thường dựa mạnh trên telemetry. Thứ hai, nhiều nghiên cứu về anomaly detection cho hệ thống hạ tầng chỉ tập trung vào dữ liệu backend mà chưa xem xét việc truyền đạt insight phát hiện được cho người dùng trong quá trình bảo trì. Thứ ba, hai nhánh nghiên cứu này thường được đánh giá tách biệt: nghiên cứu AR thường đo usability và cognitive load, trong khi nghiên cứu anomaly detection thường đo precision, recall, F1-score hoặc detection delay.

Vì vậy, hiện vẫn còn ít bằng chứng cho thấy các insight bất thường do AI sinh ra có thực sự cải thiện việc diễn giải sự cố và ưu tiên bảo trì khi chúng được nhúng vào một quy trình dashboard kết hợp AR hay không.

## Những nhu cầu chưa được giải quyết

Từ literature đã rà soát và phạm vi của đề tài, có thể thấy một số nhu cầu nghiên cứu vẫn chưa được giải quyết đầy đủ.

Cần có một nghiên cứu ở mức hệ thống kết nối `telemetry thời gian thực`, `phát hiện bất thường có hỗ trợ AI`, `dashboard giám sát`, và `kiểm tra theo ngữ cảnh bằng AR` trong cùng một pipeline vận hành. Cũng cần có thêm nghiên cứu bám đúng `môi trường data center mô phỏng`, vì nhiều nghiên cứu AR maintenance hiện nay xuất phát từ manufacturing hoặc field support tổng quát hơn là data center operations.

Bên cạnh đó, literature hiện tại vẫn bàn chưa nhiều về việc các mô hình AI gọn nhẹ như `Isolation Forest` và `LSTM Autoencoder` có thể được dùng không chỉ để phát hiện bất thường, mà còn để hỗ trợ diễn giải bất thường và ưu tiên bảo trì trong một workflow proof-of-concept thực tế. Một nhu cầu khác chưa được giải quyết rõ là một cách đánh giá kết hợp giữa `hiệu năng kỹ thuật của AI` và `giá trị ở mức người dùng/quy trình`.

## Điểm khác biệt mà đề tài hướng tới

Nghiên cứu này khác biệt ở chỗ định vị `AR` là lớp tương tác chính và `AI` là lớp phân tích bổ sung trong một workflow bảo trì cho data center mô phỏng. Thay vì đề xuất một thuật toán phát hiện bất thường hoàn toàn mới, nghiên cứu tập trung khảo sát cách các mô hình AI hiện có có thể được tích hợp với thu thập telemetry, xử lý cảnh báo và trực quan hóa theo ngữ cảnh bằng AR để hỗ trợ quyết định giám sát và bảo trì hiệu quả hơn.

Cụ thể hơn, hệ thống đề xuất kết hợp:

- telemetry và operational context từ các thực thể hạ tầng mô phỏng,
- phát hiện bất thường và cảnh báo sớm bằng AI gọn nhẹ,
- dashboard giám sát và xử lý cảnh báo,
- kiểm tra bằng AR dựa trên marker để hỗ trợ bảo trì theo ngữ cảnh.

Sự kết hợp này cho phép đề tài giải quyết một khoảng trống mà các công trình trước đây từ riêng nhánh AR maintenance hoặc riêng nhánh data-center anomaly detection vẫn chưa bao phủ đầy đủ.

## Đóng góp nghiên cứu kỳ vọng

Các đóng góp kỳ vọng của nghiên cứu này gồm:

1. Một kiến trúc proof-of-concept tích hợp giám sát telemetry, phát hiện bất thường có hỗ trợ AI, tương tác qua dashboard và kiểm tra bằng AR dựa trên marker cho bài toán bảo trì data center mô phỏng.
2. Một đánh giá thực nghiệm về việc trực quan hóa theo ngữ cảnh bằng AR có cải thiện hiệu quả bảo trì, tải nhận thức và situational awareness so với dashboard-only monitoring hay không.
3. Một đánh giá so sánh các mô hình phát hiện bất thường gọn nhẹ, tập trung không chỉ vào chất lượng phát hiện mà còn vào tính kịp thời trong môi trường hạ tầng mô phỏng.
4. Bằng chứng ở mức workflow về việc các insight bất thường do AI sinh ra có giúp người dùng diễn giải trạng thái bất thường và ưu tiên hành động bảo trì hiệu quả hơn hay không.

Tổng hợp lại, các đóng góp này định vị đề tài như một nghiên cứu về tính khả thi và tích hợp hệ thống, thay vì một bài báo AI thuần thuật toán.
