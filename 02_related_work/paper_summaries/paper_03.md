# Paper 03 Summary

### Citation
- **Tên bài:** Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments: An Experience Report
- **Tác giả:** Goda Nagakalyani, Saurav Chaudhary, Varsha Apte, Ganesh Ramakrishnan, Srikanth Tamilselvam
- **Năm:** 2025
- **Nguồn:** ACM SIGCSE TS 2025
- **DOI:** 10.1145/3641554.3701913

### Problem
Bài báo giải quyết hạn chế của autograder truyền thống. Autograder thường chỉ compile/run code và kiểm tra test case, nhưng không đánh giá được source code quality, partial correctness hoặc các yêu cầu cụ thể trong đề bài như “phải dùng bubble sort”. Manual grading dựa trên đọc source code thì cần nhiều thời gian khi lớp đông.

### Method
Bài đề xuất **TA Buddy**, một AI-assisted source code grading tool. TA Buddy dùng Code Llama, được fine-tune bằng dataset gồm problem statements, rubrics, student submissions và ratings do human TAs gán. Input gồm problem statement, student code và grading rubric. Output là suggested ratings cho từng rubric criterion.

### Dataset
Tác giả tạo dataset từ 21 C++ programming assignments trong CS101 tại IIT Bombay, gồm 2914 submissions và 155 rubric criteria. Sau đó khoảng 24 TAs chấm thủ công các bài đã ẩn danh theo rubric để tạo dữ liệu fine-tuning.

### Evaluation
TA Buddy-assisted grading được so sánh với pure manual grading. Các câu hỏi đánh giá gồm: acceptance rate của AI-suggested grades, thời gian chấm có giảm không, và grade agreement giữa hai cách chấm.

### Results
Bài báo cáo thời gian chấm giảm **24%** trong khi vẫn giữ **90% grade agreement** giữa TA Buddy-assisted grading và pure manual grading. Đây là bằng chứng rất mạnh cho hướng AI-assisted grading có human-in-the-loop.

### Limitations
- Bối cảnh là programming assignments, không phải hackathon.
- Không tập trung ranking/leaderboard.
- Fine-tuning Code Llama cần dataset lớn và GPU, khó triển khai ngay nếu nhóm chưa có dữ liệu.

### Relevance to our topic
Mức độ liên quan: **Rất cao — Core paper**. Đây là bài sát nhất với hệ thống nhóm vì có workflow: **problem statement + source code + rubric → AI suggested grades → human accept/override → final grade**.

### Possible improvement for our system
Áp dụng trực tiếp vào hệ thống MERN:
1. Rubric động lưu trong MongoDB.
2. GitHub webhook lấy source code/diff.
3. AI service tạo suggested score cho từng criterion.
4. Judge xem score/evidence và accept/override.
5. Hệ thống tính final score và ranking.

---

### Detailed application to our MERN + React Native project
TA Buddy là bài quan trọng nhất để nhóm áp dụng trực tiếp vì mô hình của bài khớp với kiến trúc hệ thống: **problem statement + source code + grading rubric → AI suggested ratings → human accept/overrule**. Trong dự án nhóm, phần này có thể chuyển thành: **đề bài của bảng đấu + code/diff từ GitHub + rubric động từ MongoDB → AI suggested score → Judge xác nhận hoặc chỉnh sửa → final score/ranking**.

#### Minimum implementation inspired by TA Buddy
1. Admin tạo rubric trong Web Admin.
2. Rubric được lưu trong MongoDB theo từng round/bảng đấu.
3. GitHub webhook gửi event khi thí sinh push code.
4. Backend Node.js/Express lấy source snapshot hoặc commit diff.
5. Backend gửi `problemStatement`, `sourceCode/diff`, `rubric` sang AI Evaluation Service.
6. AI trả về điểm gợi ý cho từng tiêu chí, lý do và feedback.
7. Judge nhìn thấy AI suggestion trên giao diện chấm dạng sheet.
8. Judge có quyền accept hoặc override điểm AI.
9. Hệ thống dùng điểm judge-confirmed để tính ranking.

#### Suggested JSON output for our system
```json
{
  "teamId": "A03",
  "rubricId": "preliminary_rubric_v1",
  "criteriaResults": [
    {
      "criterionId": "code_quality",
      "suggestedScore": 7,
      "maxScore": 10,
      "evidence": "Functions are separated but naming is inconsistent.",
      "feedback": "Refactor repeated logic and use consistent names.",
      "needsHumanReview": true
    }
  ],
  "overallFeedback": "The implementation is mostly functional but requires better structure and validation."
}
```

#### Why this paper is suitable for the weekly report
- Có source code grading thật.
- Có rubric thật.
- Có AI suggested score theo từng criterion.
- Có human-in-the-loop.
- Có kết quả định lượng: giảm thời gian chấm và vẫn giữ agreement tốt với manual grading.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
