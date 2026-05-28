# Paper 15 — Rubric Is All You Need: Improving LLM-based Code Evaluation With Question-Specific Rubrics

## 1. Thông tin bài báo

- **Tên bài báo:** *Rubric Is All You Need: Improving LLM-based Code Evaluation With Question-Specific Rubrics*
- **Tác giả:** Aditya Pathak, Rachit Gandhi, Vaibhav Uttam, Arnav Ramamoorthy, Pratyush Ghosh, và cộng sự
- **Năm:** 2025
- **Nguồn:** arXiv, lĩnh vực Software Engineering / Computing Education
- **Từ khóa chính:** LLM-based code evaluation, question-specific rubric, code assessment, grading, feedback, rubric-based evaluation
- **Vai trò trong nghiên cứu của nhóm:** **Core paper quan trọng nhất cho hướng dynamic rubric / rubric theo đề bài**

---

## 2. Lý do chọn bài báo này

Bài báo này rất phù hợp với đề tài của nhóm vì trọng tâm của nhóm là:

```text
source code / GitHub diff
+ problem statement
+ dynamic rubric
→ AI suggested score theo từng criterion
→ evidence + feedback
→ judge accept/override
→ final score/ranking
```

Trong khi nhiều nghiên cứu trước dùng rubric chung cho mọi bài, bài này nhấn mạnh rằng khi đánh giá code bằng LLM, **rubric cần bám sát từng đề bài cụ thể**. Đây là điểm trùng trực tiếp với bối cảnh SEAL Hackathon, vì mỗi mùa thi, mỗi track, mỗi round có thể có chủ đề và tiêu chí khác nhau.

Ví dụ:

- Fall 2025 có thể tập trung vào AI Agents trong SDLC.
- Spring 2026 có thể tập trung vào Domain-Specific AI RAG.
- Vòng sơ loại và vòng chung kết có tiêu chí khác nhau.
- Track A/B/C có thể có đề bài hoặc yêu cầu khác nhau.

Vì vậy, hệ thống không nên dùng một rubric chung cho mọi bài nộp. Thay vào đó, hệ thống cần hỗ trợ **dynamic rubric** theo event, round và track.

---

## 3. Vấn đề nghiên cứu của bài báo

Bài báo đặt vấn đề rằng LLM đã được dùng nhiều trong lập trình, đặc biệt là code generation và feedback generation, nhưng **code evaluation / code grading bằng LLM vẫn chưa được khai thác đủ sâu**.

Các hệ thống chấm code truyền thống thường dựa vào:

1. Test case.
2. So khớp output.
3. Similarity với reference solution.
4. Static analysis.
5. Rubric chung như correctness, syntax, style.

Tuy nhiên, các cách này có hạn chế:

- Test case chỉ kiểm tra được một phần functional correctness.
- Code không compile có thể bị đánh rớt hoàn toàn dù vẫn có logic đúng một phần.
- Generic rubric dễ bỏ qua yêu cầu logic riêng của từng đề.
- Similarity-based methods không phù hợp khi có nhiều cách giải hợp lệ.
- Feedback có thể không gắn trực tiếp với yêu cầu của đề bài.

Bài báo lập luận rằng **question-specific rubric** giúp LLM đánh giá code tốt hơn vì nó đưa các yêu cầu logic riêng của bài toán vào quá trình chấm.

---

## 4. Khái niệm quan trọng: Question-Agnostic Rubric và Question-Specific Rubric

Bài báo phân biệt hai loại rubric:

## 4.1. Question-Agnostic Rubric

Đây là rubric chung, không phụ thuộc vào đề bài cụ thể.

Ví dụ:

```text
- Code correctness
- Code readability
- Code style
- Efficiency
- Syntax
```

Ưu điểm:

- Dễ tái sử dụng.
- Có thể áp dụng cho nhiều bài khác nhau.
- Dễ thiết kế ở mức tổng quát.

Nhược điểm:

- Không kiểm tra được yêu cầu đặc thù của từng bài.
- Có thể bỏ qua constraint quan trọng trong problem statement.
- Feedback dễ chung chung.
- Không phản ánh đầy đủ mục tiêu giảng viên/ban giám khảo muốn kiểm tra.

## 4.2. Question-Specific Rubric

