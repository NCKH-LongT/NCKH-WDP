# Topic Proposal

## 1. Group Information

- Class: SE1823
- Group: 02
- Leader: Cao Trần Hoàng Minh
- Members: Nguyễn Gia Hữu Phước, Lâm Thị Ngọc Hân, Hoàng Ngọc Minh Châu

## 2. Proposed Title

English title: Smart Vehicle Care CRM Platform with Loyalty & Appointment Management

Vietnamese title: Nền tảng CRM chăm sóc xe thông minh tích hợp quản lý lịch hẹn và khách hàng thân thiết

## 3. Application Domain

Lĩnh vực ứng dụng của đề tài là quản lý dịch vụ chăm sóc xe, CRM, loyalty system và appointment management cho các cửa hàng chăm sóc xe máy, ô tô hoặc gara quy mô vừa và nhỏ. Hệ thống hướng đến việc số hóa quy trình đặt lịch, quản lý thông tin khách hàng, theo dõi lịch sử bảo dưỡng, triển khai chương trình khách hàng thân thiết và hỗ trợ chăm sóc khách hàng bằng các tính năng AI đơn giản.

## 4. Problem Statement

Ngành chăm sóc xe tại Việt Nam đang phát triển nhanh do số lượng xe máy và ô tô ngày càng tăng. Tuy nhiên, nhiều cửa hàng chăm sóc xe vừa và nhỏ vẫn quản lý lịch hẹn, thông tin khách hàng, lịch sử dịch vụ và chương trình khách hàng thân thiết bằng sổ ghi chép, file rời hoặc các công cụ không chuyên biệt. Cách quản lý này dễ dẫn đến trùng lịch, bỏ sót lịch hẹn, khó tra cứu lịch sử bảo dưỡng và thiếu dữ liệu để đánh giá hành vi khách hàng.

Bên cạnh đó, các chương trình loyalty truyền thống như thẻ giấy hoặc hình thức "rửa 5 lần tặng 1 lần" thường thiếu khả năng theo dõi tự động, không phản ánh đầy đủ giá trị khách hàng và khó tạo động lực tương tác lâu dài. Khách hàng cũng thường quên lịch bảo dưỡng định kỳ, không nắm rõ điểm thưởng hoặc không nhận được ưu đãi phù hợp với loại xe và lịch sử sử dụng dịch vụ. Vì vậy, cần có một nền tảng số tích hợp appointment management, CRM và loyalty system nhằm hỗ trợ cửa hàng tối ưu vận hành, cải thiện trải nghiệm khách hàng và tăng customer retention.

## 5. Motivation

Vấn đề này quan trọng vì hiệu quả vận hành và khả năng giữ chân khách hàng ảnh hưởng trực tiếp đến doanh thu của các cửa hàng chăm sóc xe. Khi dữ liệu khách hàng và lịch sử dịch vụ được quản lý tập trung, nhân viên có thể phục vụ nhanh hơn, admin có thể theo dõi hiệu quả kinh doanh rõ hơn và khách hàng có trải nghiệm đặt lịch thuận tiện hơn.

Ngoài ra, việc tích hợp các tính năng AI ở mức phù hợp như gợi ý promotion, phân nhóm khách hàng, phân tích hành vi sử dụng dịch vụ và nhắc lịch bảo dưỡng thông minh có thể giúp hệ thống vượt ra khỏi chức năng quản lý cơ bản. Các tính năng này không cần mô hình quá phức tạp nhưng vẫn có giá trị thực tế, phù hợp với phạm vi một đồ án Software Engineering sử dụng MERN Stack.

## 6. Target Users

Người dùng chính của hệ thống gồm ba nhóm:

1. Customer: đặt lịch dịch vụ chăm sóc xe, quản lý thông tin cá nhân và phương tiện, theo dõi lịch sử bảo dưỡng, kiểm tra loyalty points, membership tier, reward và nhận promotion hoặc maintenance reminder.
2. Staff: quản lý appointment trong ngày, xác nhận hoặc cập nhật trạng thái lịch hẹn, ghi nhận dịch vụ đã thực hiện, hỗ trợ khách hàng tại cửa hàng và cập nhật thông tin dịch vụ.
3. Admin: quản lý user, service, promotion, loyalty program, reward, membership tier, theo dõi dashboard, báo cáo doanh thu, hiệu quả loyalty program và hành vi khách hàng.

## 7. Proposed AI Model / Method

Nhóm dự kiến sử dụng các phương pháp AI và data analysis ở mức vừa phải, có thể triển khai được với dữ liệu phát sinh từ hệ thống:

- Recommendation model: gợi ý dịch vụ, reward hoặc promotion dựa trên lịch sử sử dụng dịch vụ, loại xe, membership tier và hành vi đổi điểm.
- Rule-based recommendation kết hợp scoring: áp dụng cho giai đoạn đầu khi dữ liệu còn ít, ví dụ ưu tiên gợi ý bảo dưỡng định kỳ theo số ngày kể từ lần sử dụng dịch vụ gần nhất.
- Customer segmentation bằng k-Means: phân nhóm khách hàng theo tần suất sử dụng dịch vụ, tổng chi tiêu, điểm tích lũy, số lần đặt lịch và mức độ tương tác.
- Classification model như Random Forest hoặc XGBoost: dự đoán khả năng khách hàng quay lại hoặc nguy cơ không tiếp tục sử dụng dịch vụ khi hệ thống có đủ dữ liệu.
- Intelligent reminder: tính toán thời điểm nhắc lịch bảo dưỡng dựa trên loại xe, lịch sử dịch vụ, chu kỳ dịch vụ và hành vi đặt lịch trước đó.

