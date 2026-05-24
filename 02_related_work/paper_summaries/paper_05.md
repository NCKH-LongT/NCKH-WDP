# Paper 05 Summary

## Citation

Tên bài: New Parking Lot Selection Approach Based on the Multi-Criteria Decision Making (MCDM) Methods: Health Criteria
Tác giả: Amari, A., Moussaid, L. & Tallal, S.
Năm: 2023
Nguồn: Sustainability, Vol. 15, No. 2, Article 938. MDPI (Scopus Q2, IF = 3.3, CiteScore = 5.8)
DOI/Link: [10.3390/su15020938](https://doi.org/10.3390/su15020938)

## Problem

Bài báo giải quyết vấn đề **lựa chọn bãi đỗ xe tối ưu dựa trên nhiều tiêu chí (multi-criteria parking lot selection):**

- **Tìm chỗ đỗ gây phát thải CO₂:** Tài xế di chuyển nhiều khi tìm chỗ đỗ → tăng phát thải khí nhà kính.
- **Nhiều tiêu chí cạnh tranh:** Khoảng cách, chi phí, tình trạng giao thông, slot trống — khó đánh giá đồng thời.
- **Tiêu chí sức khỏe bị bỏ qua:** Nghiên cứu trước đây chưa xét **thể trạng người lái (health criteria)** — ví dụ người khuyết tật, người cao tuổi, hoặc người có vấn đề sức khỏe cần chỗ đỗ gần hơn.

## Method

Tác giả đề xuất **framework MCDM (Multi-Criteria Decision Making)** kết hợp nhiều phương pháp:

1. **CRITIC (CRiteria Importance Through Intercriteria Correlation):** Xác định trọng số **khách quan (objective weights)** cho mỗi tiêu chí — thay vì gán trọng số chủ quan. Trọng số tỷ lệ với độ lệch chuẩn (σ) và mức độ xung đột giữa các tiêu chí (1 - correlation).
   - Công thức: `W_j = (σ_j × Σ(1 - r_jk)) / Σ_all`

2. **Bốn phương pháp MCDM được so sánh:**
   - **TOPSIS:** Xếp hạng dựa trên khoảng cách đến giải pháp lý tưởng (Ideal Best A⁺) và xấu nhất (Ideal Worst A⁻).
   - **CODAS (Combinative Distance-based Assessment):** Kết hợp Euclid distance và Taxicab distance.
   - **EDAS (Evaluation based on Distance from Average Solution):** Đánh giá dựa trên khoảng cách từ giải pháp trung bình.
   - **WASPAS (Weighted Aggregated Sum Product Assessment):** Kết hợp WSM và WPM.

3. **Phương pháp đánh giá mới:** Đề xuất **"average inter-item correlation SW"** — kết hợp "average inter-item correlation" và hệ số SW — để đánh giá mức độ tương quan giữa các phương pháp MCDM và chọn phương pháp tốt nhất.

## Dataset

Bài báo sử dụng **case study minh họa (illustrative case study):**

- **Kịch bản:** Nhiều bãi đỗ xe ứng viên với các đặc tính khác nhau (khoảng cách, chi phí, slot trống, tình trạng giao thông, hạ tầng cho người khuyết tật).
- **Tiêu chí đánh giá:** Khoảng cách đến cổng, chi phí đỗ xe, tình trạng giao thông xung quanh, thể trạng người lái (health criteria).
- **Ma trận quyết định:** Xây dựng decision matrix với các bãi đỗ là alternatives, các tiêu chí là criteria.

## Evaluation

| Metric | Mô tả |
|---|---|
| Ranking Consistency | Mức độ nhất quán trong xếp hạng giữa các phương pháp MCDM |
| Average Inter-item Correlation SW | Hệ số đánh giá tương quan giữa phương pháp và tập hợp các phương pháp |
| Objective Weight Distribution | Phân bổ trọng số khách quan bằng CRITIC |

So sánh: 4 phương pháp MCDM (TOPSIS, CODAS, EDAS, WASPAS) trên cùng bộ dữ liệu.

## Results

- **CRITIC tạo trọng số khách quan hiệu quả:** Tránh thiên kiến chủ quan khi đánh giá tầm quan trọng tiêu chí.
- **TOPSIS cho kết quả ổn định nhất:** Xếp hạng nhất quán với hầu hết các phương pháp khác.
- **Health criteria có ảnh hưởng đáng kể:** Khi xét thể trạng người lái, thứ tự xếp hạng bãi đỗ thay đổi — chứng tỏ tiêu chí này không nên bỏ qua.
- **Average inter-item correlation SW:** Phương pháp đánh giá mới cho phép chọn MCDM phù hợp nhất cho bài toán cụ thể.

## Limitations

1. **Case study quy mô nhỏ:** Chỉ minh họa trên số lượng bãi đỗ hạn chế — chưa kiểm chứng quy mô lớn.
2. **Tiêu chí health đơn giản hóa:** Chỉ xét "bodily fragility" — chưa phân loại chi tiết các loại khuyết tật.
3. **Chưa tích hợp real-time:** Dữ liệu đầu vào là tĩnh — chưa cập nhật theo thời gian thực.
4. **Tập trung parking lot selection:** Chọn bãi đỗ nào (giữa nhiều bãi), chưa chọn slot nào trong bãi.

## Relevance to our topic

Bài báo liên quan đến **RQ3** (tiêu chí ưu tiên phân bổ slot) và cung cấp:

- **CRITIC weighting:** Cơ sở lý thuyết cho Weighted Scoring Model (WSM) — hệ thống sử dụng 4 trọng số (W1-W4) cấu hình được, ban đầu gán mặc định nhưng có thể tối ưu hóa bằng CRITIC trong tương lai.
- **TOPSIS framework:** WSM là phiên bản đơn giản hóa của TOPSIS — giữ nguyên ý tưởng xếp hạng theo điểm tổng hợp (weighted sum) nhưng bỏ qua Ideal Best/Worst (giảm complexity cho real-time).
- **Health criteria:** Mở ra khả năng thêm tiêu chí ưu tiên cho người khuyết tật (slot gần thang máy) — tiêu chí bổ sung cho WSM.

## Possible improvement

1. **Áp dụng CRITIC cho auto-tuning trọng số WSM:** Thu thập dữ liệu thực tế → chạy CRITIC để tính W1-W4 khách quan thay vì gán mặc định.
2. **Thêm tiêu chí health vào WSM:** Bổ sung W5 = accessibility score cho slot gần thang máy/cửa ra → phục vụ người có nhu cầu đặc biệt.
3. **Nâng cấp WSM lên TOPSIS:** Khi hệ thống có đủ dữ liệu, chuyển từ WSM đơn giản sang TOPSIS đầy đủ (với Ideal Best/Worst) để cải thiện chất lượng xếp hạng.
4. **Dynamic weight adjustment:** Trọng số thay đổi theo ngữ cảnh — giờ cao điểm ưu tiên W2 (load balancing), giờ thấp điểm ưu tiên W1 (distance).
