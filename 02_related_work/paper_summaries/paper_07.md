# Paper 19 — CodEv: An Automated Grading Framework Leveraging Large Language Models for Consistent and Constructive Feedback

## 1. Thông tin bài báo

- **Tên bài báo:** *CodEv: An Automated Grading Framework Leveraging Large Language Models for Consistent and Constructive Feedback*
- **Tác giả:** En-Qi Tseng, Pei-Cing Huang, Chan Hsu, Peng-Yi Wu, Chan-Tung Ku, Yihuang Kang
- **Năm:** 2025
- **Nguồn:** IEEE-style conference paper / arXiv PDF
- **Từ khóa chính:** LLM grading, CoT, LLM ensemble, code evaluation, consistency, constructive feedback
- **Vai trò trong nghiên cứu của nhóm:** **Core paper cho reliability, consistency và feedback quality**

---

## 2. Lý do chọn bài báo này

CodEv phù hợp vì nhóm cần chứng minh rằng AI-assisted grading không chỉ cần điểm gợi ý, mà còn cần:

```text
- feedback có ích;
- kết quả ổn định;
- kiểm tra độ nhất quán;
- độ tin cậy khi dùng LLM để hỗ trợ chấm code.
```

Trong dự án của nhóm, CodEv không nhất thiết phải được triển khai đầy đủ. Nhưng nó rất hữu ích cho phần:

```text
Discussion
Limitations
Future Work
Reliability Evaluation
```

---

## 3. Vấn đề nghiên cứu của bài báo

Bài báo cho rằng chấm code không chỉ là kiểm tra đúng/sai. Một đánh giá tốt cần xem xét:

```text
- functionality;
- readability;
- structure;
- maintainability;
- feedback cụ thể;
- consistency giữa các lần chấm.
```

Các phương pháp cũ dựa nhiều vào test case hoặc output comparison, dẫn đến feedback hạn chế. LLM có thể đọc code và sinh feedback tốt hơn, nhưng LLM cũng có vấn đề:

```text
- khó đảm bảo luôn làm theo instruction;
- có thể cho output không ổn định;
- có thể bias;
- có thể sinh feedback thiếu chính xác;
- chi phí cao nếu dùng model lớn.
```

CodEv đề xuất framework dùng CoT, LLM ensemble và agreement tests để tăng độ tin cậy.

---

## 4. Framework CodEv

CodEv có ba giai đoạn chính:

```text
1. Template Design
2. LLMs Ensemble
3. Robustness Testing and Result Generation
```

Theo diagram trong bài, workflow có thể hiểu như sau:

```text
Criteria + Question + Student code
→ Prompt template
→ LLMs generate multiple responses
→ Scores/comments
→ Agreement test
→ If reliable: final score
→ If not reliable: teacher check
```

Điểm quan trọng là CodEv không chỉ lấy một câu trả lời duy nhất của LLM. Nó tìm cách kiểm tra tính ổn định của output.

---

## 5. Template Design

CodEv xây prompt template dựa trên tiêu chí chấm. Template có thể bao gồm:

```text
- question;
- student code;
- criteria;
- instruction để đánh giá code;
- yêu cầu tạo score và comment.
```

Phần này tương tự dự án của nhóm:

```text
problem statement
+ GitHub diff/source
+ dynamic rubric
→ structured prompt
```

CodEv dùng CoT để model đánh giá sâu hơn thay vì chỉ trả kết quả ngắn.

---

## 6. LLM Ensemble

CodEv dùng nhiều response hoặc nhiều model để tăng độ ổn định.

Ý tưởng:

```text
LLM response 1
LLM response 2
LLM response 3
→ compare/vote/aggregate
→ final score/comment
```

Mục tiêu:

- giảm độ ngẫu nhiên;
- tăng consistency;
- tránh phụ thuộc một output duy nhất;
- cải thiện độ tin cậy của score và feedback.

## 6.1. Có cần áp dụng vào dự án không?

Không cần áp dụng ngay. Với app của nhóm, chỉ cần:

```text
single structured AI review
+ judge accept/override
```

Ensemble nên để:

```text
future work
hoặc optional reliability mode
```

---

## 7. Robustness Testing và Result Generation

CodEv kiểm tra độ ổn định của kết quả bằng:

```text
- intra-model consistency;
- inter-model consistency;
- agreement tests;
- feedback quality evaluation.
```

Bài cũng dùng G-Eval để đánh giá chất lượng feedback.

Ý tưởng quan trọng:

```text
Không nên chỉ tin một lần output của LLM.
Cần có cơ chế phát hiện khi AI không chắc hoặc output thiếu ổn định.
```

Trong dự án nhóm, điều này có thể ánh xạ thành:

```text
confidence
needsHumanReview
riskLevel
```

Nếu AI confidence thấp, UI judge nên đánh dấu tiêu chí đó cần xem kỹ.

---

## 8. Input, Output, Method theo IOM

## 8.1. Input

CodEv dùng:

