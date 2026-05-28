# Paper 18 - Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena

## 1. Citation information

- **Title:** Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena
- **Authors:** Lianmin Zheng et al.
- **Year:** 2023
- **Venue:** NeurIPS / arXiv
- **Status in our research:** Optional supporting paper

---

## 2. Why this paper is relevant but not core

This paper is well-known in LLM evaluation. It studies whether strong LLMs can act as judges for open-ended chatbot responses and how well they agree with human preferences.

It is useful because it introduces LLM-as-a-judge techniques such as:

```text
- pairwise comparison
- single-answer grading
- reference-guided grading
```

It also discusses important limitations such as:

```text
- position bias
- verbosity bias
- self-enhancement bias
- limited reasoning ability
```

However, it is not about source code grading, programming assignments, rubrics, or Hackathon workflows. Therefore, it should not be one of the core papers.

---

## 3. Useful ideas for our research

### 3.1. Single-answer grading

This is close to our AI scoring task:

```text
one submission + rubric → suggested criterion score
```

### 3.2. Pairwise comparison

This can inspire future ranking support:

```text
Team A submission vs Team B submission → which is stronger?
```

However, our current research should use rubric-based scoring first because judges need transparent criterion-level scores.

### 3.3. Bias awareness

The paper warns that LLM judges can be biased. This supports our decision to keep human judges in control.

---

## 4. Application to our project

| Paper concept | Possible use in our research |
|---|---|
| LLM-as-a-judge | General background for AI-assisted evaluation |
| Pairwise comparison | Future work for ranking support |
| Single-answer grading | Similar to scoring one submission |
| Bias analysis | Discussion and limitations |
| Human agreement | Justification for comparing AI with judge scores |

---

## 5. How to use in the paper

Use this paper only briefly in the **Related Work** or **Discussion** section.

Example:

```text
General LLM-as-a-judge studies show that LLMs can approximate human preference in some open-ended evaluation settings, but they also reveal biases and reliability concerns. For this reason, our workflow does not use AI as the final judge; instead, AI produces evidence-based suggestions for human judges.
```

---

## 6. Final decision

**Keep as optional supporting reference.**

It is useful for discussing LLM-as-a-judge, bias, and ranking ideas, but it should not distract from the main source-code/rubric focus.
