# 06 — Memory & Context Window

## 📖 Concept

LLMs have no persistent memory between sessions. All "memory" must be managed explicitly.

### Two Types of Memory

**1. Short-Term Memory = Context Window 🗒**

The model's active workspace — limited in size. Three strategies to manage it:

| Strategy | What it does |
|----------|-------------|
| **Truncation** | Drop oldest messages to fit new ones |
| **Summarization** | Condense past chat into a short paragraph |
| **Sliding Window** | Keep only the last N tokens |

**2. Long-Term Memory = Knowledge Base 🏛**

Permanent knowledge comes from:
- **Weights (Parameters)** — patterns baked in during training
- **External Storage (RAG)** — your PDFs, databases, logs in a vector store

---

### The 8GB "Memory Tetris" 🧩

On a local 8GB system, the context window is shared by 4 things:

```
┌─────────────────────────────┐
│  System Prompt              │ ← Your rules/instructions
│  Retrieved Chunks (RAG)     │ ← Data pulled from your files
│  User Query                 │ ← What you just asked
│  Model's Response           │ ← Answer being generated
└─────────────────────────────┘
        Limited RAM — they compete!
```

If Retrieved Chunks are too large → System Prompt gets pushed out → Model forgets its rules → Hallucinations.

---

## 🎧 Domain Example — Customer Support Agent

**Scenario:** An e-commerce company builds an AI agent that handles multi-turn support conversations.

**The problem:**
A customer chats for 40 messages about a return. By message 35, the AI forgets the order number mentioned at message 2.

**Solution — Summarization strategy:**
```
After every 10 messages:
→ Summarize: "Customer John, Order #4521, wants to return a blue jacket bought Nov 3. 
   Reason: wrong size. Refund approved, waiting on shipping label."
→ Replace 10 messages with this 1 summary in the context window.
```

Now the agent always knows the key facts, no matter how long the conversation runs.

**For long-term memory:**
Store resolved cases in a vector DB → agent can recall: *"This customer had a similar issue in March."*

---

## ✅ TIL

> The context window is not infinite storage — it's a shared whiteboard. Manage it deliberately or your agent will start "forgetting" things mid-conversation.
