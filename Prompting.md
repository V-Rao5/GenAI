# 02 — Prompting with the ROCCO Framework

## 📖 Concept

Most people prompt AI like this:
❌ "Write me something about leave policy."

The ROCCO framework structures prompts into 5 parts:

| Letter | Stands for | Purpose |
|--------|-----------|---------|
| **R** | Role | Who should the AI act as? |
| **O** | Objective | What exactly do you want? |
| **C** | Context | Background info the AI needs |
| **C** | Constraints | Rules, limits, tone |
| **O** | Output Format | How the answer should look |

**Result:** Faster answers, fewer retries, less token waste.

---

## 🏢 Domain Example — HR Job Description Generator

**Scenario:** An HR manager needs to write job postings quickly.

**Without ROCCO:**
```
Write a job description for a data analyst.
```
→ Generic, needs heavy editing.

**With ROCCO:**
```
Role: You are a senior HR specialist at a fintech startup.
Objective: Write a job posting for a mid-level Data Analyst.
Context: Our team uses Python, SQL, and Tableau. We are a remote-first company of 80 people.
Constraints: Keep it under 300 words. Use an enthusiastic but professional tone. No jargon.
Output Format: Use these sections — About the Role | What You'll Do | What We Need | Perks.
```
→ Ready-to-post output in one shot.

---

## ✅ TIL

> Treat your prompt like a work brief, not a casual question. The more structured your input, the less cleanup your output needs.
