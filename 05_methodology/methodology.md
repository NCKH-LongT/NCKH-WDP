# Methodology

This is an applied AI system study. The project does not propose a new model from scratch. It integrates existing LLM/code LLM into a MERN-based hackathon system.

## Steps

1. Collect code submissions or sample repos.
2. Define dynamic rubric in MongoDB.
3. Capture GitHub commit/diff by webhook.
4. Build structured prompt from rubric + code/diff.
5. Generate AI suggested scores.
6. Judge accepts/overrides.
7. Compare AI score/ranking with human score/ranking.
