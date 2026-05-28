# Paper 16 — Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments: An Experience Report (TA Buddy)

## 1. Thông tin bài báo

- **Tên bài báo:** *Design and Evaluation of an AI-Assisted Grading Tool for Introductory Programming Assignments: An Experience Report*
- **Tên hệ thống:** TA Buddy
- **Tác giả:** Goda Nagakalyani, Saurav Chaudhary, Varsha Apte, Ganesh Ramakrishnan, Srikanth Tamilselvam
- **Năm:** 2025
- **Nguồn:** SIGCSE TS 2025, ACM
- **Từ khóa chính:** AI-assisted grading, source code evaluation, rubric, programming assignments, human grader
- **Vai trò trong nghiên cứu của nhóm:** **Core paper cho human-in-the-loop workflow**

---

## 2. Lý do chọn bài báo này

TA Buddy là một trong những bài phù hợp nhất với hướng nghiên cứu của nhóm vì nó đưa ra một workflow rất gần với mục tiêu của nhóm:

```text
problem statement
+ student code
+ grading rubric
→ AI suggested grades/ratings theo từng criterion
→ human grader accept hoặc overrule
→ final grade
```

Trong dự án của nhóm, workflow tương ứng là:

```text
problem statement
+ GitHub source code / commit diff
+ dynamic rubric
→ AI suggested score + evidence + feedback theo criterion
→ judge accept/override
→ final score/ranking
```

Điểm quan trọng là TA Buddy không xem AI như người chấm cuối cùng. AI đóng vai trò **trợ lý chấm điểm**, còn người chấm vẫn quyết định điểm cuối. Đây cũng là hướng nhóm nên áp dụng trong SEAL Hackathon.

---

## 3. Vấn đề nghiên cứu của bài báo

Bài báo xuất phát từ vấn đề thực tế trong các lớp lập trình nhập môn có số lượng sinh viên lớn. Chấm bài lập trình bằng test case giúp tự động hóa một phần, nhưng không đủ trong bối cảnh giáo dục.

Lý do:

1. Test case chủ yếu kiểm tra functional correctness.
2. Code có thể fail test vì lỗi nhỏ nhưng vẫn có logic đáng được partial mark.
3. Code có thể pass test nhưng vi phạm yêu cầu trong problem statement.
4. Nhiều tiêu chí cần đọc source code trực tiếp, ví dụ:
   - dùng đúng thuật toán yêu cầu;
   - không viết toàn bộ logic trong `main`;
   - có chia hàm đúng yêu cầu;
   - có xử lý mảng/chuỗi theo constraint;
   - có tuân thủ coding style hoặc structure.
5. Manual source code inspection tốn rất nhiều thời gian.

TA Buddy được thiết kế để giảm tải quá trình này bằng cách tự động gợi ý rating theo rubric.

---

## 4. Workflow của TA Buddy

Workflow của TA Buddy gồm các bước chính:

```text
1. Instructor chuẩn bị problem statement và rubric.
2. Student nộp source code.
3. Hệ thống chạy autograder/testcase nếu có.
4. TA Buddy đọc problem statement + student code + rubric.
5. TA Buddy gợi ý rating cho từng rubric criterion.
6. Gợi ý được hiển thị trên giao diện chấm.
7. Human TA xác nhận hoặc đổi rating.
8. Human TA có thể giữ hoặc chỉnh reasoning/comment.
9. Final grade được ghi nhận sau quyết định của human TA.
```

Điểm rất đáng học là giao diện TA Buddy **pre-populate** rating cho người chấm. Người chấm không bắt đầu từ trang trắng, mà bắt đầu từ một đề xuất có sẵn. Điều này giúp tiết kiệm thời gian, nhưng vẫn giữ quyền kiểm soát cho con người.

---

## 5. Input, Output, Method theo IOM

## 5.1. Input

TA Buddy dùng các input:

```text
- Programming problem statement
- Student source code submission
- Instructor-specified grading rubric
```

Trong dự án của nhóm, các input này được mở rộng thành:

```text
- Problem statement theo track/round
- GitHub source code hoặc commit diff
- Dynamic rubric theo event/round/track
- Optional build/lint/test results
- README/demo/slide nếu có
```

## 5.2. Output

TA Buddy tạo:

```text
- Suggested rating cho từng rubric criterion
- AI-generated reasoning/comment
```

Trong dự án của nhóm, output nên là:

```text
- suggestedScore
- evidence
- feedback
- confidence
- needsHumanReview
- suggestedJudgeQuestions
```

## 5.3. Method

TA Buddy dùng mô hình AI để chọn rating phù hợp nhất cho từng criterion. Nhưng đóng góp mà nhóm nên học không phải là phần mô hình, mà là **workflow hỗ trợ người chấm**:

```text
AI suggests → human verifies → human accepts/overrides → final grade
```

---

## 6. Kết quả thực nghiệm của bài báo

Bài báo so sánh:

