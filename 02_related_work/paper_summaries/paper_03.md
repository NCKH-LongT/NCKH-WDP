# Paper 03 Summary

## Citation

Tên bài: Reducing Street Parking Search Time via Smart Assignment Strategies
Tác giả: Hemmatpour, B., Dogani, J. & Laoutaris, N.
Năm: 2025
Nguồn: arXiv preprint (arXiv:2508.19979) — đồng thời công bố tại ACM (DOI: 10.1145/3748636.3762748)
DOI/Link: [arXiv:2508.19979](https://arxiv.org/abs/2508.19979)

## Problem

Bài báo giải quyết vấn đề **thời gian tìm chỗ đỗ xe trên đường phố (street parking search time)** tại các khu vực đô thị mật độ cao:

- **Tìm kiếm không phối hợp (uncoordinated search):** Tài xế tự tìm chỗ đỗ theo kinh nghiệm cá nhân → gây tắc nghẽn giao thông và lãng phí nhiên liệu.
- **Hiệu quả của ứng dụng di động chưa được lượng hóa:** Nhiều ứng dụng hỗ trợ tìm chỗ đỗ đã được đề xuất, nhưng tác động thực tế đến thời gian tìm kiếm chưa được nghiên cứu đầy đủ.
- **Hành vi người dùng không đồng nhất:** Chỉ một phần tài xế sử dụng hệ thống phối hợp (system users) — phần còn lại (non-users) hành động độc lập, gây nhiễu cho chiến lược phân bổ.

## Method

Tác giả đề xuất và so sánh **4 chiến lược phân bổ chỗ đỗ:**

1. **Unc-Agn (Uncoordinated-Agnostic):** Baseline — mô phỏng tài xế tự tìm chỗ, không có hệ thống hỗ trợ.
2. **Cord-Agn (Coordinated-Agnostic):** Phối hợp giữa system users nhưng không biết vị trí non-users.
3. **Cord-Oracle:** Hệ thống lý tưởng biết chính xác vị trí tất cả non-users — dùng làm upper bound.
4. **Cord-Approx (đề xuất chính):** Ước lượng hành vi non-users bằng **phân phối xác suất từ dữ liệu lịch sử (past occupancy distributions)** → kéo dài khoảng cách ảo (elongate physical distances) giữa system users và slot có nguy cơ bị non-user chiếm → giải bài toán **Hungarian matching** trên tập slot đã điều chỉnh.

**Thuật toán cốt lõi:**

- **Hungarian Algorithm (Kuhn-Munkres):** Giải bài toán đối sánh hoàn hảo trọng số tối thiểu (minimum-weight bipartite matching). Ma trận cost `C[i][j]` = thời gian di chuyển từ xe `i` đến slot `j` (đã điều chỉnh bởi xác suất non-user chiếm). Độ phức tạp: O(n³).

## Dataset

Bài báo sử dụng **mô phỏng dựa trên dữ liệu thực (data-driven simulation):**

- **Khu vực:** Hệ thống đỗ xe trên đường phố thành phố **Madrid, Tây Ban Nha**.
- **Dữ liệu thực tế:** Sử dụng dữ liệu giao thông thực (real traffic data) về lưu lượng xe và tỷ lệ lấp đầy.
- **Mô phỏng cao cấp (high-fidelity):** Tái tạo hệ thống đỗ xe trên đường phố bao gồm nhiều khu vực (central hubs, residential areas).

## Evaluation

| Metric | Mô tả |
|---|---|
| Average Search Time | Thời gian trung bình để tìm chỗ đỗ — metric chính |
| Search Time Reduction | Phần trăm giảm thời gian tìm chỗ so với non-users |
| Zone-level Performance | Hiệu quả theo từng khu vực (trung tâm vs. khu dân cư) |

So sánh: 4 chiến lược (Unc-Agn, Cord-Agn, Cord-Oracle, Cord-Approx).

## Results

- **Cord-Approx: trung bình 6.69 phút** để tìm chỗ đỗ, so với **19.98 phút** cho non-users — giảm đáng kể.
- **Giảm 72% thời gian tìm kiếm** (range 67–76%) tại các trung tâm (central hubs).
- **Giảm lên đến 73%** tại khu dân cư (residential areas).
- Hiệu quả tăng khi tỷ lệ adoption (người dùng hệ thống) ≥ 30%.

## Limitations

1. **Preprint chưa peer-review:** Kết quả chưa được kiểm chứng bởi hội đồng khoa học độc lập.
2. **Bối cảnh đỗ xe trên đường phố:** Tập trung vào street parking — khác biệt đáng kể với bãi đỗ xe trong nhà (indoor parking lot).
3. **Giả định về hành vi non-users:** Ước lượng bằng phân phối xác suất — thực tế hành vi có thể biến đổi phức tạp hơn.
4. **Chưa xét tiêu chí đa mục tiêu:** Chỉ tối ưu thời gian tìm kiếm — chưa xét chi phí, loại xe, hoặc ưu tiên cá nhân.

## Relevance to our topic

Bài báo liên quan đến **RQ2** (phân bổ tự động vs. chọn tự do) và cung cấp:

- **Hungarian Algorithm:** Cơ sở lý thuyết cho thuật toán phân bổ slot tối ưu — hệ thống đơn giản hóa thành Greedy Matching cho single-facility.
- **Cord-Approx Strategy:** Ý tưởng ước lượng hành vi bên ngoài (non-users) có thể áp dụng khi hệ thống chỉ quản lý một phần xe trong bãi (xe có đặt chỗ vs. xe walk-in).
- **Bằng chứng định lượng:** Giảm 72–76% thời gian tìm chỗ — chứng minh giá trị của phân bổ tự động so với tự tìm.

## Possible improvement

1. **Điều chỉnh Hungarian cho indoor parking:** Thay ma trận cost dựa trên khoảng cách đường phố bằng khoảng cách trong bãi (distanceToGate, floorLevel).
2. **Kết hợp với WSM (RQ3):** Sử dụng Greedy Matching làm cơ chế dispatch, kết hợp WSM làm hàm đánh giá đa tiêu chí.
3. **Áp dụng cho bài toán walk-in vs. reserved:** Dùng ý tưởng Cord-Approx để ước lượng slot nào sẽ bị walk-in chiếm → ưu tiên phân bổ slot an toàn hơn cho reserved users.
