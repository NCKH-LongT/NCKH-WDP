# Related Work

## 1. Tổng quan

Nghiên cứu này tập trung vào **AI-assisted source code evaluation and ranking based on dynamic rubrics in programming competitions**. Hệ thống quản lý Hackathon đóng vai trò là bối cảnh ứng dụng, nhưng đóng góp khoa học được giới hạn ở workflow hỗ trợ đánh giá bằng AI.

Phần related work được tổ chức thành năm nhóm:

```text
1. Dynamic / question-specific rubric-based code evaluation
2. Human-in-the-loop AI-assisted grading
3. Structured prompting for programming assessment
4. Evaluation methodology and AI-human score comparison
5. Reliability, consistency, and feedback quality
```

---

## 2. Dynamic and question-specific rubric-based code evaluation

Công trình liên quan nhất với hướng nghiên cứu này là **Rubric Is All You Need**. Bài báo này lập luận rằng đánh giá source code bằng LLM sẽ hiệu quả hơn khi sử dụng các rubric được thiết kế riêng cho từng bài toán lập trình cụ thể, thay vì dùng các rubric chung chung không phụ thuộc vào câu hỏi.

Điều này rất phù hợp với nghiên cứu của chúng tôi vì rubric trong Hackathon không cố định. Rubric có thể thay đổi theo mùa thi, vòng thi, track và problem statement. Do đó, hệ thống của chúng tôi sử dụng **dynamic rubrics**, có thể được cấu hình riêng cho từng bối cảnh đánh giá.

Bài báo đề xuất ba cách tiếp cận:

```text
- Complete Rubric Evaluation (CRE)
- Pointwise Rubric Evaluation (PRE)
- Ensembling Method Evaluation (EME)
```

Trong số đó, **Pointwise Rubric Evaluation** là hướng phù hợp nhất với hệ thống của chúng tôi. Cách tiếp cận này đánh giá từng rubric criterion riêng biệt và cung cấp feedback chi tiết. Điều này trực tiếp hỗ trợ thiết kế lưu kết quả AI trong `AiReviewCriterion`, trong đó mỗi criterion có suggested score, evidence, feedback và confidence riêng.

Đối với nghiên cứu của chúng tôi, bài báo này củng cố quyết định thiết kế sau:

```text
AI should not generate only one overall score.
AI should evaluate each rubric criterion separately.
```

---

## 3. Human-in-the-loop AI-assisted grading

**TA Buddy** là tài liệu tham khảo gần nhất về workflow cho dự án của chúng tôi. Hệ thống này sử dụng problem statement, source code submission và grading rubric để tạo ra các suggested ratings cho từng rubric criterion. Sau đó, human teaching assistants có thể accept hoặc override các gợi ý của AI.

Dự án của chúng tôi điều chỉnh ý tưởng này sang bối cảnh Hackathon:

```text
TA Buddy setting:
problem statement + student code + rubric
→ AI suggested criterion ratings
→ human TA accept/override
→ final grade

Our setting:
problem statement + GitHub source/diff + dynamic rubric
→ AI suggested criterion scores + evidence + feedback
→ judge accept/override
→ final score/ranking
```

Bài báo này hỗ trợ nguyên tắc **Human-in-the-loop** của chúng tôi:

```text
AI output is advisory, not final.
```

Trong hệ thống đề xuất, điểm cuối cùng chỉ được tính sau khi judge xác nhận thông qua scoring sheet.

---

## 4. Structured prompting for programming assessment

**StepGrade** là tài liệu tham khảo quan trọng nhất cho phần thiết kế prompt. Bài báo này cho thấy rằng việc đánh giá programming assignment không nên được xử lý bằng một prompt chung duy nhất. Thay vào đó, quá trình đánh giá nên được cấu trúc theo từng bước và xem xét nhiều khía cạnh, chẳng hạn như:

```text
- functionality
- code quality
- algorithmic efficiency
```

Nghiên cứu của chúng tôi điều chỉnh ý tưởng này vào bối cảnh **dynamic rubric**. Thay vì cố định các tiêu chí chỉ gồm functionality, quality và efficiency, prompt của chúng tôi đọc criteria từ database và đánh giá từng criterion riêng biệt.

Chiến lược prompt trở thành:

```text
1. Understand the problem statement.
2. Inspect the source code or GitHub diff.
3. Load the dynamic rubric.
4. Evaluate each AI-supported criterion.
5. Provide suggested score, evidence, feedback, and confidence.
6. Mark judge-only criteria as requiring human evaluation.
```

