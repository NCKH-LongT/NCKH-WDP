# Paper 06 Summary

## Citation

Tên bài: A Multi-Criteria Parking Space Proposing System based on Cheetah Optimizer Algorithm
Tác giả: Shirazi, F. & Farzaneh, N.
Năm: 2025
Nguồn: Journal of Artificial Intelligence and Data Mining (JAIDM), Vol. 13, No. 4, pp. 441–451. Shahrood University of Technology (Scopus-indexed, open access)
DOI/Link: [10.22044/jadm.2025.15911.2705](https://doi.org/10.22044/jadm.2025.15911.2705)

## Problem

Trong bãi đỗ xe đông đúc, việc chỉ dựa vào một tiêu chí duy nhất (ví dụ: khoảng cách gần nhất) để gợi ý chỗ đỗ xe là không đủ để tối ưu trải nghiệm người dùng. Cần một hệ thống gợi ý đa tiêu chí (khoảng cách, chi phí, độ sẵn sàng) có khả năng cá nhân hóa. Các phương pháp truyền thống hoặc thuật toán tối ưu hóa cũ (như GA) thường hội tụ chậm và không phù hợp cho ra quyết định thời gian thực (real-time) trong môi trường biến động liên tục.

## Method

Tác giả đề xuất hệ thống tối ưu hóa chỗ đỗ xe sử dụng **COA (Cheetah Optimization Algorithm)** — thuật toán metaheuristic lấy cảm hứng từ sinh học (mô phỏng hành vi săn mồi của loài báo ghê-ta).

Thuật toán chạy qua 3 pha:
1. **Search (Exploration):** Quét không gian giải rộng — khám phá nhiều vùng giải khác nhau.
2. **Sit-and-Wait (Exploitation):** Khai thác vùng lân cận của giải tốt đã tìm được.
3. **Attack (Convergence):** Hội tụ nhanh về giải pháp tối ưu.

Hàm fitness: `f(x) = α × distance + β × cost + γ × availability`

Benchmark so sánh với GA (Genetic Algorithm) và WOA (Whale Optimization Algorithm).

## Dataset

Bài báo sử dụng **dữ liệu mô phỏng (simulated data):**
- Mô phỏng nhiều kịch bản bãi đỗ xe với cấu hình slot, lưu lượng xe khác nhau.
- Chạy trong môi trường mô phỏng thời gian thực (real-time scenarios).
- Số lượng mẫu cụ thể không được đề cập chi tiết.

## Evaluation

| Metric | Mô tả |
|---|---|
| Convergence Speed | Thời gian để thuật toán hội tụ về giải pháp tối ưu |
| Solution Quality | Điểm số tối ưu đa tiêu chí của chỗ đỗ được gợi ý |

## Results

- COA cho kết quả **vượt trội** so với cả GA và WOA về cả **tốc độ hội tụ** và **chất lượng giải pháp**.
- Hoạt động đặc biệt hiệu quả trong các kịch bản thời gian thực đòi hỏi tốc độ ra quyết định nhanh.
- COA thể hiện khả năng cá nhân hóa gợi ý chỗ đỗ xe tốt nhờ tối ưu đa tiêu chí.

## Limitations

1. **Metaheuristic không đảm bảo Global Optimum:** Thuật toán có thể bị kẹt ở Local Optimum nếu không cấu hình tham số tốt.
2. **Chưa triển khai thực tế:** Kết quả chỉ trên mô phỏng, chưa kiểm chứng với bãi xe vật lý kết hợp IoT.
3. **Tốn tài nguyên tính toán:** Metaheuristic thường yêu cầu tính toán nhiều hơn so với heuristic đơn giản (WSM, Greedy).

## Relevance to our topic

Bài báo liên quan trực tiếp đến **RQ3** (ưu tiên tiêu chí khi phân bổ slot):

- **Tương đồng:** Cùng giải quyết bài toán phân bổ chỗ đỗ xe dựa trên nhiều tiêu chí (multi-criteria optimization).
- **Khác biệt:** P6 dùng thuật toán tiến hóa sinh học COA, hệ thống của nhóm dùng WSM tĩnh hơn nhưng dễ triển khai và giải thích được.
- **Áp dụng:** Nghiên cứu chứng minh rằng tối ưu hóa đa tiêu chí cải thiện chất lượng phân bổ so với đơn tiêu chí → hỗ trợ giả thuyết RQ3. COA được liệt kê như **hướng nâng cấp tương lai** thay thế WSM.

## Possible improvement

1. **Kết hợp AI dự đoán:** P6 tối ưu tại thời điểm hiện tại → có thể mớm dữ liệu từ Peak Hour Prediction vào hàm fitness của COA để tính toán đón đầu tương lai.
2. **Giảm search space bằng Zone Filtering:** Metaheuristic tốn tài nguyên → chạy Zone Filter trước (loại slot không phù hợp loại xe) rồi mới chạy COA trên tập slot đã lọc → giảm thời gian phản hồi.
3. **Kiểm chứng trên seed data:** Áp dụng luồng logic COA vào dataset 500+ sessions để đo hiệu năng thực thay vì chỉ mô phỏng.
