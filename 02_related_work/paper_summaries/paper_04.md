# Paper 18 — JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models (LLMs)

## 1. Thông tin bài báo

- **Tên bài báo:** *JorGPT: Instructor-Aided Grading of Programming Assignments with Large Language Models (LLMs)*
- **Tác giả:** Jorge Cisneros-González, Natalia Gordo-Herrera, Iván Barcia-Santos, Javier Sánchez-Soriano
- **Năm:** 2025
- **Nguồn:** Future Internet, MDPI
- **Từ khóa chính:** LLM grading, programming assignments, rubric, automated assessment, human instructor, evaluation metrics
- **Vai trò trong nghiên cứu của nhóm:** **Core paper cho methodology, metrics và human comparison**

---

## 2. Lý do chọn bài báo này

JorGPT phù hợp vì bài này không chỉ nói rằng LLM có thể chấm code, mà còn trình bày cách **so sánh kết quả chấm của LLM với human instructor**.

Đây là phần nhóm cần cho bài báo khoa học:

```text
AI suggested score
vs
Judge score
```

Và các chỉ số cần đo:

```text
MAE
correlation
feedback quality
execution time
cost
human oversight
```

Trong dự án của nhóm, app không cần triển khai so sánh nhiều model như JorGPT, nhưng bài báo của nhóm có thể học JorGPT để thiết kế **evaluation plan**.

---

## 3. Vấn đề nghiên cứu của bài báo

Bài báo đặt vấn đề rằng chấm bài lập trình thủ công rất tốn thời gian và có thể thiếu nhất quán, ngay cả khi có rubric. Trong các lớp lập trình nhập môn, instructor phải chấm nhiều bài và feedback cần nhanh, rõ, công bằng.

Bài báo đề xuất một hệ thống hỗ trợ instructor bằng LLM, cho phép:

```text
- xử lý student submissions;
- chọn LLM;
- tùy chỉnh rubric;
- tạo grade;
- tạo feedback;
- so sánh với human instructor grades.
```

Điểm quan trọng: bài không chỉ tập trung vào output điểm, mà còn quan tâm feedback, workload và consistency.

---

## 4. Workflow của JorGPT

Workflow tổng quát:

```text
1. Instructor chuẩn bị submissions.
2. Instructor chọn LLM trong giao diện.
3. Instructor có thể chỉnh rubric.
4. Hệ thống gửi code + rubric đến LLM.
5. LLM tạo grade và feedback.
6. Kết quả được xuất ra để instructor kiểm tra.
7. Điểm LLM được so sánh với điểm human instructor.
```

Bài nhấn mạnh rằng rubric có thể được đưa trực tiếp vào prompt để model điều chỉnh response theo guideline.

---

## 5. Input, Output, Method theo IOM

## 5.1. Input

JorGPT dùng:

```text
student code submissions
+ grading rubric
+ selected LLM configuration
```

Trong dự án nhóm:

```text
GitHub diff/source
+ problem statement
+ dynamic rubric
+ optional execution results
```

## 5.2. Output

JorGPT tạo:

```text
LLM-generated grades
+ feedback
```

Trong dự án nhóm:

```text
suggestedScore per criterion
+ evidence
+ feedback
+ confidence
+ judge questions
```

## 5.3. Method

JorGPT dùng nhiều LLM và so sánh kết quả với human instructor. Phần nhóm nên học là:

```text
- đưa rubric vào prompt;
- đo độ gần giữa AI score và human score;
- phân tích feedback;
- đo thời gian/cost;
- giữ human oversight.
```

---

## 6. Kết quả thực nghiệm quan trọng

Bài báo báo cáo rằng mô hình rút gọn dựa trên các biến có ý nghĩa thống kê đạt:

```text
adjusted R² = 0.9156
MAE = 0.4579
```

Điều này cho thấy điểm do LLM tạo ra có thể có mức độ phù hợp cao với điểm của human instructor trong bối cảnh bài báo.

Bài cũng nêu rằng công việc chấm thủ công ước tính hơn 300 giờ có thể được xử lý tự động trong dưới 15 phút trong thiết lập của họ. Tuy nhiên, kết quả này không có nghĩa là AI nên thay thế hoàn toàn con người. Bài vẫn nhấn mạnh vai trò giám sát của instructor.

---

## 7. Điểm mạnh của bài báo

