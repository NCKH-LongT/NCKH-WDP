1. Group Information

Class: SE1823
Group: 08
Leader: Trần Phan Thanh Phúc
Members: Quản Minh Luân, Đào Huy Hoàng

2. Proposed Title
   English title:

Smart Parking Building Management System with Intelligent Slot Allocation

Vietnamese title:

Hệ thống quản lý tòa nhà gửi xe thông minh tích hợp phân bổ chỗ đỗ bằng AI

3. Application Domain

Lĩnh vực ứng dụng của đề tài là quản lý bãi giữ xe thông minh (Smart Parking Management), hỗ trợ vận hành các tòa nhà gửi xe nhiều tầng tại đô thị lớn. Hệ thống tập trung vào quản lý phương tiện ra/vào, phân bổ slot đỗ xe, theo dõi trạng thái chỗ đỗ, xử lý vé xe, thanh toán và tối ưu sử dụng bãi xe bằng các kỹ thuật AI và data analysis.

Hệ thống hướng đến việc số hóa quy trình quản lý parking lot cho các trung tâm thương mại, chung cư, bệnh viện hoặc tòa nhà văn phòng có lưu lượng phương tiện lớn.

4. Problem Statement

Tại các đô thị lớn, nhu cầu gửi xe ngày càng tăng trong khi diện tích đỗ xe bị hạn chế. Các tòa nhà gửi xe nhiều tầng được xây dựng nhằm tiếp nhận, lưu trữ và tổ chức phương tiện theo nhiều tầng hoặc khu vực khác nhau. Tuy nhiên, nhiều bãi xe hiện nay vẫn quản lý thủ công hoặc sử dụng các hệ thống rời rạc, dẫn đến ùn tắc tại cổng vào/ra, khó kiểm soát số lượng slot còn trống và khó đối soát doanh thu.

Ngoài ra, việc tài xế tự tìm chỗ đỗ thường gây mất thời gian, tăng lưu lượng di chuyển trong bãi và làm giảm hiệu quả sử dụng không gian đỗ xe. Các tình huống như mất vé, sai biển số, gửi sai khu vực hoặc xe quá thời gian gửi cũng gây khó khăn cho nhân viên quản lý.

Vì vậy, cần có một hệ thống quản lý parking building thông minh có khả năng theo dõi trạng thái slot theo thời gian thực, hỗ trợ phân bổ slot tự động, quản lý lượt gửi xe và cung cấp báo cáo vận hành nhằm tăng hiệu quả sử dụng bãi xe và giảm thời gian tìm chỗ đỗ.

5. Motivation

Đề tài quan trọng vì việc quản lý bãi xe hiệu quả ảnh hưởng trực tiếp đến trải nghiệm người dùng, khả năng vận hành và doanh thu của các tòa nhà gửi xe. Khi dữ liệu phương tiện, slot và lượt gửi xe được quản lý tập trung, nhân viên có thể xử lý xe vào/ra nhanh hơn, quản lý dễ dàng theo dõi tình trạng bãi xe và người dùng có trải nghiệm gửi xe thuận tiện hơn.
Bên cạnh đó, việc tích hợp AI ở mức phù hợp như phân bổ slot thông minh, dự đoán giờ cao điểm hoặc tối ưu tỷ lệ lấp đầy bãi xe có thể giúp hệ thống vượt ra khỏi chức năng quản lý cơ bản. Các tính năng này không yêu cầu mô hình quá phức tạp nhưng vẫn mang giá trị thực tế và phù hợp với phạm vi đồ án Software Engineering sử dụng MERN Stack.

6. Target Users

Người dùng chính của hệ thống gồm bốn nhóm:

Parking User / Driver
Xem thông tin bãi xe, loại xe được hỗ trợ và số slot còn trống
Nhận vé/mã gửi xe khi vào bãi
Theo dõi thông tin lượt gửi xe hiện tại
Thanh toán phí gửi xe
Đặt chỗ trước nếu hệ thống hỗ trợ

Parking Staff
Kiểm tra và xử lý xe vào/ra
Quét hoặc nhập biển số xe
Tạo parking session
Xác nhận thanh toán
Hỗ trợ xử lý các trường hợp ngoại lệ như mất vé hoặc sai thông tin xe

Parking Facility Manager
Quản lý tòa nhà gửi xe
Quản lý loại phương tiện và phân tầng
Quản lý slot và trạng thái slot
Quản lý bảng giá và chính sách tính phí
Theo dõi dashboard, doanh thu và tỷ lệ lấp đầy

System Administrator
Quản lý tài khoản
Phân quyền hệ thống
Quản lý cấu hình hệ thống 7. Proposed AI Model / Method

7. Reasons for integrating AI

Lý do cần tích hợp AI
Hành vi con người mang tính cục bộ: Tài xế có xu hướng đỗ ngay khi thấy chỗ trống ở các tầng thấp, dẫn đến ùn tắc cục bộ tại các lối đi chính.

Bài toán tối ưu hóa đa mục tiêu: Cần cân bằng giữa việc giảm thời gian di chuyển của tài xế, tối ưu năng lượng tiêu thụ của tòa nhà (hệ thống thông gió, đèn chiếu sáng ở các tầng trống), và dành chỗ cho các xe đã đặt trước hoặc xe ưu tiên (xe điện cần sạc). Các thuật toán lập trình thông thường (Rule-based) không thể xử lý linh hoạt trong môi trường thay đổi liên tục.

Nhóm dự kiến sử dụng các phương pháp AI và data analysis ở mức vừa phải, phù hợp với dữ liệu phát sinh từ hệ thống:

