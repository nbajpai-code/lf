# 🔁 Spaced Repetition — The Memory Multiplier

> *"Forgetting is not the enemy of learning — it is the engine."* — Robert Bjork

---

## What It Is

**Spaced Repetition** is a learning system where you review material at **increasing intervals over time**. Instead of re-reading notes every day (massed practice), you revisit a concept just as you're about to forget it — this struggle to recall **strengthens the memory trace**.

The result: **the same information sticks with 5–10× fewer total hours of review**.

---

## The Science: Ebbinghaus Forgetting Curve

Hermann Ebbinghaus (1885) discovered that memory decays **exponentially** unless reinforced:

```
Memory Retention
100% │▄
     │ ▄▄
 80% │    ▄▄▄
 60% │        ▄▄▄▄
 40% │              ▄▄▄▄▄
 20% │                     ▄▄▄▄▄▄▄▄▄▄▄▄
  0% └─────────────────────────────────── Time
     0h  1h  1d  2d  1w  2w  1m  3m  6m
```

**Key insight:** Each successful recall *resets the curve* at a higher baseline — and stretches the forgetting interval. Review just before you forget and the next interval doubles.

---

## How the Algorithm Works

### SM-2 Algorithm (used by Anki)
Each card has:
- **Ease Factor (EF)**: starts at 2.5, adjusted by your rating
- **Interval**: days until next review, grows exponentially on success

```
If recalled correctly:
  New Interval = Old Interval × Ease Factor

If forgotten:
  Reset to Interval = 1 day, reduce Ease Factor
```

**Review ratings:**
- `Again (1)` — Forgot completely → Reset
- `Hard (2)` — Struggled → Short interval
- `Good (3)` — Recalled correctly → Standard growth
- `Easy (4)` — Knew it cold → Large jump

---

## 🛠️ Implementation Guide

### Step 1 — Choose a Tool

| Tool | Best For | Cost |
|---|---|---|
| **Anki** | Deep technical knowledge, medical, languages | Free |
| **RemNote** | Integrated notes + SRS | Free/Paid |
| **Readwise** | Revisiting book highlights | $7.99/mo |
| **Mochi** | Clean UI, markdown support | Free/Paid |
| **SuperMemo** | Algorithm purists | Paid |

### Step 2 — Make Great Cards (Minimum Information Principle)

**The golden rule: One idea per card.**

❌ **Bad card:**
```
Q: What is TCP/IP?
A: TCP/IP is a suite of communication protocols used to interconnect network devices
   on the internet. TCP stands for Transmission Control Protocol and IP stands for
   Internet Protocol. TCP manages the assembly of a message or file into smaller
   packets...
```

✅ **Good card:**
```
Q: TCP ensures data reliability through what mechanism?
A: Acknowledgment (ACK) and retransmission of lost packets.
```

✅ **Cloze deletion:**
```
The {{c1::three-way handshake}} establishes a TCP connection.
```

### Step 3 — Build a Review Habit
- **15–30 minutes per day** beats 4-hour weekend sessions
- Review at the **same time each day** (consistency > volume)
- Never skip a session during the learning phase (intervals break down)

### Step 4 — Organize with Tags and Decks
```
lf/
├── python/
│   ├── data-structures
│   └── algorithms
├── networking/
│   ├── tcp-ip
│   └── dns
└── cloud/
    ├── aws-core
    └── k8s
```

---

## 📋 Card Templates by Type

### Concept Definition
```
Front: What is [CONCEPT]?
Back: [1-sentence definition] + [one concrete example]
```

### Mechanism / How
```
Front: How does [PROCESS] work?
Back: Step 1 → Step 2 → Step 3 (max 3 steps per card, split if more)
```

### Why / Rationale
```
Front: Why does [SYSTEM] use [DESIGN CHOICE]?
Back: Because [reason] — this solves the problem of [problem].
```

### Comparison
```
Front: [A] vs [B] — key difference?
Back: [A] does X when Y; [B] does X when Z.
```

### Code Pattern
```
Front: Python: reverse a list in-place
Back: my_list.reverse()  # O(n) time, O(1) space
      # Note: list[::-1] returns a new list
```

---

## 🗓️ Typical Spaced Repetition Timeline

| Review # | Interval | Retention if No Review |
|---|---|---|
| 1st study | Day 0 | 100% |
| 1st review | Day 1 | ~58% before review |
| 2nd review | Day 3 | ~44% before review |
| 3rd review | Day 7 | ~38% before review |
| 4th review | Day 16 | ~32% before review |
| 5th review | Day 35 | ~26% before review |
| 6th review | Day 70 | Now in long-term memory |

---

## 🤖 AI Prompts for Spaced Repetition

### Generate Anki Cards
```
Generate 10 Anki flashcards for the topic: [TOPIC].
Use the minimum information principle — one idea per card.
Format: Q: [question] / A: [concise answer]
Include at least 3 cloze deletion cards.
```

### Identify What to Review
```
I'm learning [TOPIC]. I reviewed these concepts last week: [LIST].
Based on typical forgetting curves, which concepts should I prioritize reviewing today?
What are the most likely misconceptions I might have developed?
```

### Build a Card Deck
```
Topic: [TOPIC]
Learning goal: [GOAL]
Create a set of 20 flashcards covering the most impactful concepts.
Group them by: Definitions, Mechanisms, Comparisons, Applications.
```

---

## ⚠️ Common Mistakes

| Mistake | Fix |
|---|---|
| Cards are too long | One fact per card |
| Not reviewing daily | Set a non-negotiable 15-min slot |
| Memorizing without understanding | Learn first, card second |
| Making cards from text you don't understand | Use Feynman Technique first |
| Marking "Easy" to skip — card debt builds up | Be honest with your rating |

---

## 🔗 Related Techniques
- → [Active Recall](ACTIVE_RECALL.md) — the mechanism that makes SRS work
- → [Feynman Technique](FEYNMAN_TECHNIQUE.md) — understand before you card
- → [Interleaving](INTERLEAVING.md) — mix decks to prevent pattern matching

---

## 📚 Further Reading
- *Make It Stick* — Brown, Roediger, McDaniel (Chapter on spaced practice)
- *How We Learn* — Benedict Carey
- [Augmenting Long-term Memory](http://augmentingcognition.com/ltm.html) — Michael Nielsen (free essay)
- [SuperMemo Algorithm Explanation](https://supermemo.guru/wiki/Algorithm_SM-2)
