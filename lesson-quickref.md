# Lesson Protocol — Quick Reference

> Full specification: `learning-content.prompt.md`

---

## Trigger Phrase

> "Teach Chapter X → Topic Y using our Deep Foundation Protocol."

---

## Lesson Flow

```
GATE 1 (Content Audit)
    │
    └─ Verdict: ✅ Sufficient | ❌ Insufficient → expand first
            │
            ▼
    1.  Prerequisites
    2.  Big picture
    3.  Intuition
    4.  Precise technical explanation
    5.  Concrete examples
    6.  Memory / system visualization (ASCII)
    7.  Machine-level explanation
    8.  Failure laboratory
    9.  Debugging & observation
    10. C design & history
    11. Rust connection
    12. Common misconceptions
            │
            ▼
    EXERCISES (Levels 1–7)
    MINI PROJECT (when appropriate)
            │
            ▼
GATE 2 (Mastery Validation)
    │
    ├─ WEAK  → Targeted review → Retest
    └─ READY → Next topic
```

---

## Exercise Levels

| # | Type | Goal |
|---|---|---|
| 1 | Recognition | What is this? |
| 2 | Prediction | What will it do? |
| 3 | Explanation | Why does it do that? |
| 4 | Debugging | Find the bug |
| 5 | Modification | Change it to achieve X |
| 6 | Construction | Build X from scratch |
| 7 | Systems reasoning | What happens underneath? |

---

## Gate 2 Mastery Dimensions

`Recall` · `Mental model` · `Application` · `Prediction` · `Debugging` · `Reasoning` · `Transfer` · `Machine understanding`

---

## Topic Closing Checklist

- What I should now understand
- What I should be able to do
- What I must NOT skip before moving forward
- The next logical topic

---

## Chapter → Milestone

```
All chapter topics done
    │
Chapter Mastery Test (combined)
    │
✅ LOCKED → next chapter

Every 3–5 chapters
    │
Milestone Exam (unfamiliar program)
    Explain → Predict → Draw memory → Debug → Assembly → Behavior
```