Intelligent Slot Allocation

Phân bổ slot tự động dựa trên:

loại phương tiện
tầng/khu vực
khoảng cách đến cổng
tỷ lệ lấp đầy hiện tại
Rule-based Recommendation + Scoring

Áp dụng scoring để:

ưu tiên slot gần nhất
cân bằng số lượng xe giữa các tầng
giảm thời gian tìm chỗ
Occupancy Prediction

Dự đoán:

giờ cao điểm
tỷ lệ lấp đầy
khả năng hết chỗ trong từng khung giờ
Customer/Usage Pattern Analysis

Phân tích:

thời gian gửi xe phổ biến
loại phương tiện thường sử dụng
lưu lượng xe theo ngày/giờ
Optional AI Extensions
OCR biển số xe
phát hiện slot trống bằng camera
anomaly detection cho các trường hợp bất thường

Trong phạm vi đồ án, nhóm ưu tiên triển khai rule-based intelligent allocation và occupancy analysis. Các mô hình AI phức tạp hơn sẽ là hướng mở rộng.

8. System Features
   Authentication & Authorization
   Đăng ký, đăng nhập
   Phân quyền theo role
   Vehicle & Parking Session Management
   Quản lý thông tin phương tiện
   Tạo và theo dõi parking session
   Ghi nhận thời gian vào/ra
   Slot Management
   Theo dõi trạng thái slot:
   Available
   Occupied
   Reserved
   Maintenance
   Locked
   Phân tầng theo loại xe
   Smart Slot Allocation
   Gợi ý slot phù hợp tự động
   Giảm thời gian tìm chỗ
   Tối ưu tỷ lệ sử dụng bãi xe
   Reservation System
   Đặt chỗ trước
Kiểm tra slot khả dụng theo thời gian
   Payment & Pricing
   Tính phí gửi xe
   Quản lý bảng giá
   Hỗ trợ xử lý xe quá hạn
   Dashboard & Reports
   Thống kê lượt xe vào/ra
   Doanh thu
   Tỷ lệ lấp đầy
   Peak hour analysis
   AI-assisted Features
   Dự đoán giờ cao điểm
   Phân tích occupancy
   Đề xuất slot tối ưu

9. Expected Contribution
   Xây dựng hệ thống Smart Parking sử dụng MERN Stack giúp số hóa quy trình quản lý bãi xe nhiều tầng.
   Thiết kế RESTful API và database cho các thực thể như User, Vehicle, ParkingSlot, ParkingFloor, ParkingSession, Reservation, Payment và PricingPolicy.
   Tích hợp các tính năng AI đơn giản nhưng thực tế như intelligent slot allocation, occupancy prediction và parking analytics nhằm cải thiện hiệu quả vận hành bãi xe.
   Đề xuất cơ chế tối ưu phân bổ slot giúp giảm thời gian tìm chỗ và tăng tỷ lệ sử dụng parking lot.

10. Evaluation Plan
    Dataset

Dữ liệu thử nghiệm được xây dựng từ các kịch bản hoạt động của parking building:

vehicle records
parking sessions
slot occupancy
reservation data
payment history
Baseline

So sánh với:

quản lý thủ công
cơ chế tài xế tự chọn chỗ
Metrics
System Metrics
API response time
accuracy của slot status
parking throughput
tỷ lệ lỗi xử lý xe
AI Metrics
average searching time
slot utilization rate
occupancy prediction accuracy
reduction of congestion
Expert Evaluation

Nhờ giảng viên hoặc người có kinh nghiệm quản lý bãi xe đánh giá:

workflow
dashboard
allocation logic
tính thực tế của hệ thống
User Survey

Khảo sát:

mức độ dễ sử dụng
tốc độ xử lý
độ chính xác của slot allocation
trải nghiệm gửi xe 

11. Expected Outcomes
Đối với Khách hàng: Giảm 30% - 50% thời gian tìm chỗ đỗ và di chuyển trong tòa nhà. Trải nghiệm gửi xe mượt mà, không còn áp lực tìm kiếm.

Đối với Chủ đầu tư / Quản lý:

Tăng tỷ lệ lấp đầy (Utilization Rate) của bãi xe lên thêm 15% - 20% nhờ điều phối thông minh.

Giảm thiểu tình trạng ùn ứ tại các nút giao nội khu tòa nhà vào giờ cao điểm.

Tiết kiệm chi phí năng lượng (đèn, quạt thông gió) tại các khu vực ít xe đỗ nhờ dự đoán chính xác nhu cầu.

Về mặt Công nghệ: Hệ thống vận hành tự động hóa cao, giảm tải công việc cho nhân viên trực bãi và hạn chế tối đa sai sót do con người.

12. Related Papers
No Title Year Source Link / DOI
1 MEC-Based Smart Parking System Considering User Satisfaction and Network Overhead 2024 Journal of KICS https://doi.org/10.7840/kics.2024.49.9.1250
2 An Intelligent Parking Allocation Framework for Digital Society 5.0 2024 Integrated Computer-Aided Engineering https://doi.org/10.3233/IDT-230339
3 Parking Slots Allocation for Multiple Autonomous Valet Parking Vehicles 2022 SAE Technical Paper https://doi.org/10.4271/2022-01-0148
4 Data-driven Dynamic Optimization for Real-time Parking Reservation Considering Parking Unpunctuality 2024 IISE Transactions https://doi.org/10.1080/24725854.2023.2286631
5 Dynamic Space Allocation Based on Internal Demand for Optimizing Release of Shared Parking 2022 Sensors https://doi.org/10.3390/s22010235
