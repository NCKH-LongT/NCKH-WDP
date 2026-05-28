# Paper 17 — StepGrade: Grading Programming Assignments with Context-Aware LLMs

## 1. Thông tin bài báo

- **Tên bài báo:** *StepGrade: Grading Programming Assignments with Context-Aware LLMs*
- **Tác giả:** Mohammad Akyash, Kimia Zamiri Azar, Hadi Mardani Kamali
- **Năm:** 2025
- **Nguồn:** arXiv
- **Từ khóa chính:** Chain-of-Thought prompting, programming assignments, automated grading, code quality, functionality, efficiency
- **Vai trò trong nghiên cứu của nhóm:** **Core paper cho structured prompting / step-by-step criterion evaluation**

---

## 2. Lý do chọn bài báo này

StepGrade phù hợp vì nhóm cần thiết kế prompt để AI đánh giá source code theo rubric một cách rõ ràng, không hỏi chung chung kiểu:

```text
Hãy chấm source code này.
```

Thay vào đó, nhóm cần prompt có cấu trúc:

```text
1. Hiểu đề bài.
2. Đọc source/diff.
3. Đánh giá từng criterion.
4. Tìm evidence.
5. Gợi ý score.
6. Viết feedback ngắn.
7. Đánh dấu confidence/needsHumanReview.
```

StepGrade cung cấp nền tảng cho cách thiết kế đó.

---

## 3. Vấn đề nghiên cứu của bài báo

Bài báo cho rằng chấm bài lập trình là công việc tốn thời gian và cần đánh giá nhiều chiều. Các hệ thống chấm tự động truyền thống thường tập trung vào output correctness, nhưng bỏ qua:

- code readability;
- maintainability;
- modularity;
- algorithmic efficiency;
- feedback có tính sư phạm;
- mối liên hệ giữa các tiêu chí.

Regular prompting cũng có hạn chế:

1. Đánh giá rời rạc, không có reasoning rõ.
2. Feedback dễ chung chung.
3. Kết quả thiếu nhất quán.
4. Không thể hiện được vì sao model cho điểm như vậy.

StepGrade đề xuất dùng **Chain-of-Thought style structured prompting** để chia quá trình chấm thành nhiều bước có liên hệ với nhau.

---

## 4. Workflow của StepGrade

StepGrade đánh giá code qua ba nhóm tiêu chí chính:

```text
1. Functionality
2. Code Quality
3. Algorithmic Efficiency
```

Luồng tổng quát:

```text
Assignment question + submitted code
→ Functionality evaluation
→ Code quality evaluation using previous functionality context
→ Algorithmic efficiency evaluation using previous outputs
→ Final grade + detailed feedback
```

Điểm đáng chú ý: bước sau có thể sử dụng context từ bước trước. Ví dụ, khi đánh giá efficiency, hệ thống có thể dùng kết quả functionality và code quality để hiểu code đang hoạt động như thế nào trước khi nhận xét về performance.

---

## 5. Ba bước đánh giá chính

## 5.1. Functionality Evaluation

Mục tiêu:

```text
Code có đáp ứng yêu cầu bài toán không?
Có xử lý đúng output không?
Có bỏ sót edge cases không?
Có lỗi logic không?
```

Prompt yêu cầu model:

- phân tích output;
- kiểm tra standard cases;
- kiểm tra edge cases;
- xác định missing functionality;
- đưa feedback;
- gợi ý grade.

## 5.2. Code Quality Evaluation

Mục tiêu:

```text
Code có dễ đọc không?
Tên biến/hàm rõ không?
Có modular không?
Có tránh lặp code không?
Có maintainable không?
```

Prompt yêu cầu model:

- xem readability;
- xem variable naming;
- xem comments;
- xem organization;
- xem best practices;
- xem maintainability;
- đưa feedback cụ thể.

## 5.3. Algorithmic Efficiency Evaluation

Mục tiêu:

```text
Code có hiệu quả không?
Time complexity/space complexity thế nào?
Có bottleneck không?
Có thể tối ưu bằng data structure/algorithm khác không?
```

Prompt yêu cầu model:

- phân tích time/space complexity;
- tìm bottleneck;
- gợi ý optimization;
- đánh giá scalability;
- đưa feedback.

---

## 6. Input, Output, Method theo IOM

## 6.1. Input

StepGrade dùng:

```text
assignment question
+ submitted code
+ context từ các bước trước
```

Trong dự án của nhóm, input tương ứng là:

```text
problem statement
+ GitHub diff/source
+ dynamic rubric
+ execution results nếu có
+ README/demo/metadata nếu có
```

## 6.2. Output

StepGrade tạo:

```text
grade
+ detailed feedback
+ reasoning theo từng tiêu chí
```

Trong dự án của nhóm, output nên là:

```text
suggestedScore
+ evidence
+ feedback
+ confidence
+ needsHumanReview
```

## 6.3. Method

Method quan trọng nhất là **structured step-by-step prompting**.

