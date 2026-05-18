# Paper 04 Summary

## Citation

Tên bài:  
Hackverse: Hackathon Management & Collaboration Platform

Tác giả:  
M. Malathi, Manasadevi J, Menakha Priya N, Pavithra A

Năm:  
2026

Nguồn:  
International Journal of Engineering Development and Research (IJEDR), Volume 14, Issue 2

DOI/Link:  
https://rjwave.org/ijedr/papers/IJEDR2602182.pdf

---

## Problem

Bài báo giải quyết các vấn đề của việc quản lý hackathon bằng nhiều công cụ rời rạc như:

- Google Forms để đăng ký,
- WhatsApp để giao tiếp,
- spreadsheets để tổng hợp điểm.

Việc sử dụng nhiều công cụ độc lập dẫn đến:

- dữ liệu không đồng nhất,
- thiếu giao tiếp thời gian thực,
- khó theo dõi sự hiện diện và tiến độ,
- tổng hợp điểm thủ công và tốn thời gian,
- thông báo không hiệu quả,
- phân quyền người dùng chưa rõ ràng,
- trải nghiệm giao diện thiếu tính tương tác.

Mục tiêu của bài báo là xây dựng một nền tảng tập trung giúp quản lý toàn bộ vòng đời hackathon trên cùng một hệ thống.

---

## Method

Bài báo đề xuất hệ thống "Hackverse" — một nền tảng quản lý hackathon theo mô hình cloud-native Single-Page Application (SPA) với kiến trúc 3 tầng.

### Frontend

- React 19
- TypeScript
- Vite

### Backend

- Appwrite Backend-as-a-Service (BaaS)

Appwrite được sử dụng để xử lý:

- authentication,
- database,
- file storage,
- realtime WebSocket subscriptions.

### 3D Interface

Hệ thống tích hợp:

- Three.js
- React Three Fiber

để xây dựng không gian điều hướng 3D tương tác.

### Role-Based Access Control

Hệ thống hỗ trợ 3 vai trò chính:

- Organizer,
- Judge,
- Participant.

---

## Dataset

Bài báo không sử dụng dataset AI hoặc machine learning dataset.

Dữ liệu của hệ thống được sinh ra trong quá trình vận hành và được lưu trữ trong các collections của Appwrite, bao gồm:

- profiles,
- events,
- teams,
- submissions,
- evaluations,
- notifications.

---

## Evaluation

Hệ thống được đánh giá bằng:

### Functional Testing

- kiểm tra workflow,
- role-based access control,
- route protection.

### Performance Testing

Các metric chính gồm:

- realtime message latency,
- file upload duration,
- 3D rendering performance (FPS).

---

## Results

Kết quả chính của hệ thống:

- tất cả 15 functional test cases đều pass,
- role-based route protection hoạt động chính xác,
- realtime message latency trung bình khoảng 85 ms,
- upload file 50 MB hoàn thành dưới 12 giây,
- giao diện 3D đạt khoảng 60 FPS trên laptop GPU tầm trung.

Ngoài ra hệ thống còn:

- cải thiện realtime collaboration,
- giảm việc tổng hợp điểm thủ công,
- hỗ trợ leaderboard realtime,
- cải thiện user engagement nhờ immersive UI.

---

## Limitations

Hạn chế của bài báo:

- không sử dụng AI,
- chưa có AI-assisted evaluation,
- không hỗ trợ GitHub repository tracking,
- không có source code analysis,
- chưa tích hợp webhook-driven architecture,
- chưa hỗ trợ advanced analytics dashboard,
- chưa có mobile native application,
- chưa hỗ trợ video conferencing,
- chưa áp dụng gamification đầy đủ.

Ngoài ra việc sử dụng giao diện 3D có thể làm tăng complexity và resource consumption.

---

## Relevance to our topic

Bài báo rất liên quan đến đề tài SEAL ở góc độ:

- hackathon lifecycle management,
- realtime collaboration,
- role-based access control,
- realtime leaderboard,
- participant workflow management,
- centralized event platform architecture.

SEAL có thể học hỏi từ bài báo về:

- realtime architecture,
- WebSocket-based notifications,
- live leaderboard systems,
- team collaboration workflow,
- role isolation,
- cloud-native SPA design.

Ngoài ra bài báo cũng cung cấp tham khảo tốt cho:

- frontend architecture,
- event workflow management,
- participant experience design.

---

## Possible improvement

SEAL có thể mở rộng và cải tiến thêm bằng cách:

- tích hợp GitHub API,
- hỗ trợ repository tracking,
- xử lý GitHub webhooks,
- thêm AI-assisted source code review,
- hỗ trợ rubric-based judging,
- tích hợp AI-generated review summaries,
- xây dựng judge dashboard với AI analytics,
- thêm commit activity analysis,
- benchmark nhiều AI providers,
- hỗ trợ realtime repository monitoring.

Ngoài ra SEAL cũng có thể mở rộng:

- gamification system,
- advanced analytics dashboard,
- realtime competition analytics,
- AI-human collaborative evaluation workflow,
- repository-level performance metrics.