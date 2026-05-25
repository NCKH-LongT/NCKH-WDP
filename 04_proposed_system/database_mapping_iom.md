# Database Mapping for IOM Workflow

## 1. Reused Existing Collections

The current database already contains useful collections for the IOM workflow:

| Existing Collection | Reused For |
|---|---|
| `events` | Competition season/theme |
| `rounds` | Preliminary/final rounds |
| `tracks` | Track/table assignment |
| `teams` | Team state and competition status |
| `participants` | Participant profile and check-in status |
| `eventparticipants` | Event participation and confirmation status |
| `repositories` | GitHub repository metadata |
| `commits` | Commit metadata |
| `submissions` | Final submission snapshot |
| `rubrics` | Rubric definition |
| `criterions` / `criteria` | Rubric criteria |
| `aireviews` | AI review summary |
| `judgeassignments` | Judge scope |
| `scores` | Criterion-level judge score |
| `rankings` | Leaderboard |

## 2. Design Decision: Avoid Duplicate Collections

Because `eventparticipants`, `teams` and `participants` already contain status fields, the MVP does not require separate `teamregistrations`, `memberconfirmations` or `checkins` collections.

Recommended field usage:

| Need | Existing Field Strategy |
|---|---|
| Member confirmation | `eventparticipants.status` |
| Team registration state | `teams.status` |
| Check-in state | `participants.checkinStatus` or equivalent |
| Team check-in completion | derived from participants in the same team |

## 3. Required Additions for IOM

### 3.1. `commitdiffs`

Purpose: store exact code changes used as AI input.

```js
{
  _id,
  commitId,
  repositoryId,
  teamId,
  filePath,
  status: "added | modified | removed",
  patch,
  additions,
  deletions,
  createdAt
}
```

### 3.2. `aireviewcriteria`

Purpose: store AI output per rubric criterion.

```js
{
  _id,
  aiReviewId,
  criterionId,
  suggestedScore,
  maxScore,
  evidence,
  feedback,
  confidence,
  createdAt
}
```

### 3.3. `scoresheets`

Purpose: group one judge's scoring session for one team/submission.

```js
{
  _id,
  eventId,
  roundId,
  trackId,
  teamId,
  submissionId,
  rubricId,
  judgeId,
  status: "draft | submitted | locked",
  totalScore,
  weightedScore,
  submittedAt,
  createdAt,
  updatedAt
}
```

### 3.4. Optional: `githubaccesslogs`

Purpose: audit GitHub add/remove member actions.

```js
{
  _id,
  eventId,
  teamId,
  repositoryId,
  userId,
  githubUsername,
  action: "invite | add | remove | revoke",
  status: "pending | success | failed",
  requestedBy,
  errorMessage,
  createdAt
}
```

## 4. Suggested Updates to Existing Collections

### `criterions` / `criteria`

Add:

```js
{
  aiSupported: Boolean,
  judgeOnly: Boolean,
  aiInstruction: String,
  order: Number
}
```

### `scores`

Add:

```js
{
  scoreSheetId,
  aiSuggestedScore,
  aiReviewCriteriaId,
  isOverridden,
  overrideReason
}
```

### `repositories`

Add:

```js
{
  status: "created | access_pending | access_granted | locked | archived",
  accessGrantedAt,
  accessRevokedAt
}
```

## 5. Minimal Relationship

```text
events
 ├── rounds
 ├── tracks
 ├── teams
 │    ├── participants / eventparticipants
 │    ├── repositories
 │    │    ├── commits
 │    │    │    └── commitdiffs
 │    ├── submissions
 │    │    └── aireviews
 │    │         └── aireviewcriteria
 │    └── rankings
 ├── rubrics
 │    └── criteria
 └── judgeassignments
      └── scoresheets
           └── scores
```
