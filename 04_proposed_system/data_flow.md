# Data Flow

1. Admin creates competition, boards, timeline and rubrics.
2. Participants register and confirm email.
3. Backend creates GitHub repo for confirmed team.
4. On contest day, all members check in on React Native app.
5. Backend adds team members to GitHub repo.
6. Team pushes code to GitHub.
7. GitHub webhook calls Express backend.
8. Backend extracts commit diff/source snapshot.
9. Backend retrieves dynamic rubric from MongoDB.
10. AI service evaluates code by rubric.
11. AI returns scores, evidence and feedback.
12. Judge reviews AI suggestion in scoring sheet.
13. Judge accepts/overrides scores.
14. System calculates final score and ranking.
15. After final result, backend removes participants from repo.