```text
student code
+ question/problem
+ criteria
```

Trong dự án nhóm:

```text
GitHub diff/source
+ problem statement
+ dynamic rubric
+ optional execution result
```

## 8.2. Output

CodEv tạo:

```text
scores
+ review comments
+ feedback
```

Trong dự án nhóm:

```text
suggestedScore
+ evidence
+ feedback
+ confidence
+ needsHumanReview
```

## 8.3. Method

CodEv dùng:

```text
CoT prompting
+ LLM ensemble
+ agreement test
+ feedback quality evaluation
```

Trong dự án nhóm:

```text
structured prompting là phần áp dụng chính;
ensemble/agreement test là phần mở rộng.
```

---

## 9. Kết quả và ý nghĩa

CodEv cho thấy framework LLM-based có thể tạo điểm và feedback tương đối phù hợp với human evaluation, đồng thời nhấn mạnh rằng consistency/reliability là yếu tố cần kiểm soát.

Điểm hữu ích nhất cho nhóm không phải là phải làm ensemble ngay, mà là bài cung cấp lý do để nhóm đưa các field như:

```text
confidence
needsHumanReview
riskLevel
```

vào AI output.

---

## 10. Điểm mạnh của bài báo

1. Có workflow/framework rõ ràng.
2. Có CoT prompting.
3. Có LLM ensemble.
4. Có agreement tests.
5. Có đánh giá feedback quality.
6. Nhấn mạnh consistency và reliability.
7. Phù hợp cho phần discussion/future work của bài nghiên cứu nhóm.

---

## 11. Hạn chế của bài báo

1. Bối cảnh vẫn là programming assignments.
2. Không có human judge accept/override workflow rõ như TA Buddy.
3. Ensemble có thể tốn chi phí và thời gian.
4. Không xử lý dynamic rubric theo event/round/track.
5. Không tập trung vào ranking/finalist.
6. Có thể phức tạp hơn nhu cầu MVP của dự án nhóm.

---

## 12. Ứng dụng vào nghiên cứu khoa học của nhóm

CodEv nên được dùng ở ba phần:

## 12.1. Related Work

Dùng để nói rằng nhiều nghiên cứu đã dùng CoT/ensemble để tăng chất lượng LLM grading.

## 12.2. Method Discussion

Dùng để giải thích tại sao AI output nên có:

```text
confidence
needsHumanReview
risk warnings
```

## 12.3. Future Work

Dùng để đề xuất:

```text
- gọi AI nhiều lần để kiểm tra consistency;
- dùng ensemble giữa nhiều model;
- agreement test trước khi hiển thị suggestion;
- feedback quality rating.
```

---

## 13. Ứng dụng vào dự án Hackathon

Trong app, không cần triển khai full CodEv.

## Nên áp dụng ngay

```text
- structured prompt;
- confidence;
- needsHumanReview;
- evidence-based feedback.
```

## Có thể để sau

```text
- LLM ensemble;
- agreement testing;
- G-Eval feedback quality;
- multi-model comparison.
```

---

## 14. Mapping với DB hiện tại

| CodEv concept | Dự án nhóm |
|---|---|
| Criteria/question | `rubrics`, `criterions`, `tracks.problemStatement` |
| Student code | `commitdiffs`, `submissions` |
| Prompt template | prompt file / AI service |
| LLM response | `aireviews` |
| Score/comment per criterion | `aireviewcriterions` |
| Agreement/reliability | future: `confidence`, repeat review, model runs |
| Teacher check | Judge review in `scoresheets` |

---

## 15. Đưa vào Related Work như thế nào?

Đoạn có thể dùng:

```text
CodEv proposes an LLM-based code evaluation framework that uses CoT prompting, LLM ensemble methods, and agreement tests to improve the consistency and reliability of scores and feedback. While our current prototype does not implement full ensemble-based evaluation, CodEv motivates the inclusion of confidence and human-review flags in our AI-assisted judging workflow.
```

Bản tiếng Việt:

```text
CodEv đề xuất một framework đánh giá code bằng LLM, sử dụng CoT prompting, LLM ensemble và agreement tests để tăng tính nhất quán và độ tin cậy của điểm số và feedback. Dù prototype hiện tại của nhóm không triển khai đầy đủ ensemble-based evaluation, CodEv giúp nhóm có cơ sở để đưa confidence và human-review flags vào workflow AI-assisted judging.
```

---

## 16. Kết luận lựa chọn

**Quyết định:** Giữ làm **core paper số 5**.

**Mức độ liên quan:** 8.5/10.

**Vai trò:** Nền tảng cho reliability, consistency và future work.

**Cách áp dụng:**

```text
CoT / structured prompt
→ AI criterion feedback
→ confidence + needsHumanReview
→ future ensemble/agreement test
```

CodEv giúp bài nghiên cứu của nhóm có phần thảo luận vững hơn về giới hạn của LLM và cách tăng độ tin cậy khi áp dụng AI vào chấm source code.
