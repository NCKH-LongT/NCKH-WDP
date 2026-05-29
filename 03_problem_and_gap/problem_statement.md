# Phát biểu vấn đề

## Bối cảnh

Giám sát và bảo trì hạ tầng hiện đại đòi hỏi người vận hành phải hiểu đồng thời cả hành vi số của hệ thống lẫn bối cảnh vật lý nơi hoạt động bảo trì diễn ra. Trong thực tế, trạng thái hạ tầng thường được theo dõi thông qua dashboard, log và bảng cảnh báo, trong khi thao tác kiểm tra tại chỗ lại diễn ra ở một ngữ cảnh khác. Sự tách rời này khiến người dùng khó liên kết dữ liệu telemetry thời gian thực với đúng tài sản cần được kiểm tra, đặc biệt khi các sự kiện bất thường cần được diễn giải và xử lý nhanh chóng.

Vấn đề này vẫn có ý nghĩa ngay cả trong môi trường trung tâm dữ liệu mô phỏng. Mặc dù đề tài không hướng tới triển khai ở quy mô doanh nghiệp thực tế, môi trường mô phỏng vẫn bao gồm nhiều thực thể hạ tầng như rack, switch, node, service và container, tất cả đều sinh ra dữ liệu vận hành theo thời gian. Khi số lượng tín hiệu telemetry và sự kiện bất thường tăng lên, người dùng cần một cách tiếp cận trực quan hơn để hiểu trạng thái hệ thống và gắn nó với hành động bảo trì.

## Các vấn đề của quy trình hiện tại

Quy trình giám sát hiện tại tồn tại một số hạn chế thực tế. Thứ nhất, người vận hành phải tự ánh xạ thông tin hạ tầng ở dạng số, chẳng hạn như mức sử dụng CPU, bộ nhớ, trạng thái service hay cảnh báo bất thường, sang đúng tài sản vật lý hoặc tài sản mô phỏng tương ứng. Thứ hai, dashboard tập trung tuy cung cấp cái nhìn tổng quan nhưng lại thiếu ngữ cảnh không gian cho các hoạt động bảo trì tại chỗ. Thứ ba, các cảnh báo dựa trên ngưỡng truyền thống thường khó nắm bắt được những mẫu bất thường phức tạp trong luồng telemetry đa biến. Cuối cùng, quy trình bảo trì thường bị phân mảnh giữa màn hình theo dõi, hàng đợi cảnh báo, hồ sơ incident và thao tác của technician, làm giảm tính liên tục trong vận hành.

Do các hạn chế này, trạng thái bất thường có thể bị phát hiện muộn, bị diễn giải không nhất quán hoặc được truyền đạt kém hiệu quả giữa người giám sát hệ thống và kỹ thuật viên bảo trì. Kết quả là quy trình trở nên kém trực quan hơn và kém hiệu quả hơn trong việc kiểm tra cũng như ưu tiên xử lý sự cố.

## Các bên liên quan

Các bên liên quan chính của bài toán này gồm:

- `IT Administrator`, người giám sát trạng thái tổng thể của hệ thống, quản lý truy cập, topology và cấu hình cảnh báo.
- `System Monitoring Operator`, người theo dõi telemetry thời gian thực, điều tra trạng thái bất thường, xử lý alert và mở incident hoặc ticket bảo trì.
- `Maintenance Technician`, người thực hiện kiểm tra tại chỗ hoặc trong môi trường mô phỏng và cần thông tin có ngữ cảnh trong quá trình bảo trì.

Các nhóm người dùng này cùng tương tác với một tập dữ liệu vận hành nhưng từ những góc nhìn khác nhau. Vì vậy, một hệ thống hữu ích không chỉ cần phát hiện được hành vi bất thường mà còn phải trình bày kết quả theo cách hỗ trợ cả giám sát tập trung lẫn quy trình bảo trì theo ngữ cảnh.

## Tác động thực tiễn

Vấn đề này quan trọng vì giám sát hạ tầng không chỉ là một bài toán diễn giải dữ liệu mà còn là một bài toán điều phối vận hành. Nếu telemetry, cảnh báo và ngữ cảnh bảo trì vẫn bị tách rời, người dùng sẽ tốn thêm thời gian để xác định tài sản bị ảnh hưởng, kiểm tra các trạng thái liên quan và quyết định vấn đề nào cần được xử lý trước. Trong bối cảnh học thuật và proof-of-concept, điều này cũng hạn chế khả năng nghiên cứu việc kết hợp giữa giám sát, phân tích có hỗ trợ AI và tương tác bằng AR thành một quy trình thống nhất.

Về mặt nghiên cứu, vấn đề này có ý nghĩa vì nó nằm ở giao điểm của observability, tương tác người-máy và hỗ trợ ra quyết định bằng AI. Giải quyết vấn đề không nhất thiết đòi hỏi phải sáng tạo ra một mô hình AI hoàn toàn mới, nhưng đòi hỏi phải thiết kế và đánh giá một hệ thống tích hợp được phân tích telemetry với một giao diện bảo trì dễ sử dụng hơn.

## Sự cần thiết của hỗ trợ AI

Hỗ trợ AI là cần thiết vì telemetry hạ tầng thời gian thực chứa các mẫu dữ liệu theo thời gian và dữ liệu đa biến mà các luật ngưỡng đơn giản khó diễn giải đầy đủ. Các mô hình phát hiện bất thường gọn nhẹ có thể giúp nhận diện những trạng thái hạ tầng bất thường, đưa ra tín hiệu cảnh báo sớm và làm giàu góc nhìn vận hành bằng điểm bất thường hoặc insight định hướng rủi ro. Đồng thời, Augmented Reality có thể cung cấp khả năng trực quan hóa theo ngữ cảnh bằng cách gắn những insight đó trực tiếp lên rack, switch hoặc node tương ứng trong quá trình kiểm tra.

Vì vậy, bài toán cốt lõi của nghiên cứu này không chỉ là làm thế nào để trực quan hóa dữ liệu hạ tầng, mà là làm thế nào để tích hợp diễn giải bất thường có hỗ trợ AI và hỗ trợ bảo trì theo ngữ cảnh bằng AR vào một quy trình giám sát thống nhất cho môi trường trung tâm dữ liệu mô phỏng.
