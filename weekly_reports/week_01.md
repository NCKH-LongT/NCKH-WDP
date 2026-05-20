# Weekly Report - Week 01

## Group Information

Class: SE1823
Group: G09
Project: AR-based Infrastructure Monitoring and Maintenance System
Leader: [Phan Võ Đức Huy]
Members:

- [Phan Võ Đức Huy] - [Leader]
- [Nguyễn Khánh Ngân] - [Member]
- [Lê Trần Anh Duy] - [Member]

## Tasks Completed This Week

| Member              | Task                        | Result                                               |
| ------------------- | --------------------------- | ---------------------------------------------------- |
| [Phan Võ Đức Huy]   | Xác định ý tưởng đề tài     | In Brainstorming                                     |
| [Lê Trần Anh Duy]   | Viết topic proposal         | Hoàn thành                                           |
| [Nguyễn Khánh Ngân] | Tìm hiểu sản phẩm liên quan | Tìm hiểu các bài báo về sản phẩm tương tự, liên quan |

## Git Commits

| Commit ID   | Message                  | Author            |
| ----------- | ------------------------ | ----------------- |
| [commit_id] | docs: add topic proposal | [Phan Võ Đức Huy] |

## Current Problems

- Nhóm cần tiếp tục làm rõ phạm vi đề tài để tránh bị hiểu nhầm là xây dựng một hệ thống enterprise-ready cho data center thực tế, trong khi mục tiêu đúng là proof-of-concept để kiểm chứng concept AR + AI.
- Thành phần AR là bắt buộc nên rủi ro kỹ thuật lớn nhất hiện tại nằm ở việc nhận diện marker, độ ổn định overlay, góc nhìn camera và khả năng hiển thị thông tin rõ ràng trên thiết bị di động.
- Phần AI hiện vẫn đang hơi rộng nếu giữ quá nhiều mô hình cùng lúc. Nếu không thu hẹp sớm về một baseline chính và một vài hướng mở rộng, nhóm sẽ bị phân tán công sức.
- Kiến trúc mô phỏng hạ tầng cần được chốt đơn giản theo hướng Docker-only để đảm bảo dễ dựng demo, dễ thu telemetry và dễ kiểm soát lỗi.
- Chưa xác định đầy đủ bộ chỉ số telemetry nào sẽ được thu thập, cách tạo tình huống bất thường trong môi trường mô phỏng và tiêu chí nào sẽ dùng để đánh giá hiệu quả của hệ thống.
- Cần phân biệt rõ đâu là chức năng lõi để chứng minh concept, đâu là chức năng phụ có thể bổ sung sau, tránh làm dàn trải ở các phần như ticket workflow quá chi tiết hoặc dự đoán nâng cao quá sớm.

## Plan for Next Week

### Định hướng đề tài và proposal

- Chốt MVP theo hướng kiểm chứng concept (PoC): một môi trường data center mô phỏng bằng Docker containers, một dashboard web giám sát trạng thái và một luồng AR hiển thị thông tin node qua marker.
- Hoàn thiện lại proposal theo framing học thuật đã thống nhất: AR là thành phần cốt lõi, AI là phần mở rộng nghiên cứu, hệ thống là PoC cho môi trường mô phỏng chứ không nhắm đến triển khai doanh nghiệp.

### Literature review và nghiên cứu liên quan

- Tìm kiếm các bài báo liên quan và bổ sung thêm các keyword phù hợp với dự án.
- Xây dựng danh sách search keywords phục vụ cho việc tìm kiếm bài báo.
- Phân loại các paper theo hướng domain, AR, AI methods và monitoring/maintenance.

### Thiết kế hệ thống

- Phác thảo system architecture tổng thể cho hệ thống, bao gồm dashboard, backend, telemetry flow, AR client và lớp AI mở rộng.
- Thiết kế ERD ở mức ban đầu cho các thực thể chính như node, container/service, telemetry, alert, marker mapping và ticket.
- Chốt bộ telemetry tối thiểu cần thu thập như CPU, memory, network, service status và log sự kiện để phục vụ cả dashboard lẫn AR.

### Prototype và chuẩn bị demo

- Phân tích và lên kế hoạch làm prototype cho hai luồng quan trọng nhất: Docker telemetry -> dashboard và marker recognition -> AR overlay trên node mô phỏng.

## Questions for Instructor

- Instructor có chấp nhận định hướng đề tài như một proof-of-concept để kiểm chứng tính khả thi của concept AR + AI trong monitoring và maintenance cho data center mô phỏng hay không?
- Trong phạm vi môn học, phần AR có thể được xem là thành phần cốt lõi còn AI là phần mở rộng nghiên cứu hay instructor mong muốn AI phải là trọng tâm chính?
- Nhóm có thể sử dụng môi trường mô phỏng bằng Docker containers thay cho hạ tầng thực hoặc cluster phức tạp để phục vụ demo và đánh giá hay không?
- Với phần AI, nhóm có thể chỉ triển khai một mô hình anomaly detection chính để đảm bảo tính khả thi, còn predictive maintenance được trình bày như hướng mở rộng được không?
- Instructor kỳ vọng mức độ đánh giá hệ thống ở mức nào: đánh giá tính khả thi của concept, đánh giá trải nghiệm AR, hay cần benchmark định lượng mạnh cho mô hình AI?
- Các chức năng như ticketing, workflow xử lý sự cố hoặc dự đoán nâng cao có bắt buộc phải hoàn thiện sâu không, hay nhóm có thể giữ ở mức đơn giản để tập trung vào phần core concept?
