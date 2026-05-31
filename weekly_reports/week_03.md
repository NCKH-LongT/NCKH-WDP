# Weekly Report - Week 03

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

| Member              | Task                                                                                                                                                   | Result     |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- |
| [Phan Võ Đức Huy]   | Xây dựng hướng collector agent, chốt danh sách telemetry metrics tối thiểu, cập nhật overview architecture và rà soát research gap, research questions | Hoàn thành |
| [Lê Trần Anh Duy]   | Cập nhật use case diagram, vẽ activity diagram và phác thảo mock UI cho dashboard                                                                      | Hoàn thành |
| [Nguyễn Khánh Ngân] | Tổng hợp và viết lại problem statement, research gap, research questions; đồng thời hỗ trợ cập nhật system architecture, phác thảo mock UI             | Hoàn thành |

## Git Commits

| Commit ID | Message                                                          | Author            |
| --------- | ---------------------------------------------------------------- | ----------------- |
| dae88aa   | fix: removed unnecessary file                                    | [Phan Võ Đức Huy] |
| ad28d52   | docs: add problem statement, research gap and research questions | [Phan Võ Đức Huy] |

## Current Problems

- **Nhóm hiện chỉ có môi trường Windows và một thiết bị Android không hỗ trợ ARCore ổn định**, nên hướng native AR ban đầu không phù hợp với điều kiện triển khai thực tế.
- **Cách tiếp cận ArUco + OpenCV trên mobile chưa khả thi để kiểm thử ổn định** vì số lượng thiết bị test quá hạn chế, khó đánh giá chính xác chất lượng marker detection và overlay AR.
- **Hướng chuyển sang iOS native cũng không khả thi trong ngắn hạn** do nhóm không có máy Mac hoặc Xcode để build, debug và kiểm thử ứng dụng.
- **Vì vậy, rủi ro lớn nhất hiện tại không còn là chọn framework native nào**, mà là cần chốt một hướng AR ít phụ thuộc thiết bị và toolchain hơn để đảm bảo tiến độ PoC.
- **Nhóm đã xác định lại hướng phù hợp hơn là WebAR-first**: AR sẽ chạy trên mobile browser để giảm phụ thuộc vào ARCore/ARKit, còn mobile app nếu mở rộng chỉ đóng vai trò companion app cho workflow vận hành thay vì render AR native.

## Plan for Next Week

### 1) Chốt baseline technical design để bắt đầu coding

- Chuyển các tài liệu hiện có thành bộ module rõ ràng cho Phase 1: dashboard, control plane backend, telemetry ingestion, AR diagnostics và simulation.
- Chốt telemetry contract tối thiểu gồm node metrics, container metadata, service status và simulation events.
- Xác định rõ các entity và quan hệ chính để chuẩn bị cho schema/API implementation.

### 2) Bắt đầu dựng backend và luồng dữ liệu

- Tạo skeleton cho backend service và telemetry ingestion flow.
- Mô tả hoặc dựng thử các API chính cho auth, topology, alert, incident/ticket và AR diagnostics.
- Chuẩn bị luồng ingest telemetry từ collector/simulation vào hệ thống để phục vụ dashboard và alerting.

### 3) Dựng frontend và AR workflow

- Chuyển mock UI thành layout cụ thể cho dashboard monitoring.
- Xác định màn hình chính cho alert queue, asset health detail, ticket workflow và AR inspection result.
- Chốt luồng người dùng tối thiểu để demo end-to-end: telemetry -> alert -> incident/ticket -> AR inspection.

### Solution direction

- Giữ `web dashboard` là frontend chính cho admin/operator, sử dụng `React/Next.js` để xử lý monitoring, alert, incident và ticket workflow.
- Chuyển phần AR sang một `WebAR frontend` riêng chạy trên mobile browser, ưu tiên marker-based flow để thực hiện `scan marker -> resolve asset -> hiển thị diagnostics`.
- Nếu cần mở rộng mobile app ở giai đoạn sau, app sẽ chỉ đóng vai trò companion app cho technician như login, ticket list, notification và mở `WebAR` qua link hoặc WebView, thay vì dùng native AR framework.

### Prototype và chuẩn bị demo

- Ưu tiên làm prototype cho luồng monitoring cơ bản trước: simulation/collector -> backend -> dashboard realtime.
- Nếu kịp, bắt đầu prototype AR marker lookup để trả về thông tin node và trạng thái sức khỏe tương ứng.

### 4) Proposal system

- Rà soát và cập nhật lại proposal system theo hướng triển khai thực tế hiện tại của nhóm, đặc biệt là phần AR stack và giới hạn thiết bị test.
- Làm rõ các thay đổi khi nhóm chuyển từ hướng native AR sang `WebAR-first`, bao gồm tác động đến kiến trúc frontend, mobile workflow và tính khả thi của demo.
- Đồng bộ proposal với các tài liệu requirements, architecture và kế hoạch implement để tránh lệch giữa tài liệu và hướng làm thực tế.

## Questions for Instructor

- Với điều kiện thiết bị hiện tại của nhóm chỉ có `Windows` và Android không hỗ trợ `ARCore` ổn định, instructor có đồng ý để nhóm chuyển hướng triển khai phần AR sang `WebAR-first` thay vì native AR không?
- Nếu nhóm chọn `WebAR-first` cho bản PoC, mức độ hiện thực hóa AR như `scan marker -> resolve asset -> hiển thị telemetry/diagnostics` có đủ phù hợp với mục tiêu học thuật của đề tài không?
- Trong proposal và các tài liệu tiếp theo, instructor có muốn nhóm giữ `mobile app` như một phần mở rộng companion workflow cho technician, hay nên tập trung mô tả `web dashboard + WebAR frontend` là hai client chính?
- Với ràng buộc thiết bị và môi trường build hiện tại, instructor có ưu tiên nhóm hoàn thành end-to-end flow khả thi trước, thay vì tiếp tục đầu tư vào native AR stack có rủi ro triển khai cao hơn không?