Trong phạm vi đồ án, nhóm ưu tiên triển khai rule-based recommendation, customer segmentation và một mô hình dự đoán đơn giản. Các mô hình phức tạp hơn có thể được xem là hướng mở rộng nếu dữ liệu thực nghiệm đủ lớn.

## 8. System Features

Các chức năng chính của hệ thống:

1. Authentication và authorization: hỗ trợ đăng ký, đăng nhập, quên mật khẩu và role-based authorization cho Customer, Staff và Admin.
2. Appointment Management: cho phép khách hàng tạo, xem, cập nhật hoặc hủy lịch hẹn; nhân viên xác nhận lịch, cập nhật trạng thái dịch vụ và hạn chế trùng lịch.
3. Vehicle Management: lưu thông tin xe, liên kết xe với customer và theo dõi lịch sử bảo dưỡng, dịch vụ đã sử dụng.
4. Loyalty System: tích điểm sau dịch vụ, quản lý membership tiers gồm Bronze, Silver, Gold, Platinum, hỗ trợ đổi reward, discount và quản lý expiration của points.
5. CRM Features: theo dõi customer history, phân nhóm khách hàng, quản lý promotion targeting và tạo personalized offers dựa trên dữ liệu sử dụng dịch vụ.
6. Notification System: gửi booking reminder, maintenance reminder và promotion notification thông qua kênh thông báo trong hệ thống hoặc email.
7. Dashboard & Reports: hiển thị revenue statistics, customer analytics, appointment statistics và loyalty performance tracking cho admin.
8. AI-assisted Features: gợi ý promotion phù hợp, đề xuất thời điểm nhắc bảo dưỡng và phân tích hành vi khách hàng để hỗ trợ quyết định chăm sóc khách hàng.

## 9. Expected Contribution

Đóng góp dự kiến:

1. Xây dựng một nền tảng web sử dụng MERN Stack giúp số hóa quy trình quản lý lịch hẹn, khách hàng, phương tiện, dịch vụ và chương trình khách hàng thân thiết cho cửa hàng chăm sóc xe.
2. Thiết kế mô hình dữ liệu và RESTful API phù hợp với các thực thể chính như User, Customer, Staff, Vehicle, Service, Appointment, LoyaltyPoint, MembershipTier, Promotion, Reward, Notification, Payment và ServiceHistory.
3. Tích hợp các tính năng AI đơn giản nhưng thực tế như gợi ý promotion, phân nhóm khách hàng, nhắc lịch bảo dưỡng thông minh và phân tích customer behavior nhằm hỗ trợ tăng customer engagement và customer retention.

## 10. Evaluation Plan

Nhóm sẽ đánh giá hệ thống như thế nào?

- Dataset: dữ liệu thử nghiệm được xây dựng từ kịch bản hoạt động của cửa hàng chăm sóc xe, bao gồm customer profiles, vehicle information, appointment records, service history, loyalty points, promotion usage và payment records. Nếu có điều kiện, nhóm sẽ bổ sung dữ liệu khảo sát hoặc dữ liệu mẫu từ một cửa hàng thực tế sau khi ẩn thông tin cá nhân.
- Baseline: so sánh với quy trình quản lý thủ công bằng sổ ghi chép hoặc spreadsheet; đối với AI recommendation, so sánh với phương pháp rule cố định như gửi cùng một promotion cho tất cả khách hàng.
- Metrics: đánh giá chức năng hệ thống bằng test cases, API response time, tỷ lệ lịch hẹn bị trùng, tỷ lệ hoàn thành appointment, precision/recall/F1-score cho mô hình phân loại nếu có nhãn, silhouette score cho customer segmentation và click-through rate hoặc redemption rate giả lập cho promotion recommendation.
- Expert evaluation: nhờ giảng viên hoặc người có kinh nghiệm quản lý cửa hàng dịch vụ đánh giá tính phù hợp của workflow, dashboard, dữ liệu báo cáo và logic loyalty program.
- User survey: khảo sát một nhóm người dùng thử gồm customer, staff và admin dựa trên các tiêu chí dễ sử dụng, tính rõ ràng của giao diện, mức độ hữu ích của reminder, promotion và khả năng hỗ trợ vận hành.

## 11. Related Papers

Liệt kê ít nhất 5 bài báo liên quan.

| No  | Title                                                                                                                         | Year | Source                                                                                          | Link / DOI                                  |
| --- | ----------------------------------------------------------------------------------------------------------------------------- | ---- | ----------------------------------------------------------------------------------------------- | ------------------------------------------- |
| 1   | Modeling Customers' Loyalty Using Ten Years' Automobile Repair and Maintenance Data: Machine Learning Approaches              | 2019 | Proceedings of the 2019 2nd International Conference on Data Science and Information Technology | https://doi.org/10.1145/3352411.3352449     |
| 2   | The Application of Data Mining Techniques in Customer Relationship Management: A Literature Review and Classification         | 2009 | Expert Systems with Applications                                                                | https://doi.org/10.1016/j.eswa.2008.02.021  |
| 3   | The Influence of Loyalty Programs and Short-Term Promotions on Customer Retention                                             | 2004 | Journal of Marketing Research                                                                   | https://doi.org/10.1509/jmkr.41.3.281.35986 |
| 4   | Customer Engagement, Buyer-Seller Relationships, and Social Media                                                             | 2016 | Management Science                                                                              | https://doi.org/10.1287/mnsc.2014.2141      |
| 5   | Optimising an Appointment System Using Machine Learning Algorithms and Scheduling Rules: A Case Study in an Outpatient Clinic | 2018 | Expert Systems with Applications                                                                | https://doi.org/10.1016/j.eswa.2018.02.022  |
