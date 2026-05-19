# Paper 07 Summary

### Citation
- **Tên bài:** CodEv: An Automated Grading Framework Leveraging Large Language Models for Consistent and Constructive Feedback
- **Tác giả:** En-Qi Tseng et al.
- **Năm:** 2025
- **Nguồn:** arXiv preprint
- **DOI/Link:** arXiv:2501.10421

### Problem
Bài giải quyết vấn đề chấm bài lập trình cần vừa có điểm số nhất quán vừa có feedback hữu ích. Các phương pháp cũ thường chỉ dựa trên output/testcases, trong khi cần đánh giá thêm readability, structure, correctness và feedback giúp người học cải thiện.

### Method
CodEv là framework LLM-based code evaluation. Bài dùng Chain-of-Thought prompting để tăng reasoning, LLM ensemble để tăng accuracy/consistency, agreement tests để kiểm tra độ tin cậy, và G-Eval để đánh giá chất lượng feedback.

### Dataset / Context
Programming assignments trong giáo dục lập trình. Bài không đặt trong bối cảnh hackathon nhưng sát với code grading.

### Evaluation
Đánh giá consistency intra-model và inter-model, so sánh với human evaluation, kiểm tra quality của feedback/code review comments.

### Results
Bài cho thấy framework có thể tạo grading results comparable to human evaluators, kể cả khi dùng smaller LLMs. CoT + ensemble + agreement tests giúp tăng tính ổn định và reliability của score/feedback.

### Limitations
- Là preprint.
- Không tập trung contest ranking.
- Có thể tốn chi phí nếu triển khai ensemble nhiều model trong MVP.

### Relevance to our topic
Mức độ liên quan: **Cao**. Bài này rất tốt cho AI Evaluation Engine và feedback generation.

### Possible improvement for our system
Áp dụng tối thiểu:
- Dùng structured prompt theo rubric.
- Thêm field `agreementStatus`, `needsHumanReview`.
- Nếu AI score không ổn định hoặc feedback quá chung chung thì yêu cầu judge review kỹ.

---

### Detailed application to our project
CodEv rất hữu ích để nâng cấp AI Evaluation Service từ mức “gọi 1 lần rồi lấy điểm” sang workflow có kiểm tra độ tin cậy.

#### Minimum CodEv-inspired feature
Trong MVP, nhóm có thể chưa cần ensemble nhiều model vì tốn chi phí. Nhưng có thể áp dụng dạng tối thiểu:

```text
Same code + same rubric
→ Run AI evaluation twice
→ Compare criterion scores
→ If score difference > threshold
→ Mark needsHumanReview = true
```

#### Suggested fields to add
```json
{
  "agreementStatus": "stable | unstable",
  "scoreVariance": {
    "functionality": 1,
    "code_quality": 3
  },
  "needsHumanReview": true
}
```

#### Research value
CodEv giúp nhóm có một đóng góp tốt hơn: hệ thống không tin điểm AI một cách mù quáng, mà kiểm tra consistency/agreement trước khi hiển thị điểm gợi ý cho judge.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
