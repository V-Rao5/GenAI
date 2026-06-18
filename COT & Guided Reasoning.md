# 04 — Chain-of-Thought & Guided Reasoning

## 📖 Concept

### 🧠 Chain-of-Thought (CoT)
Instead of jumping to an answer, CoT prompts the AI to **think step by step**.

- **Reduces mistakes** on multi-step problems
- **Validates logic** — you can see *why* it reached an answer
- **Audit-friendly** — separates reasoning from final answer

**Prompt trick:** Add `"Think step by step"` or `"Show your reasoning before answering"`.

---

### 🛠 Guided Reasoning
When you can't leave the reasoning path to the AI, you **define the exact steps yourself**.

- You control the flow
- AI fills in each step, not the whole answer at once
- Best for strict business logic or compliance scenarios

---

## 🏦 Domain Example — Loan Approval Logic

**Scenario:** A bank uses AI to assist loan officers in evaluating applications.

**Without CoT (risky):**
```
Prompt: Should we approve this loan? Income: $45,000, Debt: $18,000, Credit Score: 620.
Answer: Approve. ← No reasoning shown. How? Why?
```

**With Chain-of-Thought:**
```
Prompt: Evaluate this loan application step by step.
Income: $45,000 | Debt: $18,000 | Credit Score: 620

Step 1 — Debt-to-Income Ratio: $18,000 / $45,000 = 40% → Above 36% threshold ⚠️
Step 2 — Credit Score: 620 → Below the 650 minimum ⚠️
Step 3 — Risk Assessment: Two risk flags present.
Final Answer: Do not approve. Recommend credit counseling first.
```
→ Now a loan officer can review and justify the decision to a regulator.

**With Guided Reasoning (strict compliance):**
```
You must follow these steps in order:
1. Calculate DTI ratio. Flag if > 36%.
2. Check credit score. Flag if < 650.
3. Check employment stability (> 2 years?).
4. Only recommend approval if 0 flags.
```
→ AI cannot skip or reorder steps. 100% auditable.

---

## ✅ TIL

> CoT is for accuracy. Guided Reasoning is for compliance. Use CoT when you want the AI to think better. Use Guided Reasoning when you need it to think *your way*.