Cách tiếp cận này cho phép AI module linh hoạt giữa các mùa thi và vòng thi Hackathon khác nhau.

---

## 5. Evaluation methodology and AI-human comparison

**JorGPT** hữu ích cho phần phương pháp đánh giá vì bài báo này so sánh điểm do LLM tạo ra với điểm của human instructor và báo cáo các kết quả đánh giá định lượng. Bài báo cũng nhấn mạnh rằng rubric có thể được đưa vào prompt và human oversight là cần thiết để đảm bảo consistency và reliability.

Bài báo này định hướng evaluation plan của nghiên cứu. Nghiên cứu đề xuất sẽ so sánh:

```text
AI suggested scores vs judge scores
AI-supported ranking vs judge ranking
manual judging time vs AI-assisted judging time
```

Các metric được lấy cảm hứng từ hướng nghiên cứu này gồm:

```text
- Mean Absolute Error (MAE)
- Pearson correlation
- Spearman ranking correlation
- Top-k agreement
- judge override rate
- grading time reduction
```

Những metric này cho phép chúng tôi đánh giá liệu AI suggestions có đủ gần với human judgment hay không, và liệu chúng có thể hỗ trợ quá trình chấm điểm nhanh hơn hay không.

---

## 6. Reliability, consistency, and feedback quality

**CodEv** đóng góp vào khía cạnh reliability trong literature. Bài báo này sử dụng structured prompting, ý tưởng ensemble và agreement tests để cải thiện consistency của điểm số và feedback được tạo ra.

Ứng dụng hiện tại của chúng tôi chưa cần triển khai ensemble hoặc agreement testing ngay lập tức. Tuy nhiên, CodEv hữu ích cho phần thảo luận về limitations và future work.

Trong workflow hiện tại, reliability được xử lý theo cách đơn giản hơn:

```text
- AI provides confidence.
- AI marks uncertain cases with needsHumanReview.
- Judges can override AI suggestions.
```

Các phiên bản trong tương lai có thể bổ sung:

```text
- repeated AI reviews
- multi-model agreement
- consistency checks
- feedback quality evaluation
```

---

## 7. Additional supporting references

Bài báo **The Future of Grading Programming Assignments in Education** cung cấp bằng chứng thực nghiệm rằng các công cụ kiểu ChatGPT có thể chấm programming tasks và tạo feedback, nhưng đồng thời cũng cho thấy human verification vẫn cần thiết.

Một bài **LLM-as-a-Judge survey** tổng quát hỗ trợ phần thảo luận về reliability, bias, robustness và human alignment. Bài này giúp định vị AI module của chúng tôi như một công cụ hỗ trợ judge, thay vì một autonomous judge.

**Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena** hữu ích cho phần nền tảng chung về LLM-as-a-Judge và thảo luận về bias, nhưng bài này không tập trung riêng vào code. Do đó, chỉ nên cite ngắn nếu dung lượng bài cho phép.

---

## 8. Research gap

Các nghiên cứu hiện có cho thấy LLM có thể hỗ trợ chấm programming assignment bằng rubric, structured prompting và human oversight. Tuy nhiên, phần lớn các nghiên cứu này tập trung vào bối cảnh lớp học, nơi problem, rubric và submission format tương đối cố định.

Programming competitions và Hackathons tạo ra thêm các yêu cầu workflow khác:

```text
- team-based submissions
- GitHub repositories and commit evidence
- dynamic rubrics by season, round, and track
- judge scoring sheets
- final score calculation
- ranking and finalist selection
```

Do đó, research gap mà nghiên cứu này giải quyết là:

```text
How can existing LLM-assisted grading ideas be adapted into a Hackathon-style workflow that supports source code evidence, dynamic rubrics, judge accept/override, and ranking?
```

---

## 9. Summary of literature contribution

Năm bài báo cốt lõi định hình workflow đề xuất như sau:

```text
Rubric Is All You Need → dynamic rubric and criterion-level evaluation
TA Buddy               → human accept/override workflow
StepGrade              → structured prompting
JorGPT                 → evaluation metrics and human comparison
CodEv                  → reliability and future consistency checks
```

Kết hợp lại, các bài này hỗ trợ AI-assisted evaluation workflow được đề xuất:

```text
Input:
problem statement + GitHub source/diff + dynamic rubric

Method:
structured LLM prompting + human-in-the-loop review

Output:
suggested criterion scores + evidence + feedback + final judge-confirmed ranking
```