Trong app của nhóm, không nên hiển thị reasoning dài cho judge. Chỉ nên yêu cầu AI đánh giá có cấu trúc, sau đó trả về output ngắn gọn:

```text
evidence + feedback + suggestedScore
```

---

## 7. Kết quả và ý nghĩa của bài báo

StepGrade cho thấy structured prompting giúp kết quả có:

- grading quality tốt hơn regular prompting;
- feedback rõ hơn;
- tính diễn giải tốt hơn;
- đánh giá nhiều chiều hơn;
- phù hợp hơn với human evaluation.

Bài cũng thực nghiệm trên 30 Python assignments ở nhiều mức độ khó: easy, intermediate, advanced. Điều này cho thấy framework có thể áp dụng cho nhiều loại bài lập trình khác nhau.

---

## 8. Điểm mạnh của bài báo

1. Rất hữu ích cho thiết kế prompt.
2. Chia evaluation thành nhiều bước rõ ràng.
3. Tập trung vào functionality, code quality và efficiency.
4. Có detailed prompts có thể học theo.
5. Giúp output dễ giải thích hơn.
6. Phù hợp với rubric-based AI review.

---

## 9. Hạn chế của bài báo

1. Chỉ tập trung vào programming assignment, chưa phải team project/hackathon.
2. Bộ tiêu chí chính là functionality, code quality, efficiency; chưa có AI integration, demo, teamwork.
3. Không có workflow judge accept/override rõ như TA Buddy.
4. Không tập trung vào ranking.
5. Nếu để model giải thích quá dài, UI judge có thể bị rối.

---

## 10. Ứng dụng vào nghiên cứu khoa học của nhóm

StepGrade nên được dùng làm nền cho phần **Method / Prompt Design**.

Trong bài báo của nhóm, có thể viết:

```text
The proposed workflow adapts StepGrade-style structured evaluation by requiring the LLM to evaluate each rubric criterion separately. Instead of asking the model for a single overall score, the prompt guides the model to inspect source code evidence, identify strengths and weaknesses, and generate concise evidence-based feedback for each criterion.
```

Bản tiếng Việt:

```text
Workflow của nhóm học theo cách đánh giá có cấu trúc của StepGrade bằng cách yêu cầu LLM đánh giá từng tiêu chí rubric riêng biệt. Thay vì yêu cầu model đưa ra một điểm tổng, prompt hướng dẫn model đọc evidence từ source code, xác định điểm mạnh/yếu và tạo feedback ngắn gọn theo từng tiêu chí.
```

---

## 11. Ứng dụng vào dự án Hackathon

Trong app, StepGrade có thể áp dụng ở mức prompt template.

Prompt đề xuất:

```text
Step 1: Understand the problem statement and expected outcome.
Step 2: Inspect source code / GitHub diff / execution results.
Step 3: For each AI-supported rubric criterion, identify code evidence.
Step 4: Provide concise feedback.
Step 5: Suggest a score from 0 to maxScore.
Step 6: Mark confidence and needsHumanReview.
Step 7: For judge-only criteria, do not assign a score.
```

Không cần triển khai toàn bộ StepGrade framework. Chỉ cần dùng tư tưởng structured prompting.

---

## 12. Mapping với DB hiện tại

| StepGrade concept | Dự án nhóm |
|---|---|
| Assignment question | `tracks.problemStatement` |
| Submitted code | `commitdiffs`, `submissions` |
| Functionality evaluation | Criterion tương ứng trong `criterions` |
| Code quality evaluation | Criterion tương ứng trong `criterions` |
| Efficiency evaluation | Criterion tương ứng trong `criterions` |
| Feedback | `aireviewcriterions.feedback` |
| Grade | `aireviewcriterions.suggestedScore` |

---

## 13. Cách đưa vào Related Work

Đoạn có thể dùng:

```text
StepGrade demonstrates that structured step-by-step prompting can improve programming assignment grading by evaluating functionality, code quality, and algorithmic efficiency in a context-aware manner. This motivates our prompt design, where the LLM evaluates each dynamic rubric criterion separately and returns concise evidence, feedback, and suggested scores for human judges.
```

Bản tiếng Việt:

```text
StepGrade cho thấy prompting có cấu trúc theo từng bước giúp cải thiện việc chấm bài lập trình bằng cách đánh giá functionality, code quality và algorithmic efficiency theo ngữ cảnh. Điều này truyền cảm hứng cho thiết kế prompt của nhóm, trong đó LLM đánh giá từng tiêu chí rubric động riêng biệt và trả về evidence, feedback và điểm gợi ý cho judge.
```

---

## 14. Kết luận lựa chọn

**Quyết định:** Giữ làm **core paper số 3**.

**Mức độ liên quan:** 9/10.

**Vai trò:** Nền tảng cho structured prompting / criterion-by-criterion evaluation.

**Cách áp dụng:**

```text
StepGrade-style prompt
→ evaluate rubric criteria step by step
→ generate concise evidence + feedback + suggested score
```

Đây là bài giúp nhóm viết phần Method rõ ràng và tránh prompt AI theo kiểu chung chung, thiếu kiểm soát.
