# 03 — The LLM Stack

## 📖 Concept

An LLM isn't "smart" on its own. Its quality depends on three training layers:

```
Foundation Model
      ↓
Instruction Tuning
      ↓
Fine-tuning & Alignment
```

| Layer | What it does | Analogy |
|-------|-------------|---------|
| **Foundation Model** | Broad knowledge of language/world | A fresh college graduate — knows a lot, but unfocused |
| **Instruction Tuning** | Trained to follow task-specific commands | Onboarding at a new job |
| **Fine-tuning & Alignment** | Specialization + guardrails (reduce errors/hallucinations) | Certified expert with code of conduct |

---

## 🏥 Domain Example — Medical Chatbot

**Scenario:** A hospital wants an AI assistant to answer patient FAQs.

**Foundation Model only:**
- Can discuss medicine broadly
- Might suggest unverified treatments
- No guardrails → dangerous

**After Instruction Tuning:**
- Understands "answer patient questions about appointments, symptoms, medications"
- Follows a Q&A format

**After Fine-tuning & Alignment:**
- Only answers within approved hospital guidelines
- Refuses to diagnose: *"Please consult your doctor for diagnosis."*
- Trained on the hospital's actual policy documents

**Result:** A safe, reliable assistant — not a hallucinating chatbot.

---

## ✅ TIL

> When an AI gives vague or wrong answers, the problem is usually in the stack — not enough instruction tuning or alignment for your specific domain.
