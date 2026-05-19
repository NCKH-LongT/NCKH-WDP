# Paper 11 Summary

### Citation
- **Tên bài:** StepGrade: Grading Programming Assignments with Context-Aware LLMs
- **Tác giả:** Mohammad Akyash, Kimia Zamiri Azar, Hadi Mardani Kamali
- **Năm:** 2025
- **Nguồn:** arXiv preprint
- **DOI/Link:** arXiv:2503.20851

### Problem
Bài giải quyết hạn chế của regular prompting và autograder truyền thống. Autograder thường chỉ kiểm tra output correctness, trong khi regular prompting dễ tạo feedback nông, thiếu reasoning và không nhìn thấy sự liên kết giữa functionality, code quality và efficiency.

### Method
StepGrade dùng Chain-of-Thought prompting với GPT-4 để đánh giá code theo từng bước. Framework đánh giá ba tiêu chí chính: functionality, code quality và algorithmic efficiency. Mỗi bước nhận assignment question, submitted code và context từ bước trước để tạo grade và feedback.

### Dataset
30 Python programming assignments ở ba mức độ: easy, intermediate, advanced. Các bài gồm factorial, palindrome, sorting, binary search, Dijkstra, knapsack, Sudoku, API integration, CRUD SQLite, linear regression, v.v.

### Evaluation
So sánh CoT prompting với regular prompting, dùng expert human evaluations làm reference. Đánh giá grading quality, interpretability, accuracy và fairness.

### Results
CoT prompting consistently outperformed regular prompting. Bài cho thấy CoT tạo feedback cụ thể hơn, ví dụ gợi ý kiểm tra HTTP status code, validation, docstring, tên biến rõ hơn, pagination/response limit cho performance.

### Limitations
- Dataset nhỏ, chỉ 30 Python assignments.
- Là preprint.
- Không có dynamic rubric, GitHub webhook hay contest ranking.

### Relevance to our topic
Mức độ liên quan: **Rất cao cho prompt design**. Đây là bài nên áp dụng cùng TA Buddy.

### Possible improvement for our system
Áp dụng vào AI service:
- AI không chấm chung chung.
- AI phân tích từng criterion.
- AI phải nêu evidence từ code/diff.
- AI trả feedback ngắn và actionable cho judge.

---

### Detailed application to our MERN AI Evaluation Service
StepGrade nên được dùng để thiết kế prompt của AI service. Điểm quan trọng là không prompt AI kiểu “hãy chấm code”, mà phải yêu cầu đánh giá theo từng bước và từng tiêu chí.

#### Prompt design inspired by StepGrade
```text
You are an AI grading assistant for a programming competition.
Evaluate the submitted code using the rubric below.
For each criterion:
1. Identify evidence from the code or commit diff.
2. Explain strengths and weaknesses briefly.
3. Assign a score from 0 to maxScore.
4. Provide actionable feedback for the judge.
Return only valid JSON.
```

#### Criterion flow
```text
Functionality evaluation
→ Code quality evaluation
→ Algorithmic efficiency evaluation
→ Documentation/requirement compliance evaluation
→ Final suggested score
```

#### Why StepGrade is important
StepGrade giúp hệ thống tăng tính giải thích được. Judge không chỉ thấy điểm AI, mà còn thấy “vì sao AI đề xuất điểm đó”. Điều này rất cần trong cuộc thi vì điểm số ảnh hưởng đến ranking và giải thưởng.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
