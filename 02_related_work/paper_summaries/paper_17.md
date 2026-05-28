# Paper 17 - A Survey on LLM-as-a-Judge

## 1. Citation information

- **Title:** A Survey on LLM-as-a-Judge
- **Type:** Survey / methodology paper
- **Status in our research:** Method-supporting paper

---

## 2. Why this paper is useful

This paper is useful because our AI module can be interpreted as a limited form of **LLM-as-a-judge**. However, our system does not allow the LLM to make the final decision. The LLM only provides suggestions for human judges.

The survey helps us explain:

```text
- what LLM-as-a-judge means
- why reliability matters
- what types of bias may appear
- why human review is needed
- how to evaluate agreement with human judgment
```

---

## 3. Relevance to our project

Our workflow is not a fully automated judge. It is:

```text
LLM-as-an-assistant-for-judges
```

The LLM evaluates source code evidence and generates:

```text
- suggested score
- evidence
- feedback
- confidence
- judge questions
```

Then human judges confirm or override the suggestions.

This matches the safer interpretation of LLM-as-a-judge: the LLM helps scale evaluation, but does not replace human authority.

---

## 4. Concepts to borrow

| Survey concept | Use in our paper |
|---|---|
| Human alignment | Compare AI suggested score with judge score |
| Bias | Mention risk of over/under-scoring certain styles |
| Robustness | Future work: prompt variation and repeated review |
| Consistency | Future work: agreement tests |
| Explainability | Require evidence and feedback in AI output |
| Reliability | Use human accept/override and `needsHumanReview` flag |

---

## 5. How to use this paper in the scientific report

This paper should appear in:

```text
Related Work → LLM-as-a-judge and reliability
Discussion → limitations and risks
Evaluation Metrics → agreement, bias, robustness
```

Example claim:

```text
LLM-as-a-judge methods can scale evaluation but require careful reliability checks, bias analysis, and alignment with human judgment. Therefore, our workflow uses LLM output only as advisory evidence for judges.
```

---

## 6. Limitations for our topic

This paper is general. It is not specific to source code grading or Hackathon management. Therefore, it should not dominate the main narrative.

It should support the methodology and discussion, while the main technical direction should still come from:

```text
Rubric Is All You Need
TA Buddy
StepGrade
JorGPT
CodEv
```

---

## 7. Final decision

**Keep as supporting reference.**

Use it for:

```text
- reliability
- bias
- human alignment
- LLM-as-a-judge framing
- justification for judge accept/override
```
