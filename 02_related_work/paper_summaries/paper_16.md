# Paper 16 - The Future of Grading Programming Assignments in Education

## 1. Citation information

- **Title:** The Future of Grading Programming Assignments in Education: The Role of ChatGPT in Automating the Assessment and Feedback Process
- **Author:** Marcin Jukiewicz
- **Year:** 2024
- **Source:** Thinking Skills and Creativity
- **Status in our research:** Supporting paper

---

## 2. Why this paper is useful

This paper provides empirical evidence that a ChatGPT-style LLM can be used to grade programming assignments and generate feedback. It is useful for our research because it supports the assumption that LLMs can help with programming assessment, but also warns that human verification remains necessary.

The paper is not as directly aligned with our Hackathon workflow as TA Buddy or Rubric Is All You Need, but it is valuable for supporting the feasibility of LLM-based grading.

---

## 3. Study design

The study was conducted in a 15-week Python programming course with 67 students. Nine assignments were evaluated by both a teacher and ChatGPT. The AI evaluated tasks repeatedly to check stability and repeatability.

The main comparison is:

```text
teacher grades vs ChatGPT grades
```

This is close to our planned comparison:

```text
judge scores vs AI suggested scores
```

---

## 4. Key findings relevant to our research

The paper reports a strong positive correlation between ChatGPT grades and teacher grades, suggesting that LLM-based grading can align with human evaluation trends.

However, the paper also notes that ChatGPT can grade differently from the teacher and may require teacher intervention. This supports our design decision:

```text
AI should not produce final scores directly.
AI should produce suggestions for human judges.
```

---

## 5. Application to our project

| Idea from the paper | Application in our project |
|---|---|
| ChatGPT can grade programming tasks | Use LLM to generate suggested criterion scores |
| Teacher grades are used as reference | Judge scores are used as reference |
| Repeated AI grading checks stability | Future work: repeated AI review / consistency check |
| AI may need human intervention | Judge accept/override mechanism |
| AI can save time | Measure grading time reduction |

---

## 6. Use in the scientific paper

This paper should be used in the **Related Work** and **Methodology** sections.

It supports the following claim:

```text
Prior empirical studies show that ChatGPT-style systems can support programming assignment grading, but human verification remains important due to possible grading differences and limitations.
```

---

## 7. Limitations for our topic

This paper is not a Hackathon paper. It focuses on classroom programming assignments. It also does not deeply address dynamic rubrics, GitHub evidence, judge scoring sheets, or ranking.

Therefore, it should not be a core workflow paper, but it is strong supporting evidence.

---

## 8. Final decision

**Keep as supporting reference.**

Use it to justify:

```text
- LLMs can support programming grading.
- Human evaluation is still needed.
- AI-human score comparison is a suitable evaluation method.
```