Đây là rubric được thiết kế riêng cho từng bài toán hoặc đề bài cụ thể.

Ví dụ với đề bài yêu cầu “implement sorting using bubble sort”:

```text
- Có dùng bubble sort đúng yêu cầu không?
- Có viết hàm string-compare riêng không?
- Có lưu chuỗi trong 2D array đúng constraint không?
- Có tách logic khỏi main không?
```

Ưu điểm:

- Bám sát problem statement.
- Đánh giá được yêu cầu logic riêng.
- Feedback cụ thể hơn.
- Phù hợp hơn với chấm source code theo rubric.

Nhược điểm:

- Tốn công thiết kế rubric.
- Khó tái sử dụng nguyên xi cho bài khác.
- Nếu rubric viết không rõ, AI cũng dễ đánh giá sai.

## 4.3. Liên hệ với dự án SEAL Hackathon

Trong dự án của nhóm, `rubrics` và `criterions` nên được xem như **question-specific / context-specific rubric**.

Mapping:

| Ý tưởng trong bài báo | Áp dụng vào dự án |
|---|---|
| Question-specific rubric | Rubric động theo event/round/track |
| Rubric criterion | `criterions` |
| AI output theo từng criterion | `aireviewcriterions` |
| Human expert assessment | Judge score trong `scores` |
| Feedback theo criterion | Evidence/feedback trong `aireviewcriterions` |

---

## 5. Ba kỹ thuật chính trong bài báo

Bài báo đề xuất ba hướng kỹ thuật để dùng LLM đánh giá code theo rubric.

---

## 5.1. Complete Rubric Evaluation (CRE)

### Ý tưởng

CRE cho LLM xem toàn bộ rubric cùng lúc rồi đánh giá submission dựa trên toàn bộ rubric.

Input thường gồm:

```text
problem description
+ student code
+ full rubric
+ optional model solution/reference
```

Output:

```text
score / feedback dựa trên toàn bộ rubric
```

### Ưu điểm

- Đơn giản hơn PRE.
- Ít tốn tài nguyên hơn vì gọi LLM ít hơn.
- Phù hợp khi rubric không quá dài.
- Có thể dùng làm baseline cho hệ thống.

### Nhược điểm

- Khi rubric dài, LLM có thể bỏ sót criterion.
- Feedback từng criterion có thể không đủ chi tiết.
- Khó kiểm tra criterion nào AI làm tốt/kém.

### Ứng dụng vào dự án

CRE có thể dùng làm **baseline AI review**:

```text
source/diff + problem + rubric
→ AI trả review tổng thể + criteriaResults
```

Nếu nhóm cần MVP nhanh, có thể bắt đầu với CRE vì dễ triển khai hơn.

---

## 5.2. Pointwise Rubric Evaluation (PRE)

### Ý tưởng

PRE đánh giá từng criterion riêng biệt. Mỗi tiêu chí trong rubric được LLM xem xét độc lập hoặc theo từng mục.

Input:

```text
problem description
+ student code
+ one rubric criterion
```

Output:

```text
suggested score + evidence + feedback cho criterion đó
```

### Ưu điểm

- Rất phù hợp với đánh giá theo rubric.
- Feedback chi tiết hơn.
- Dễ lưu kết quả theo từng tiêu chí.
- Dễ so sánh AI score với Judge score theo từng criterion.
- Phù hợp với human-in-the-loop vì judge có thể override từng tiêu chí.

### Nhược điểm

- Tốn tài nguyên hơn CRE vì cần nhiều lần đánh giá hoặc prompt dài hơn.
- Nếu các tiêu chí có liên quan với nhau, đánh giá độc lập có thể thiếu context.
- Cần thiết kế prompt và output format cẩn thận.

### Ứng dụng vào dự án

PRE là kỹ thuật phù hợp nhất với thiết kế DB hiện tại của nhóm.

DB mapping:

```text
rubrics
  └── criterions
        └── aireviewcriterions
              └── scores
```

Flow:

```text
For each criterion in rubric:
    AI reads source/diff + problem + criterion
    AI returns suggestedScore, evidence, feedback, confidence
    Save to AiReviewCriterion
Judge opens ScoreSheet:
    sees AI suggestion per criterion
    accept/override
```

Đây chính là hướng nên áp dụng vào bài báo khoa học của nhóm.

