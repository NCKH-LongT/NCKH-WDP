# Literature Review Matrix

## Topic

**Hệ thống quản lý và đánh giá giải đấu lập trình tích hợp GitHub Automation và AI hỗ trợ chấm điểm source code theo rubric động.**

| STT | Bài báo | Năm / Nguồn | Lĩnh vực | Vấn đề nghiên cứu | AI / Phương pháp | Rubric / Tiêu chí | Dataset / Context | Metrics / Evaluation | Ranking | Đóng góp | Hạn chế | Relevance | Ứng dụng vào workflow |
|---:|---|---|---|---|---|---|---|---|---|---|---|---|---|
|1|AL Mrayat et al.|2025 / IJAIA|AI code review|Review code thủ công tốn thời gian và thiếu nhất quán.|GPT-4/transformer + Pylint/Flake8/Checkstyle.|Coding standards, chưa phải scoring rubric.|Academic student projects.|Issue detection, time reduction, feedback.|Thấp.|Nền tảng AI code review/static analysis.|Không chấm điểm theo rubric/ranking rõ.|Background.|Preprocessing/static analysis.|
|2|TRACE|2026 / arXiv|CS project assessment|Đánh giá project nhóm và contribution khó công bằng.|Repository mining + GitHub API + AI analytics.|Code quality, test coverage, docs, functionality, usability.|GitHub Classroom/project repos.|Correlation với instructor, time reduction.|Trung bình.|Workflow repo/dashboard tốt.|Preprint, không phải contest.|Supporting.|GitHub extraction/dashboard.|
|3|TA Buddy|2025 / ACM SIGCSE|AI source code grading|Autograder test case không chấm được partial marks/code quality.|Fine-tuned Code Llama; problem + code + rubric -> suggested ratings.|Instructor-specified grading rubric; TA accept/overrule.|6 problems, 740 submissions; 55 criteria.|24% time reduction, 90% grade agreement.|Trung bình cao.|Core workflow sát dự án nhất.|Không đo ranking similarity.|Very high core.|AI prefill score -> judge override -> final ranking.|
|4|JorGPT|2025 / Future Internet|LLM grading|Manual grading tốn thời gian và thiếu nhất quán.|Nhiều LLM, instructor chọn model/rubric.|Correctness, docs, efficiency, readability/style, compliance.|Intro to Programming; 672 students.|Adjusted R²=0.9156, MAE=0.4579, time reduction.|Trung bình.|Rubric design + metrics mạnh.|Không phải contest/ranking.|High core.|Rubric + MAE/correlation/time metrics.|
|5|Systematic Comparison of LLMs|2026 / Computers and Education: AI|Model reliability|LLM architecture/vendor ảnh hưởng điểm chấm.|18 LLM, distribution, variability, ICC.|Không trọng tâm rubric.|6,000+ submissions.|Correlation, clustering, ICC.|Trung bình cao.|Cần model selection/human-in-loop.|Không workflow/rubric contest.|High.|Benchmark model, reliability.|
|6|Hands-on Analysis|2024 / IST|LLM auto evaluation|Đo LLM chấm code ổn định đến đâu.|LLM multi-run evaluation.|Correctness, quality, style/best practices.|Programming assignments.|10 iterations/model, consistency, exact match, ±1 accuracy.|Trung bình.|Không nên chạy AI một lần duy nhất.|Ít rubric/ranking.|High.|AI consistency check.|
|7|CodEv|2025 / arXiv|Automated grading|Cần điểm nhất quán và feedback hữu ích.|CoT + LLM ensemble + agreement tests.|Correctness/readability/functionality.|Programming assignments.|ICC, agreement, feedback quality.|Trung bình cao.|Tăng độ ổn định và feedback.|Preprint, không contest.|High.|Repeat/ensemble -> agreement -> score.|
|8|Comparative Study of LLMs|2025 / Applied Sciences|Model comparison|So sánh accuracy/efficiency/feedback khi chấm code.|GPT-4, Claude, Gemini, structured prompt.|Functionality, structure, documentation, efficiency.|315 Python assignments, 100 analyzed.|Agreement, accuracy, feedback quality.|Trung bình cao.|Workflow data -> rubric -> AI -> comparison.|Không ranking metric chính.|Very high.|Multi-model scoring.|
|9|Automated Python Grading|2025 / Information|Hybrid scoring|Dự đoán điểm Python bằng LLM + ML.|GPT-4-Turbo + ML/PyCaret.|Score 0-100, chưa rõ rubric criterion.|350 Python submissions.|Prediction performance.|Trung bình.|Hybrid LLM+ML calibration.|Python-specific, rubric chưa rõ.|Supporting.|Future hybrid scoring.|
|10|BeGrading|2024/2025 / Springer|LLM feedback/grading|Giảm gánh nặng chấm và tăng feedback.|Fine-tuned/customized LLM, augmented data.|Không trọng tâm predefined rubric.|3,470 samples + 374 book questions.|Difference rate/benchmark.|Thấp-trung bình.|Hướng fine-tune và feedback.|Không sát ranking/rubric động.|Supporting.|Feedback report/future fine-tune.|
|11|StepGrade|2025 / arXiv|CoT code grading|Regular prompting thiếu reasoning và minh bạch.|GPT-4 + CoT step-by-step.|Functionality, code quality, algorithmic efficiency.|30 Python assignments.|CoT vs regular prompting; deviation from human.|Trung bình.|Prompt design mạnh, evidence/feedback.|Preprint, dataset nhỏ.|High.|Structured prompt in Node AI service.|
|12|GradeHITL|2025 / arXiv|Human-in-loop|LLM fully automated khó đạt human-level.|LLM hỏi human experts, refine rubrics.|Rubric-based, dynamic refinement.|Short-answer grading.|Accuracy improvement.|Thấp-trung bình.|Luận cứ cho judge override/rubric refine.|Không code grading.|Method.|Judge override -> improve rubric.|
|13|AI-based Automated Grading of Source Code|2025 / ICPC|Source code rubric grading|Test-case autograding thiếu partial/code-quality criteria.|LLM for code + instructor-specified rubric.|Rất sát: instructor-specified rubrics.|Intro programming assignments.|Need full paper for detailed metrics.|Trung bình cao.|Core evidence LLM+code+rubric.|Có phí/không ranking.|Very high.|AI source code scoring.|
|14|GradeOpt|2024/2025 / arXiv|Guideline optimization|Guidelines mơ hồ làm chấm lệch.|Multi-agent Grader/Reflector/Refiner.|Guidelines gần rubric, short-answer.|Open-ended answers.|Accuracy, human alignment, ablation.|Thấp-trung bình.|Future rubric/prompt optimization.|Không code/hackathon.|Method.|Analyze judge override -> refine prompt/rubric.|

## Priority

1. TA Buddy
2. StepGrade
3. JorGPT
4. CodEv
5. AI-based Automated Grading of Source Code
6. Systematic Comparison of LLMs
