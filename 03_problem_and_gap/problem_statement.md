# Problem Statement

Trong hackathon/cuộc thi lập trình, BTC phải quản lý đăng ký đội, xác nhận thành viên, check-in, cấp quyền GitHub, theo dõi commit, chấm điểm theo rubric, tổng hợp ranking và thu hồi quyền repo sau cuộc thi. Nếu làm thủ công, workflow tốn thời gian và dễ sai sót.

Phần khó nhất là đánh giá source code. Giám khảo phải đọc nhiều repository trong thời gian ngắn, trong khi rubric có thể thay đổi theo vòng thi hoặc mùa thi. Autograder truyền thống thường chỉ kiểm tra output/test case, chưa đánh giá tốt code quality, readability, architecture, documentation, efficiency hoặc requirement compliance.

Nhóm đề xuất hệ thống MERN + React Native tích hợp GitHub Automation và AI-assisted grading. AI gợi ý điểm theo từng rubric criterion, nhưng judge vẫn xác nhận cuối cùng.
