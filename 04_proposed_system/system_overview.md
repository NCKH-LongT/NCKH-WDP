# Proposed System Overview

## 1. System Name

**SEAL Hackathon Management & AI-assisted Evaluation System**

## 2. Technology Stack

| Layer | Technology |
|---|---|
| Admin Web | React |
| Judge Web | React |
| Participant Mobile App | React Native |
| Backend | Node.js / Express |
| Database | MongoDB |
| Source Control Integration | GitHub API / GitHub Webhook |
| AI Service | Existing LLM API through backend service |

The system does not use n8n. All automation is implemented in the MERN backend.

## 3. Main Actors

| Actor | Description |
|---|---|
| Admin / Event Coordinator | Creates competition, tracks, rounds, rubrics, judges, rankings and awards |
| Participant | Registers, confirms participation, checks in, codes and submits through GitHub |
| Judge | Reviews assigned teams, views AI suggestions, enters official scores |
| Mentor | Reviews assigned teams and can monitor source code progress |
| Speaker | Supports workshop activities |

## 4. Main System Modules

| Module | Purpose |
|---|---|
| Competition Management | Manage seasons, themes, tracks, rounds, timeline and policies |
| Registration Management | Manage teams, participants and confirmation statuses |
| GitHub Integration | Create repo, manage access, receive webhook, store commits/diffs |
| Dynamic Rubric Management | Configure rubric by event, round and track |
| AI Evaluation | Evaluate source code/diff using IOM workflow |
| Judge Scoring | Judge accepts/overrides AI suggestion and submits official score |
| Ranking & Awards | Calculate preliminary/final ranking and manage prizes |
| Audit & Config | Store logs, API keys and system settings |

## 5. IOM-based AI Evaluation Role

The AI module acts as a review assistant, not an automatic judge.

```text
Input: source code/diff + problem statement + dynamic rubric + repository evidence
Method: structured LLM prompting + human-in-the-loop review
Output: suggested scores + evidence + feedback + confidence + risk warnings
```

## 6. Expected MVP

The MVP should include:

1. Dynamic rubric configuration.
2. GitHub commit/diff extraction.
3. AI evaluation API.
4. AI result per rubric criterion.
5. Judge scoring sheet with AI suggestion and override.
6. Ranking generation.
