# Paper 09 Summary

## Citation

Tên bài: Dynamic coordinated strategy for parking guidance in a mixed driving parking lot involving human-driven and autonomous vehicles
Tác giả: Wang, Z., Zhang, C., Xue, S., Luo, Y., Chen, J., Wang, W. & Yan, X.
Năm: 2024
Nguồn: Electronic Research Archive, Volume 32, Issue 1, pp. 523–550. AIMS Press (Scopus & SCIE indexed, IF = 1.1, CiteScore = 1.7)
DOI/Link: [10.3934/era.2024026](https://doi.org/10.3934/era.2024026)

## Problem

Bài báo giải quyết thách thức trong việc **hướng dẫn đỗ xe (parking guidance)** tại các bãi đỗ hoạt động trong kịch bản giao thông hỗn hợp (mixed driving), nơi cùng tồn tại cả **xe người lái (Human-driven Vehicles — HVs)** và **xe tự hành (Autonomous Vehicles — AVs)**:

- **Hành vi không tuân thủ (noncompliance):** Xe người lái có thể không tuân theo chỉ dẫn của hệ thống — đi sai đường, chọn chỗ khác, hoặc chiếm chỗ đã phân bổ cho xe khác. Ngược lại, xe tự hành tuân thủ tuyệt đối.
- **Xung đột đan xen (interweaving conflicts):** Xe người lái và xe tự hành di chuyển với tốc độ, quỹ đạo và hành vi khác nhau → dễ gây ra tắc nghẽn làn đường (lane blocking) và xung đột đường đi.
- **Tính động của bãi đỗ:** Trạng thái bãi đỗ thay đổi liên tục (xe vào/ra, slot bị chiếm/giải phóng) → các phương án hướng dẫn tĩnh trở nên lỗi thời ngay sau khi được tạo ra.

## Method

Tác giả đề xuất **Chiến lược Phối hợp Động (Dynamic Coordinated Strategy — DCS)** gồm 4 bước chính:

1. **Triggering Scheme Formulation:** Xác định thời điểm và điều kiện để hệ thống kích hoạt quy trình tối ưu hóa phân bổ lại — ví dụ khi có xe mới vào bãi, xe rời đi, hoặc phát hiện xung đột đường đi.

2. **Identifying Preoccupied Parking Spaces:** Giám sát trạng thái thời gian thực để xác định slot nào đã bị chiếm (bao gồm cả slot đang bị xe noncompliance chiếm sai chỉ dẫn).

3. **Updating the Parking Lot Traffic Network:** Duy trì bản đồ giao thông động — cập nhật trọng số các đoạn đường trong bãi đỗ khi có thay đổi (slot mới trống, làn bị chặn, xe đang di chuyển).

4. **Optimizing Vehicle-Path-Space Matching Scheme:** Thiết lập mô hình quy hoạch toán học để **tối thiểu hóa tổng thời gian cruising còn lại** cho tất cả xe trong bãi.

**Công cụ thuật toán cốt lõi:**

- **Parking-Cruising Path Tree (PCPT):** Cấu trúc dữ liệu dựa trên **thuật toán cây đường đi ngắn nhất động (Dynamic Shortest Path Tree — DSPT)**. PCPT xây dựng cây đường đi từ cổng vào đến từng slot → tính weight cho mỗi nhánh = `cruising_time + blocking_probability` → chọn nhánh tối ưu. Phương pháp cập nhật PCPT cho phép tính toán lại đường đi hiệu quả khi trạng thái thay đổi mà không cần chạy lại toàn bộ Dijkstra.

- **Conflict Resolution:** Khi 2 xe hướng đến cùng slot → ưu tiên xe gần hơn, xe còn lại được chuyển hướng sang slot tối ưu tiếp theo trong PCPT.

## Dataset

Bài báo sử dụng **mô phỏng (simulation-based evaluation):**

- **Mô hình bãi đỗ giả lập:** Thiết kế nhiều cấu hình bãi đỗ (layout) với số lượng slot, cấu trúc làn đường và cổng vào/ra khác nhau.
- **Kịch bản giao thông hỗn hợp:** Thay đổi **tỷ lệ thâm nhập AV (AV penetration rate)** — từ thấp (chủ yếu xe người lái) đến cao (chủ yếu xe tự hành).
- **Mức độ bão hòa (saturation level):** Nhiều mức bão hòa bãi đỗ từ thấp đến cao để kiểm tra tính hiệu quả.
- **Mô hình hành vi tài xế:** Mô phỏng hành vi tuân thủ (compliance) và không tuân thủ (noncompliance) của xe người lái.
- **Tham số kinematic:** Dựa trên dữ liệu thực tế về khả năng cơ động của xe (mô hình Ackermann).

## Evaluation

| Metric | Mô tả |
|---|---|
| Parking-Cruising Duration | Tổng thời gian xe chạy vòng trong bãi để tìm và đến chỗ đỗ — mục tiêu giảm thiểu |
| Forced Delay | Thời gian trễ phát sinh do lane blocking — xe bị chặn bởi xe khác đang đỗ/lùi |
| Optimization Rate | Phần trăm cải thiện cruising duration so với phương pháp không có DCS |
| Total Remaining Cruising Time | Tổng thời gian cruising còn lại của tất cả xe — hàm mục tiêu cần tối thiểu hóa |

So sánh DCS với: hướng dẫn tĩnh (static guidance), FCFS (First-Come-First-Served), và kịch bản không có hướng dẫn.

## Results

- **Tỷ lệ tối ưu lên đến 18%:** DCS đạt tỷ lệ tối ưu parking-cruising duration lên đến **18%** so với các phương pháp truyền thống.
- **Hiệu quả đặc biệt cao trong điều kiện khó:** Kết quả tối ưu nổi bật nhất khi bãi đỗ có **mức bão hòa cao** và **tỷ lệ thâm nhập AV thấp** (nhiều hành vi noncompliance).
- **Giảm đáng kể forced delays:** Thuật toán PCPT giảm thiểu thời gian trễ do lane blocking.
- **Xe có cruising duration dài được hưởng lợi nhiều nhất:** Xe vào bãi khi gần đầy được DCS hướng dẫn hiệu quả hơn.
- **PCPT đảm bảo tính toán thời gian thực:** Cập nhật cây PCPT mà không cần chạy lại toàn bộ shortest path → đủ nhanh cho real-time.

## Limitations

1. **Dựa hoàn toàn trên mô phỏng:** Chưa được kiểm chứng trên bãi đỗ thực tế đang vận hành.
2. **Giả định về mức độ noncompliance:** Mô hình noncompliance được đơn giản hóa — thực tế đa dạng hơn.
3. **Yêu cầu hạ tầng cảm biến:** DCS đòi hỏi giám sát thời gian thực chính xác về vị trí từng xe → yêu cầu đầu tư IoT/sensor.
4. **Chưa tích hợp định giá và ưu tiên người dùng:** Tối ưu thuần túy về thời gian cruising, chưa xét chi phí hoặc ưu tiên cá nhân.
5. **Bối cảnh đặc thù AV:** Tỷ lệ AV ở hầu hết quốc gia (đặc biệt Việt Nam) rất thấp → ứng dụng thực tế còn hạn chế trong ngắn hạn.

## Relevance to our topic

Bài báo liên quan đến **RQ4** (cải thiện tỷ lệ sử dụng giờ cao điểm) và cung cấp nhiều ý tưởng cho hệ thống:

- **Thuật toán PCPT:** Mô hình tham khảo để tối ưu đường đi xe trong bãi — có thể đơn giản hóa thành hướng dẫn đường đi cho tài xế.
- **Chiến lược DCS:** Nguyên lý cập nhật liên tục phân bổ khi trạng thái thay đổi — phù hợp kiến trúc event-driven (Socket.IO) của hệ thống.
- **Conflict Resolution:** Cơ chế giải quyết xung đột khi 2 xe hướng đến cùng slot — áp dụng khi có nhiều request đồng thời.
- **Hướng nâng cấp tương lai:** Nguyên lý tối ưu iterative của DCS/PCPT có thể thay thế threshold-based load balancing đơn giản — cho phép phân bổ slot chính xác hơn khi bãi có lưu lượng cao.

## Possible improvement

1. **Đơn giản hóa DCS cho bãi đỗ thuần xe người lái:** Loại bỏ thành phần AV, giữ lại nguyên lý dynamic path guidance và conflict resolution → áp dụng cho bãi đỗ truyền thống.
2. **Tích hợp hướng dẫn đường đi vào App:** Kết hợp shortest path từ PCPT vào giao diện mobile — hiển thị đường đi tối ưu từ cổng vào đến slot.
3. **Áp dụng Deep Reinforcement Learning (DRL):** Thay thế tối ưu hóa lặp bằng DQN/DRL — agent học từ dữ liệu lịch sử để phân bổ tốt hơn, đặc biệt giờ cao điểm.
4. **Kết hợp với Load Balancing (RQ4):** Tích hợp nguyên lý DCS vào Threshold-based Load Balancing — khi tầng gần đầy, không chỉ chuyển hướng tầng mà còn tối ưu đường đi đến tầng mới.
