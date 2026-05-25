# System Architecture

## 1. Architecture Summary

The system follows a MERN-based architecture with React Admin/Judge Web, React Native Mobile App, Node.js/Express backend, MongoDB database, GitHub API/Webhook integration and an external LLM API.

```text
Admin Web / Judge Web / React Native App
        |
        v
Node.js / Express Backend
        |
        |-- MongoDB
        |-- GitHub Integration Service
        |-- AI Evaluation Service
        |-- Scoring & Ranking Service
        |-- Email/Notification Service
        |
        v
External Services: GitHub API, LLM API, Email Provider
```

## 2. Backend Services

| Service | Responsibility |
|---|---|
| Competition Service | Event, round, track, timeline and policy management |
| Registration Service | Team, participant, eventparticipant and confirmation status |
| GitHub Service | Repo creation, collaborator access, webhook handling, commit diff extraction |
| AI Evaluation Service | Build IOM prompt, call LLM, parse JSON, save AIReview and AIReviewCriteria |
| Judge Scoring Service | Create scoring sheet, save official scores, track AI override |
| Ranking Service | Calculate ranking, finalist selection and awards |

## 3. Database Groups

| Group | Collections |
|---|---|
| Competition | events, rounds, tracks, timelineevents, prizes |
| Team & Participant | teams, participants, eventparticipants, teamslots |
| GitHub | repositories, commits, commitdiffs, githubaccesslogs |
| Rubric | rubrics, criteria/criterions |
| AI Review | aireviews, aireviewcriteria, aiprompts |
| Judging | judgeassignments, scoresheets, scores |
| Result | rankings, finalist selection fields/rules |

## 4. Architecture Diagram

See `04_proposed_system/diagrams/architecture.mmd`.
