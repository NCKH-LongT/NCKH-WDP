# Paper 07 Summary

## Citation

Tên bài: Online parking assignment in an environment of partially connected vehicles: A multi-agent deep reinforcement learning approach
Tác giả: Zhang, X., Zhao, C., Liao, F., Li, X. & Du, Y.
Năm: 2022
Nguồn: Transportation Research Part C: Emerging Technologies, Vol. 138, Article 103624. Elsevier (Scopus Q1, IF = 7.9, SJR = 2.734)
DOI/Link: [10.1016/j.trc.2022.103624](https://doi.org/10.1016/j.trc.2022.103624)

## Problem

Trong bãi đỗ xe thực tế, có sự pha trộn giữa **xe có kết nối mạng (Connected Vehicles — CVs)** có thể giao tiếp với hệ thống và **xe không kết nối (Non-Connected Vehicles — NCVs)** di chuyển tự do. Việc gán chỗ đỗ online cho CVs bị ảnh hưởng lớn bởi hành vi không dự đoán được của NCVs — khi CV đến nơi thì slot có thể đã bị NCV chiếm mất.

Phương pháp truyền thống FCFS (First-Come-First-Served) chỉ gán slot trống gần nhất mà không nhìn được bài toán tổng thể → dẫn đến lãng phí không gian và tắc nghẽn.

## Method

Tác giả đề xuất framework **Multi-Agent Deep Reinforcement Learning (MARL)** với kiến trúc centralized assignment:

1. **Agent 1:** Đo lường tác động của NCVs lên không gian trạng thái bãi đỗ — dự đoán slot nào có khả năng bị NCV chiếm.
2. **Agent 2:** Khai thác đặc tính đỗ xe của CVs — tối ưu phân bổ slot cho xe có kết nối.
3. **Phối hợp agents:** Hai agents học policy riêng rồi kết hợp theo cơ chế **value decomposition** → Joint Q-value để ra quyết định tổng thể.
4. **Exploration Strategy:** Epsilon-greedy với adaptive decay — giảm exploration nhanh hơn ở vùng state ổn định.

## Dataset

Bài báo sử dụng **dữ liệu mô phỏng giao thông hỗn hợp:**
- Mô phỏng môi trường partially connected với đa dạng tỷ lệ CVs/NCVs.
- Huấn luyện qua nhiều episodes (đợt) trong mạng nơ-ron sâu.
- Không sử dụng dataset bãi xe thực tế.

## Evaluation

| Metric | Mô tả |
|---|---|
| Allocation Efficiency | Khả năng tối ưu không gian bãi đỗ và giảm chi phí di chuyển của phương tiện |

So sánh với baseline: FCFS và các phương pháp greedy thông thường.

## Results

- Framework MARL cải thiện **15% hiệu quả phân bổ** so với baseline FCFS.
- MARL tìm được các chính sách điều phối phức tạp mà phương pháp tĩnh không làm được.
- Vượt trội rõ rệt hơn khi tỷ lệ pha trộn CVs/NCVs ở mức phức tạp — cho thấy khả năng xử lý môi trường uncertainty.

## Limitations

1. **Training tốn tài nguyên:** Quá trình huấn luyện MARL đòi hỏi phần cứng mạnh và thời gian dài để hội tụ.
2. **Hiệu năng giảm khi NCVs áp đảo:** Nếu tỷ lệ NCVs quá cao và hành vi hoàn toàn hỗn loạn, khả năng dự đoán của Agent 1 sẽ suy giảm.
3. **Chưa thử nghiệm quy mô lớn:** Chưa áp dụng trên mạng lưới bãi đỗ phân tán toàn thành phố.
4. **Khó giải thích (Explainability):** RL policy là black-box, khó giải thích cho người quản lý bãi xe tại sao hệ thống chọn slot X thay vì slot Y.

## Relevance to our topic

Bài báo liên quan đến **RQ2** (auto-assign vs. manual) và **RQ1** (phân bổ theo loại xe):

- **Centralized Assignment:** Nguyên lý hệ thống tập trung quyết định phân bổ slot → áp dụng trực tiếp vào kiến trúc backend của hệ thống (server-side slot assignment).
- **Hard Constraints:** Ý tưởng ràng buộc cứng (loại slot phải khớp loại xe) → áp dụng vào bước **Zone Filter** trong pipeline: `IF vehicle.type != floor.allowedType THEN skip`.
- **Khác biệt:** P7 dùng Reinforcement Learning (thử-sai, black-box), hệ thống của nhóm dùng WSM kết hợp AI dự báo (Supervised Learning) → dễ triển khai, dễ giải thích.

## Possible improvement

1. **Thay RL bằng WSM + ML:** RL khó triển khai thực tế → tách bài toán: dùng ML (Random Forest) để dự đoán lưu lượng, WSM để ra quyết định. Pipeline nhẹ, dễ debug và giải thích được (Explainable) cho Ban quản lý bãi xe.
2. **Tracking toàn bộ xe qua Check-in:** P7 đau đầu với NCVs vì không tracking được → hệ thống sử dụng Check-in tự động tại cổng (QR/RFID) để tracking toàn bộ xe, loại bỏ hoàn toàn "điểm mù".
3. **Tích hợp Peak Hour Prediction:** MARL phản ứng theo thời gian thực → hệ thống bổ sung "Peak Hour Probability" để tự động chuyển sang chế độ Load Balancing trước khi bãi thực sự đầy.
