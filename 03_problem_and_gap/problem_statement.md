# Problem Statement

SEAL Hackathon là cuộc thi phần mềm có nhiều mùa, nhiều chủ đề, nhiều track và nhiều vòng chấm điểm. Các mùa thi gần đây như Fall 2025 và Spring 2026 cho thấy rubric có thể thay đổi mạnh theo chủ đề, ví dụ AI Agents for Software Innovation hoặc Domain-Specific AI RAG Systems. Điều này yêu cầu hệ thống chấm điểm phải hỗ trợ rubric động thay vì hard-code tiêu chí.

Trong quá trình thi, giám khảo phải đánh giá nhiều đội trong thời gian ngắn. Việc chấm thủ công có thể gặp các vấn đề:

1. Tốn thời gian đọc source code, README, demo và slide.
2. Khó đảm bảo nhất quán giữa nhiều giám khảo.
3. Khó truy vết bằng chứng kỹ thuật từ GitHub repository.
4. Khó đánh giá nhanh các tiêu chí kỹ thuật như architecture, AI integration, code quality, RAG pipeline hoặc reliability.
5. Khó tổng hợp điểm và ranking trong thời gian ngắn.

Các autograder truyền thống chỉ dựa vào test case không đủ cho hackathon, vì sản phẩm không chỉ cần đúng chức năng mà còn cần kiến trúc, khả năng tích hợp AI, documentation, UX, demo, teamwork và tính sáng tạo.

Vì vậy, dự án đề xuất một workflow **IOM-based AI-assisted evaluation**. AI nhận input gồm source code/diff từ GitHub, problem statement, dynamic rubric, README và metadata liên quan. AI trả output gồm suggested score theo từng tiêu chí, evidence, feedback, confidence và flag cần human review. Method sử dụng LLM prompting có cấu trúc, học từ TA Buddy và StepGrade, kết hợp human judge accept/override.

Điểm chính thức vẫn do giám khảo quyết định. AI chỉ đóng vai trò trợ lý đánh giá để hỗ trợ quá trình chấm nhanh hơn, rõ bằng chứng hơn và dễ so sánh hơn.
