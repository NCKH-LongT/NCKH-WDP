# System Architecture

```text
React Admin Web
React Native Mobile App
        |
        v
Node.js / Express Backend
        |
        |-- MongoDB
        |-- GitHub Service
        |     |-- createRepository()
        |     |-- addCollaborator()
        |     |-- removeCollaborator()
        |     |-- handleWebhook()
        |     |-- getCommitDiff()
        |
        |-- AI Evaluation Service
              |-- buildPrompt()
              |-- callLLM()
              |-- parseJSON()
              |-- saveAIReview()
```

Tất cả trigger/webhook được xử lý trong Express backend.
