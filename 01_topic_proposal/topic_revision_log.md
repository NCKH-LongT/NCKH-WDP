# Topic Revision Log

| Version | Change | Reason |
|---|---|---|
| v1 | Hệ thống quản lý Hackathon có AI chấm source code | Ý tưởng ban đầu còn rộng, dễ hiểu là xây model AI mới |
| v2 | AI-assisted source code grading based on rubric | Tập trung hơn vào AI chấm điểm theo rubric |
| v3 | IOM-based AI-assisted workflow for SEAL Hackathon | Cập nhật theo feedback giảng viên: không fine-tune, học workflow IOM từ bài báo |

## Current Final Direction

Nghiên cứu cách tích hợp LLM hiện có vào workflow chấm source code theo rubric động trong hệ thống SEAL Hackathon, dựa trên Input–Output–Method, có human judge accept/override và evaluation bằng score/ranking alignment.