```text
Pure Manual Grading
vs
AI-Assisted Grading with TA Buddy
```

Các kết quả quan trọng:

- Thời gian chấm giảm khoảng **24%**.
- Grade agreement giữa AI-assisted grading và pure manual grading đạt khoảng **90%**.
- TA có thể xác nhận hoặc thay đổi gợi ý của AI.
- Các bài fail test vẫn có thể nhận partial marks nếu source code thể hiện logic đúng một phần.

Kết quả này rất hữu ích cho nhóm vì nó chứng minh rằng AI-assisted grading có thể giúp giảm thời gian chấm nhưng vẫn giữ vai trò quyết định của con người.

---

## 7. Điểm mạnh của bài báo

1. Có hệ thống thật, không chỉ là ý tưởng.
2. Có giao diện chấm cho human grader.
3. Có rubric-based grading.
4. Có AI suggestion theo từng criterion.
5. Có cơ chế human accept/overrule.
6. Có đánh giá thời gian chấm.
7. Có so sánh với manual grading.
8. Rất phù hợp với bài toán judge scoring sheet của dự án.

---

## 8. Hạn chế của bài báo

1. Bối cảnh là programming assignment, không phải Hackathon.
2. Submission chủ yếu là cá nhân, không phải team project.
3. Rubric nằm trong bối cảnh khóa học, không có track/round/ranking.
4. Không xử lý GitHub commit diff hoặc repository lifecycle.
5. Không có workflow finalist/ranking/prize.
6. Phần thuyết trình/demo/teamwork không phải trọng tâm.

---

## 9. Ứng dụng vào nghiên cứu khoa học của nhóm

TA Buddy nên được dùng làm nền cho phần **human-in-the-loop AI-assisted judging**.

Áp dụng vào bài của nhóm:

```text
TA Buddy:
problem + code + rubric
→ suggested rating
→ TA accept/overrule

SEAL AI Buddy:
problem + GitHub diff/source + dynamic rubric
→ suggested score + evidence + feedback
→ judge accept/override
→ final score/ranking
```

Đây là cấu trúc quan trọng nhất để nhóm tránh biến AI thành “giám khảo tự động”.

---

## 10. Ứng dụng vào dự án Hackathon

Trong app, chỉ cần áp dụng phần workflow:

```text
1. AI tạo gợi ý điểm theo từng criterion.
2. Judge xem gợi ý trong scoring sheet.
3. Judge có thể accept hoặc override.
4. Nếu override, hệ thống lưu overrideReason.
5. Final score được tính từ điểm judge.
```

Không cần áp dụng toàn bộ kỹ thuật trong bài. Với dự án, phần quan trọng là UI/UX và dữ liệu:

```text
AiReviewCriterion.suggestedScore
AiReviewCriterion.evidence
AiReviewCriterion.feedback
Score.aiSuggestedScore
Score.isOverridden
Score.overrideReason
```

---

## 11. Mapping với DB hiện tại

| TA Buddy | Dự án nhóm |
|---|---|
| Problem statement | `tracks.problemStatement`, `rounds` |
| Student code | `repositories`, `commits`, `commitdiffs`, `submissions` |
| Rubric | `rubrics`, `criterions` |
| AI suggested rating | `aireviewcriterions.suggestedScore` hoặc `score` |
| AI reasoning | `aireviewcriterions.evidence`, `feedback` |
| Human TA | Judge |
| Human final grade | `scores`, `scoresheets` |
| Accept/overrule | `isOverridden`, `overrideReason` |

---

## 12. Đưa vào Related Work như thế nào?

Đoạn có thể dùng:

```text
TA Buddy demonstrates a practical AI-assisted grading workflow in which the system generates suggested ratings for each rubric criterion and human graders can accept or overrule them. This human-in-the-loop design directly inspires our judge-facing workflow, where AI-generated criterion-level scores, evidence, and feedback are displayed in the scoring sheet, while judges remain responsible for the final score.
```

Bản tiếng Việt:

```text
TA Buddy cho thấy một workflow AI-assisted grading thực tế, trong đó hệ thống tạo rating gợi ý cho từng tiêu chí rubric và người chấm có thể xác nhận hoặc thay đổi. Thiết kế human-in-the-loop này trực tiếp truyền cảm hứng cho workflow của nhóm, nơi điểm gợi ý, evidence và feedback của AI được hiển thị trong scoring sheet, còn judge vẫn quyết định điểm cuối.
```

---

## 13. Kết luận lựa chọn

**Quyết định:** Giữ làm **core paper số 2**.

**Mức độ liên quan:** 9.5/10.

**Vai trò:** Nền tảng cho judge accept/override và AI-assisted grading workflow.

**Cách áp dụng:**

```text
AI suggested criterion score
→ Judge review
→ Accept/override
→ Final score/ranking
```

Đây là bài quan trọng nhất để giải thích tại sao module AI trong dự án không thay thế giám khảo mà chỉ hỗ trợ giám khảo.
