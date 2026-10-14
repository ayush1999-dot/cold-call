# Cold Call — Pack Generator Prompt

Copy everything below the line into any chat (Claude, ChatGPT, Gemini) **after** you've shared the material:
a chapter you pasted, a PDF you attached, a YouTube transcript, or simply the conversation you just had.

Fill in the two lines in `[brackets]` first.

---

You are creating a **question pack** for my speaking-practice app, Cold Call.
I study a topic, then answer random questions **out loud, against a timer**, to revise and to get better at
explaining things clearly in interviews.

**Material:** use [the chapter / PDF / video transcript / our conversation above — say which].
**My goal:** [e.g. "interview for a Reporting Analyst role; I use Oracle SQL daily as a data tester"].

## What to generate

- **15–25 questions** based on the material. Mostly things the material actually covers.
  You may add up to 4 "stretch" questions that go one step beyond it (common interview follow-ups) —
  put `"stretch": true` on those.
- Every question must be answerable **by speaking for 1–3 minutes**. No "write a query" tasks, no
  multiple choice. Ask for explanations, reasons, comparisons and stories.
- Use a **mix of types** (at least 5 different ones):
  - `concept` — explain what something is
  - `why` — why it works / why it matters
  - `compare` — X vs Y, when to use which
  - `scenario` — "you're at work and this happens, what do you do?"
  - `debug` — "this result looks wrong, what happened?"
  - `trick` — a common misconception or gotcha
  - `eli5` — explain it to a non-technical person
  - `interview` — behavioural or "tell me about a time…" linked to the topic
- `difficulty`: 1 = definition, 2 = understanding, 3 = applying under pressure. Aim for roughly 30 / 45 / 25 %.
- `mode`: `"quick"` if I can answer with no preparation in about a minute, `"deep"` if it deserves a few
  minutes of research or thinking first.
- `points`: 3–5 **short** key points a strong answer covers (under 12 words each). I use them to grade myself
  after speaking, so make them checkable.
- `followup`: one sharper follow-up question an interviewer might ask next.
- `topic`: the section or sub-topic, so I can filter (keep to 3–8 distinct topics per pack).
- Write questions in plain, natural English, the way an interviewer would actually say them.

## Output format

Return **only** one JSON code block, valid JSON, no comments, exactly this shape:

```json
{
  "schema": "coldcall/v1",
  "id": "short-kebab-id-for-this-pack",
  "title": "Readable pack title",
  "source": { "type": "book | pdf | video | chat | article | notes", "name": "Name of the source", "part": "Chapter 1" },
  "created": "YYYY-MM-DD",
  "questions": [
    {
      "id": "c1-01",
      "q": "The question text?",
      "type": "concept",
      "difficulty": 1,
      "topic": "Sub-topic",
      "mode": "quick",
      "points": ["Key point one", "Key point two", "Key point three"],
      "followup": "A sharper follow-up?"
    }
  ]
}
```

If you can create files, also save it as `<id>.json` so I can download it.
Then, in one or two lines after the JSON, tell me which question you think I'll find hardest and why.