---

## 5.3. Ensembling Method Evaluation (EME)

### Ý tưởng

EME dùng nhiều kết quả đánh giá rồi tổng hợp lại để tăng tính ổn định.

Có thể hiểu đơn giản:

```text
LLM run 1 → score A
LLM run 2 → score B
LLM run 3 → score C
→ majority vote / aggregation
→ final suggested score
```

Hoặc:

```text
nhiều model / nhiều prompt / nhiều lần chạy
→ tổng hợp kết quả
```

### Ưu điểm

- Tăng độ ổn định.
- Giảm ảnh hưởng của một lần AI trả lời sai.
- Phù hợp khi cần độ tin cậy cao.

### Nhược điểm

- Tốn chi phí hơn.
- Tăng latency.
- Phức tạp hơn cho MVP.
- Cần cơ chế tổng hợp/voting rõ ràng.

### Ứng dụng vào dự án

Không cần áp dụng ngay trong app. Có thể đưa vào **future work**.

Trong báo cáo khoa học, nhóm có thể viết:

```text
The current prototype uses a single structured rubric-based review. Ensemble-based evaluation can be explored in future work to improve scoring stability for high-stakes judging scenarios.
```

---

## 6. Dataset và cách đánh giá trong bài báo

Bài báo xây dựng dataset gồm:

- OOP submissions.
- DSA submissions.
- Problem descriptions.
- Student code.
- Model/reference solutions.
- Rubrics.
- Feedback / expert assessment.

Bài dùng các metric như:

- Spearman correlation.
- Cohen’s Kappa.
- ICC.
- Leniency.

Điểm đáng chú ý là bài không chỉ đo AI đúng/sai, mà còn đo:

```text
AI nghiêm hơn hay dễ hơn expert?
AI ranking có cùng xu hướng với expert không?
AI feedback có bám rubric không?
```

---

## 7. Metric Leniency

Một đóng góp hay của bài là metric **Leniency**.

Leniency dùng để đo hệ thống AI có xu hướng:

```text
chấm dễ hơn human expert
hay
chấm nghiêm hơn human expert
```

### Vì sao metric này hữu ích với dự án?

Trong cuộc thi lập trình, AI có thể:

- quá nghiêm khi thấy build/test fail;
- quá dễ khi code trông có vẻ tốt nhưng demo thực tế yếu;
- quá ưu tiên code style;
- đánh giá chưa đúng các tiêu chí presentation/teamwork.

Vì vậy, nếu nhóm có thời gian thực nghiệm, có thể thêm phân tích:

```text
AI strictness / AI leniency compared with judge
```

Tuy nhiên, metric này không bắt buộc cho MVP. Có thể đưa vào phần mở rộng.

---

## 8. Kết quả chính của bài báo

Bài báo cho thấy rubric bám sát đề bài giúp cải thiện chất lượng đánh giá code bằng LLM so với rubric chung.

Các kết quả trong bài cho thấy các phương pháp có rubric thường vượt trội hơn phương pháp không dùng rubric hoặc chỉ dựa vào metric code similarity. Đặc biệt, với dataset DSA, phương pháp dùng question-specific rubric đạt kết quả tốt hơn rõ rệt so với question-agnostic rubric trong nhiều chỉ số tương quan.

Kết luận quan trọng với nhóm:

```text
Nếu muốn AI đánh giá code tốt, không nên chỉ đưa code vào AI và hỏi “chấm giúp tôi”.
Cần đưa problem statement + rubric cụ thể + yêu cầu từng criterion.
```

---

## 9. Điểm mạnh của bài báo

1. Rất sát chủ đề LLM-based code evaluation.
2. Nhấn mạnh vai trò của rubric cụ thể theo bài toán.
3. Có kỹ thuật PRE phù hợp với criterion-level AI review.
4. Có cách đánh giá bằng correlation/ranking/leniency.
5. Có dataset gồm student submissions và rubric.
6. Chỉ ra hạn chế của test-case-based grading.
7. Gợi ý được hướng tích hợp vào hệ thống thực tế.

---

## 10. Hạn chế của bài báo

