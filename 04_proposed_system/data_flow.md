# Data Flow

## 1. End-to-End Hackathon Workflow

```text
Admin creates competition
→ Configure tracks, rounds, timeline and rubrics
→ Participants register and confirm attendance
→ Teams are assigned to tracks/slots
→ GitHub repositories are created
→ Participants check in on contest day
→ Repository access is activated
→ Teams code and push commits
→ GitHub webhook sends push events
→ Backend extracts commit metadata and diffs
→ AI evaluates source code/diff using IOM workflow
→ Judges review AI suggestions and submit scores
→ System calculates rankings
→ Admin selects finalists
→ Final judges score finalists
→ System publishes results and awards
→ Repository access is revoked
```

## 2. Per-push AI Review Flow

1. A team pushes code to GitHub.
2. GitHub webhook sends a push event to the Express backend.
3. The backend verifies webhook signature.
4. The backend stores commit metadata in `commits`.
5. The backend extracts changed files and saves them in `commitdiffs`.
6. The backend retrieves the current problem statement and rubric.
7. The AI Evaluation Service reviews the diff.
8. The system stores result in `aireviews` and `aireviewcriteria`.
9. Mentors or judges can view risks and feedback during the coding phase.

## 3. Final Aggregate AI Review Flow

1. When coding ends, the final submission is locked.
2. The backend retrieves final repository snapshot, README, demo link, slide link and commit history.
3. The backend retrieves the active rubric for the round.
4. AI evaluates the submission criterion by criterion.
5. AI generates suggested scores, evidence, feedback and judge questions.
6. Judges view AI output in the scoring interface.
7. Judges accept or override AI suggestions.
8. Final scores and rankings are calculated.

## 4. Judge Scoring Flow

```text
Judge logs in
→ System loads assigned teams
→ Judge opens team scoring sheet
→ System displays rubric + AI suggestions
→ Judge accepts or overrides each criterion score
→ Judge submits scoring sheet
→ Ranking service recalculates leaderboard
```

## 5. Data Flow Diagram

See:

- `04_proposed_system/diagrams/iom_workflow.mmd`
- `04_proposed_system/diagrams/ai_evaluation_workflow.mmd`
- `04_proposed_system/diagrams/judge_scoring_workflow.mmd`