1. Có hệ thống thực nghiệm rõ ràng.
2. Có nhiều LLM để so sánh.
3. Có rubric trong workflow.
4. Có human instructor grades làm reference.
5. Có metric định lượng như MAE, adjusted R², Pearson correlation.
6. Có phân tích thời gian và chi phí.
7. Phù hợp để học cách thiết kế evaluation methodology.

---

## 8. Hạn chế của bài báo

1. Bối cảnh vẫn là programming assignment, chưa phải Hackathon.
2. Tập trung vào final grade hơn là criterion-level judge accept/override.
3. Không xử lý GitHub commit diff hoặc repository workflow.
4. Không có ranking/finalist như cuộc thi.
5. Multi-model comparison không cần thiết cho MVP của nhóm.
6. Dataset và setup có thể khác nhiều so với team-based submissions.

---

## 9. Ứng dụng vào nghiên cứu khoa học của nhóm

JorGPT nên được dùng để viết phần **Methodology** và **Evaluation Metrics**.

Nhóm có thể học các điểm sau:

```text
1. So sánh AI score với human judge score.
2. Dùng MAE để đo sai lệch điểm.
3. Dùng correlation để đo xu hướng giống nhau.
4. Phân tích feedback quality.
5. Đo thời gian chấm.
6. Nhấn mạnh human oversight.
```

Bài báo của nhóm không cần so sánh nhiều LLM ngay. Có thể viết:

```text
Although JorGPT compares multiple LLMs, our current study focuses on a single AI-assisted workflow. Multi-model comparison is considered future work.
```

---

## 10. Ứng dụng vào dự án Hackathon

Trong app, JorGPT gợi ý rằng cần lưu đủ dữ liệu để phân tích sau này:

```text
AI suggested score
Judge final score
Override reason
Time spent
Feedback usefulness
```

Các field/collection liên quan:

```text
aireviewcriterions.suggestedScore
scores.scoreValue
scores.aiSuggestedScore
scores.isOverridden
scores.overrideReason
scoresheets.submittedAt
```

---

## 11. Mapping với DB hiện tại

| JorGPT concept | Dự án nhóm |
|---|---|
| Student submissions | `submissions`, `repositories` |
| Rubric | `rubrics`, `criterions` |
| LLM grade | `aireviewcriterions.suggestedScore` |
| LLM feedback | `aireviewcriterions.feedback` |
| Human instructor grade | `scores.scoreValue` |
| Evaluation output | MAE, correlation, override rate |
| Instructor review | Judge review in `scoresheets` |

---

## 12. Metrics nên lấy từ JorGPT

Các metric nên đưa vào bài báo nhóm:

```text
MAE: độ lệch tuyệt đối trung bình giữa AI score và Judge score.
Pearson correlation: AI score có cùng xu hướng với Judge score không.
Execution time: AI-assisted review mất bao lâu.
Feedback quality: judge đánh giá feedback có hữu ích không.
```

Nhóm có thể bổ sung thêm metric phù hợp với cuộc thi:

```text
Spearman rank correlation
Top-k agreement
Human override rate
Criterion-level error
```

---

## 13. Đưa vào Related Work như thế nào?

Đoạn có thể dùng:

```text
JorGPT evaluates the use of multiple LLMs for grading programming assignments and compares LLM-generated grades with human instructor grades using quantitative metrics such as adjusted R² and MAE. This work informs our evaluation methodology, particularly the need to measure score alignment, feedback usefulness, and grading efficiency between AI suggestions and human judge decisions.
```

Bản tiếng Việt:

```text
JorGPT đánh giá việc sử dụng nhiều LLM để chấm bài lập trình và so sánh điểm do LLM tạo ra với điểm của human instructor bằng các chỉ số định lượng như adjusted R² và MAE. Nghiên cứu này giúp nhóm thiết kế methodology, đặc biệt là cách đo độ gần giữa điểm AI gợi ý và điểm judge, chất lượng feedback và hiệu quả thời gian chấm.
```

---

## 14. Kết luận lựa chọn

**Quyết định:** Giữ làm **core paper số 4**.

**Mức độ liên quan:** 8.5/10.

**Vai trò:** Nền tảng cho evaluation methodology.

**Cách áp dụng:**

```text
AI score vs Judge score
→ MAE / correlation / ranking similarity
→ human oversight
→ time reduction
```

Bài này giúp bài nghiên cứu của nhóm không chỉ dừng ở đề xuất workflow, mà còn có cách đánh giá workflow một cách khoa học.