1. Bối cảnh vẫn là programming assignments, chưa phải Hackathon.
2. Dataset chủ yếu là OOP/DSA, không phải project/team-based submissions.
3. Không xử lý đầy đủ các tiêu chí như demo, presentation, teamwork.
4. PRE có thể tốn tài nguyên khi rubric dài.
5. Việc thiết kế question-specific rubric vẫn cần chuyên gia.
6. Chưa trực tiếp giải quyết workflow ranking/finalist trong cuộc thi.

---

## 11. Ứng dụng vào nghiên cứu khoa học của nhóm

Bài này nên được dùng làm nền tảng cho luận điểm:

> Để AI đánh giá source code theo rubric trong cuộc thi lập trình, rubric không nên là tiêu chí chung chung mà cần được thiết kế theo problem statement, round và track của cuộc thi.

Áp dụng cụ thể:

```text
SEAL event/track/round
→ dynamic rubric
→ each criterion has aiInstruction
→ AI evaluates criterion-level evidence
→ save to AiReviewCriterion
→ judge accept/override
```

---

## 12. Ứng dụng vào dự án Hackathon

Trong app, không cần triển khai đầy đủ CRE/PRE/EME như bài báo. Chỉ cần áp dụng phần phù hợp:

## Nên áp dụng ngay

```text
- Dynamic rubric theo event/round/track
- AI review theo từng criterion
- Evidence/feedback theo criterion
- Judge accept/override
```

## Có thể để sau

```text
- Ensemble evaluation
- Leniency calibration
- Multi-model voting
- Large dataset evaluation
```

---

## 13. Mapping với DB hiện tại

| Thành phần | Collection đề xuất / hiện có |
|---|---|
| Problem statement | `tracks`, `rounds` |
| Dynamic rubric | `rubrics` |
| Rubric criterion | `criterions` |
| Code evidence | `repositories`, `commits`, `commitdiffs`, `submissions` |
| AI overall review | `aireviews` |
| AI per-criterion review | `aireviewcriterions` |
| Judge score sheet | `scoresheets` |
| Judge score per criterion | `scores` |
| Ranking | `rankings` |

Đặc biệt, `aireviewcriterions` là bảng phản ánh trực tiếp tinh thần PRE của bài báo.

---

## 14. Cách viết vào Related Work

Đoạn có thể dùng:

```text
Pathak et al. argue that LLM-based code evaluation benefits from question-specific rubrics rather than generic rubrics. Their work distinguishes question-agnostic and question-specific rubrics and proposes Complete Rubric Evaluation, Pointwise Rubric Evaluation, and Ensembling Method Evaluation. This is highly relevant to our study because SEAL Hackathon uses dynamic rubrics that vary by event, round, and track. Inspired by their pointwise evaluation strategy, our workflow stores AI-generated evidence, feedback, and suggested scores at the rubric-criterion level.
```

Bản tiếng Việt:

```text
Pathak và cộng sự cho rằng đánh giá source code bằng LLM hiệu quả hơn khi sử dụng rubric được thiết kế riêng cho từng đề bài thay vì rubric chung. Bài báo phân biệt question-agnostic rubric và question-specific rubric, đồng thời đề xuất Complete Rubric Evaluation, Pointwise Rubric Evaluation và Ensembling Method Evaluation. Nghiên cứu này rất phù hợp với đề tài của nhóm vì SEAL Hackathon có rubric động theo mùa thi, vòng thi và track. Dựa trên ý tưởng pointwise evaluation, workflow của nhóm lưu kết quả AI theo từng tiêu chí rubric, bao gồm điểm gợi ý, evidence và feedback.
```

---

## 15. Kết luận lựa chọn

**Quyết định:** Giữ làm **core paper số 1**.

**Mức độ liên quan:** 10/10.

**Vai trò:** Nền tảng chính cho dynamic rubric và criterion-level AI review.

**Cách áp dụng:**

```text
Question-specific rubric
→ Dynamic rubric trong SEAL Hackathon
Pointwise Rubric Evaluation
→ AiReviewCriterion
Leniency / Spearman / Kappa
→ Metrics mở rộng cho đánh giá AI-human alignment
```

Đây là bài nên phân tích kỹ nhất trong phần related work vì nó giúp bài nghiên cứu của nhóm có cơ sở rõ ràng để nói rằng:

> AI-assisted grading không chỉ cần LLM tốt, mà còn cần rubric đúng ngữ cảnh và được cấu trúc theo từng tiêu chí.
