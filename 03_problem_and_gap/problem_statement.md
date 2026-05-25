# Problem Statement

## Current Challenges

### Problem 1: Phân bổ chỗ đỗ thủ công gây lãng phí diện tích
- **Description:** Tại các tòa nhà đỗ xe đa tầng, tài xế tự tìm chỗ đỗ (free-choice) dẫn đến hiện tượng dồn xe ở tầng thấp trong khi tầng cao còn trống. Đặc biệt nghiêm trọng khi xe máy và ô tô không được phân khu rõ ràng — xe máy chiếm chỗ ô tô và ngược lại, gây lãng phí diện tích đáng kể [5].
- **Impact:** Nghiên cứu tại campus cho thấy khu ô tô chỉ sử dụng 14.51% capacity trong khi khu xe máy quá tải 150.24% [8]. Tài xế xe máy tại TP.HCM mất trung bình 3.3 phút tìm chỗ đỗ [9], trong khi ô tô mất trung bình 8.1 phút [7]. Giờ cao điểm gây ùn tắc lối đi nội bộ.
- **Current solutions:** Nhân viên chỉ tay, biển báo tĩnh, hoặc đèn LED đếm chỗ trống theo tầng — không có phân bổ tự động đến từng slot.

### Problem 2: Thiếu hệ thống đặt chỗ trước cho xe máy
- **Description:** Các hệ thống reservation hiện tại chỉ phục vụ ô tô tại các thị trường phương Tây. Tại Việt Nam — nơi xe máy chiếm đa số phương tiện — chưa có giải pháp đặt chỗ trước cho xe máy trong parking building. Tài xế xe máy phải xếp hàng chung với ô tô tại cổng, tăng queuing time — yếu tố tiêu cực nhất ảnh hưởng đến quyết định chọn bãi đỗ theo khảo sát 318 tài xế tại TP.HCM [9].
- **Impact:** 38% tài xế xe máy phải dừng hỏi đường tìm chỗ, 28% chạy lòng vòng [9]. Parking index xe máy tại campus đạt 150.24% (quá tải gấp rưỡi) trong khi ô tô chỉ 14.51% [8].
- **Current solutions:** Không có. Literature review 99 papers [7] xác nhận: chưa có nghiên cứu nào về reservation system phân biệt "two-wheeler vs four-wheeler."

### Problem 3: Không có dữ liệu đánh giá hiệu quả thuật toán phân bổ
- **Description:** Các bãi xe hiện tại không log dữ liệu phân bổ (strategy nào, mất bao lâu, slot nào, tầng nào). Manager không có cơ sở để biết thuật toán phân bổ có hiệu quả hay không, hoặc so sánh giữa các phương pháp khác nhau.
- **Impact:** Không thể cải tiến vận hành dựa trên data. Quyết định quản lý dựa trên cảm tính thay vì metrics.
- **Current solutions:** Một số nghiên cứu dùng simulation (Entropy-Based DP, Smart Parking Guidance) nhưng chỉ cho ô tô, flat parking lot, hoặc city-wide — không áp dụng cho multi-floor building có cả xe máy.

## Why This Matters

Tại Việt Nam, xe máy chiếm đa số phương tiện nhưng hạ tầng parking building được thiết kế theo chuẩn ô tô phương Tây. Khi tòa nhà đỗ xe đa tầng ngày càng phổ biến tại các đô thị lớn (TP.HCM, Hà Nội, Đà Nẵng), bài toán phân bổ slot cho hỗn hợp xe máy + ô tô trở nên cấp thiết:

- **Kinh tế:** Bãi xe hoạt động dưới công suất = mất doanh thu. Hệ thống reservation có thể tăng 17% lượt xe phục vụ/ngày [6].
- **Trải nghiệm:** Tài xế mất thời gian tìm chỗ = giảm hài lòng. Hệ thống guidance giảm 15.51% lượng xe chạy lòng vòng [3].
- **Vận hành:** Không có data = không cải tiến được. Hệ thống cần log metrics để manager ra quyết định dựa trên evidence.

## Existing Approaches and Their Limitations

| Approach | Ưu điểm | Hạn chế |
|---|---|---|
| Constraint Optimization [1] | Phân bổ theo priority + zone | Chỉ flat zones, không multi-floor, không xét loại xe |
| Dynamic Programming [4] | Chọn tầng tối ưu cho multi-story | Chỉ cho ô tô, chưa test thực tế |
| Smart Parking Guidance [3] | Giảm 15% xe chạy lòng vòng | City-wide (nhiều bãi), không phân biệt xe máy/ô tô |
| GA Reservation [6] | Tăng 17% utilization | Giả định user đến đúng giờ, không xét tầng/khoảng cách |
| Free-choice (không guidance) | Đơn giản, không cần hệ thống | Dồn tầng thấp, search time cao, không data |

**Điểm chung:** Chưa có approach nào kết hợp đồng thời multi-floor + phân khu xe máy/ô tô + reservation + simulation đánh giá.

## Our Problem Definition

Xây dựng hệ thống phân bổ slot tự động cho tòa nhà đỗ xe 3 tầng, 90 slot (30 ô tô + 60 xe máy), giải quyết:

1. Phân khu nghiêm ngặt theo loại xe (car → Zone A, motorbike → Zone B)
2. Cân bằng tải giữa các tầng để tránh 1 tầng quá tải
3. Hỗ trợ đặt chỗ trước với tự động hủy sau 30 phút
4. Log metrics mỗi session để đánh giá hiệu quả
5. Simulation so sánh thuật toán dưới các kịch bản tải khác nhau

---

## References

- [1] Constraint Optimization Model for Dynamic Parking Space Allocation, 2024
- [2] ParkGauge: Gauging the Occupancy of Parking Garages with Crowdsensed Parking Characteristics, NTU, 2016
- [3] Smart Parking Guidance: A Step Towards Sustainable Cities
- [4] Entropy-Based Dynamic Programming for Efficient Vehicle Parking
- [5] Study of Parking Patterns for Different Parking Facilities
- [6] Optimization Model of Parking Space Allocation Based on Genetic Algorithm
- [7] Parking Reservation Techniques: A Review of Research Topics, Considerations, and Optimization Methods, 2023
- [8] Planning Campus Parking Facilities Using Parking Demand Analysis, 2024
- [9] Motorcycle Drivers' Parking Lot Choice Behaviors in Developing Countries: Analysis for Ho Chi Minh City, Vietnam, 2019

---

Date: 2026-05-21
