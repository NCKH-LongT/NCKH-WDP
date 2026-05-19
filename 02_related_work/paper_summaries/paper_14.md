# Paper 14 Summary

### Citation
- **Tên bài:** A LLM-Powered Automatic Grading Framework with Human-Level Guidelines Optimization
- **Tác giả:** Yucheng Chu et al.
- **Năm:** 2024/2025 version
- **Nguồn:** arXiv preprint
- **DOI:** 10.48550/arXiv.2410.02165

### Problem
Bài giải quyết automatic short-answer grading, nơi open-ended responses khó chấm ở quy mô lớn và dễ thiếu nhất quán. Một vấn đề quan trọng là grading guidelines có thể chưa tối ưu cho LLM; nếu đưa guideline của human trực tiếp cho LLM, model có thể hiểu sai hoặc nhạy với prompt.

### Method
Bài đề xuất **GradeOpt**, framework multi-agent gồm Grader, Reflector và Refiner. Grader chấm, Reflector phân tích lỗi, Refiner tối ưu grading guideline. Framework dùng iterative reflection, misconfidence-based selection, iterative optimization và log-probability-based robustness để tăng accuracy/trustworthiness.

### Dataset / Context
Hai ASAG datasets thực tế: một dataset từ high school physical sciences curriculum và một national sample of teachers trả lời câu hỏi để đánh giá content-specific knowledge required for teaching. Không phải source code.

### Evaluation
Đánh giá grading accuracy và alignment với human evaluators; có ablation studies để kiểm tra đóng góp của từng component.

### Results
GradeOpt consistently outperforms representative baselines về grading accuracy và alignment với human evaluators. Bài chứng minh guideline optimization có thể cải thiện đánh giá bằng LLM.

### Limitations
- Không phải programming/source code grading.
- Không có GitHub, contest ranking.
- Phù hợp hơn cho future work về prompt/rubric optimization.

### Relevance to our topic
Mức độ liên quan: **Trung bình**. Không phải core domain paper, nhưng rất hữu ích cho dynamic rubric và prompt optimization.

### Possible improvement for our system
Future work:
- Lưu các trường hợp judge override AI.
- Phân tích lỗi theo criterion.
- Gợi ý chỉnh rubric description/prompt.
- Versioning rubric để cải thiện AI alignment qua từng mùa thi.

---

# Overall Recommendation

## Core papers nên ưu tiên áp dụng trực tiếp
1. TA Buddy / Design and Evaluation of an AI-Assisted Grading Tool
2. AI-based Automated Grading of Source Code
3. JorGPT
4. StepGrade
5. CodEv

## Supporting papers cho reliability/model selection
6. Systematic Comparison of LLMs
7. Hands-on Analysis
8. Comparative Study of LLMs
9. Automated Python Code Submissions

## Supporting/future work papers
10. BeGrading
11. GradeHITL
12. GradeOpt
13. TRACE
14. AL Mrayat et al.

## Minimum application to the project
Nhóm nên áp dụng **TA Buddy + StepGrade** làm MVP:

```text
GitHub webhook → lấy source code/diff → lấy rubric từ MongoDB → AI chấm từng tiêu chí bằng structured prompt → AI trả score/evidence/feedback → judge accept/override → final score → ranking.
```

### Detailed application to dynamic rubric / future work
GradeOpt không chấm source code, nhưng rất hữu ích cho ý tưởng **rubric/prompt optimization**. Trong hệ thống của nhóm, nếu Judge thường xuyên override AI ở một tiêu chí, có thể tiêu chí đó quá mơ hồ hoặc prompt chưa đủ rõ.

#### Future workflow inspired by GradeOpt
```text
AI suggested score
→ Judge override
→ Store disagreement case
→ Analyze common mismatch by criterion
→ Suggest improved rubric description/prompt
→ Save new rubric version
```

#### Why it matters
Dự án có “dynamic rubric”, vì vậy không chỉ cần chấm theo rubric mà còn cần quản lý version và cải tiến rubric qua từng mùa thi. Đây là hướng nghiên cứu mở rộng rất tốt.


---

**Ghi chú cho repo:** File này thuộc thư mục `02_related_work/paper_summaries/` và dùng để phục vụ literature review, gap analysis, methodology và AI integration của dự án.
