# Paper 01 Summary

## Citation

Tên bài: A Multi-Agent System for Parking Allocation: An Approach to Allocate Parking Spaces
Tác giả: Icarte-Ahumada, G., He, Z., Godoy, V., García, F. & Oyarzún, M.
Năm: 2025
Nguồn: Electronics, Vol. 14, No. 5, Article 840. MDPI (Scopus Q1, IF = 2.6, CiteScore = 6.1)
DOI/Link: [10.3390/electronics14050840](https://doi.org/10.3390/electronics14050840)

## Problem

Bài báo giải quyết vấn đề phân bổ chỗ đỗ xe trong bãi xe thông minh khi nhiều xe cùng đến và cần được gán vào slot phù hợp. Vấn đề cụ thể:
- Mỗi xe có đặc tính riêng (kích thước, loại xe) và mỗi slot có ràng buộc tương thích.
- Khi nhiều xe yêu cầu đồng thời, cần cơ chế phối hợp để tránh xung đột (2 xe tranh 1 slot).
- Phương pháp phân bổ tuần tự (serial) gây chậm khi lượng xe lớn.

## Method

Sử dụng hệ thống **đa tác tử (Multi-Agent System — MAS)** với **Contract Net Protocol (CNP):**

1. **Kiến trúc MAS:** Mỗi xe và mỗi slot đỗ là một agent tự trị. Xe-agent gửi yêu cầu (Call-for-Proposal), slot-agent đánh giá khả năng tương thích (vehicle size, type compatibility) và trả lời (Bid).
2. **Contract Net Protocol:** Xe-agent nhận các Bid → chọn Bid tốt nhất → Award cho slot-agent.
3. **Bốn cơ chế phối hợp được đánh giá:**
   - **Serial:** Từng xe đàm phán tuần tự.
   - **Serial with Decommitment:** Tuần tự nhưng cho phép hủy cam kết nếu tìm slot tốt hơn.
   - **Concurrent:** Nhiều xe đàm phán song song.
   - **Concurrent with Decommitment:** Song song + cho phép hủy cam kết.
4. **Decommitment Mechanism:** Cho phép hủy cam kết (decommit) nếu tìm được slot tốt hơn, tránh lock-in sớm vào slot không tối ưu.

## Dataset

Bài báo sử dụng **mô phỏng (simulation):**
- Bãi xe giả lập với số lượng slot và xe khác nhau.
- Các kịch bản thay đổi theo tỷ lệ xe/slot (occupancy rate) và mức độ đa dạng loại xe.
- Không sử dụng dataset thực tế từ bãi xe cụ thể.

## Evaluation

Các metric đánh giá:
- **Allocation Success Rate:** Tỷ lệ xe được gán slot thành công.
- **Average Allocation Time:** Thời gian trung bình từ khi xe yêu cầu đến khi được gán slot.
- **Slot Utilization Rate:** Tỷ lệ slot được sử dụng hiệu quả (tương thích đúng loại xe).
- **Decommitment Count:** Số lần hủy cam kết — đánh giá mức overhead của cơ chế decommitment.

## Results

Kết quả chính:
- **Concurrent + Decommitment** là cơ chế hiệu quả nhất: giảm thời gian phân bổ đáng kể so với Serial, đồng thời tăng tỷ lệ sử dụng slot.
- Cơ chế Concurrent giảm latency phân bổ nhờ đàm phán song song thay vì tuần tự.
- Decommitment cải thiện chất lượng phân bổ (tránh lock-in sớm) với overhead chấp nhận được.
- Khi occupancy rate cao (>80%), lợi ích của Concurrent + Decommitment càng rõ rệt.

## Limitations

- **Mô phỏng, không có dữ liệu thực tế:** Kết quả chưa được kiểm chứng trên bãi xe thật với lưu lượng xe thực.
- **Hạ tầng MAS phức tạp:** Yêu cầu mỗi xe và slot phải là agent tự trị → chi phí triển khai cao cho bãi xe vừa và nhỏ.
- **Chưa xét multi-criteria:** Phân bổ chỉ dựa trên vehicle-type compatibility, chưa xét các tiêu chí khác (khoảng cách, tầng, thời gian gửi).
- **Không xử lý reservation:** Chưa tính đến slot đã đặt trước.

## Relevance to our topic

**Liên quan trực tiếp đến RQ1** (phân tầng theo loại phương tiện):
- Nguyên lý phân bổ slot dựa trên đặc tính phương tiện (kích thước, loại xe) của P1 là nền tảng cho **Dynamic Vehicle-Type Zoning** trong hệ thống — nơi mỗi tầng được dành riêng cho loại xe cụ thể.
- Contract Net Protocol cung cấp mô hình lý thuyết cho cơ chế matching vehicle ↔ slot, mặc dù hệ thống của chúng tôi đơn giản hóa thành rule-based zoning thay vì MAS đầy đủ.

## Possible improvement

1. **Đơn giản hóa MAS thành rule-based:** Thay vì triển khai MAS với agent cho mỗi xe/slot, hệ thống sử dụng rule-based zoning: `IF vehicle.type == floor.allowedType THEN eligible`.
2. **Bổ sung multi-criteria scoring:** P1 chỉ dựa trên vehicle-type match → hệ thống bổ sung WSM scoring (RQ3) với 4 tiêu chí: khoảng cách, tỷ lệ lấp đầy, thời gian gửi, tầng ưu tiên.
3. **Thêm reservation-aware:** P1 không xét reservation → hệ thống tích hợp reservation-aware capacity (từ [P10]).
4. **Kiểm chứng trên dữ liệu thực/giả lập:** So sánh auto-assign vs. manual qua A/B testing với seed data 500+ sessions.
