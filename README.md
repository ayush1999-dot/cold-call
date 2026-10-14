# Cold Call

Spin a question from what you just studied. Think, then answer it **out loud** against the clock.
Built to revise topics and practise explaining them clearly for interviews.

## How it works

1. **Study** a chapter, PDF, YouTube video, or have a learning chat with an AI.
2. **Generate a pack:** paste the prompt from [`PROMPT.md`](PROMPT.md) into that same chat.
   It returns a JSON file of 15–25 speaking questions with key points.
3. **Practise:** open the app, add the pack, press **Spin**.

| Mode | Flow |
|---|---|
| ⚡ Quick fire | 15 s to think → 1 min to talk. Trains thinking on your feet. |
| 🔍 Deep dive | 5 min to research and plan → 2 min to explain properly. |

After each answer you get:
- the **key points** to tick off (did you cover them?)
- an interviewer-style **follow-up** question
- optional **recording** to play back, and a **live transcript** with filler-word count and words per minute (Chrome/Edge)
- a self-grade: **Nailed / Shaky / Missed**. Turn on **🎯 Weak spots** and missed or new questions come up more often.

Filter by topic and difficulty. Mix all packs together for a full revision session.
Progress is saved in your browser only.

Keyboard: `Space` next step · `S` spin · `1` `2` `3` grade.

## Adding packs

Three ways:

- **In the app:** Packs → paste the JSON or choose the file. Saved in that browser.
- **In the repo (shows up on every device):** put the file in `packs/` and add its name to `packs/index.json`:
  ```json
  { "packs": ["sample-sql-basics.json", "sql-book-ch2.json"] }
  ```
- **By link:** `https://<you>.github.io/coldcall/?pack=packs/sql-book-ch2.json` (or any raw JSON URL).

Pack format: see the schema in `PROMPT.md` and the example in `packs/sample-sql-basics.json`.

## Run it

- **Locally:** open `index.html` in a browser. Works offline with your imported packs.
  (Packs in `packs/` only load when served, e.g. `python3 -m http.server`.)
- **On GitHub Pages:**
  ```bash
  git init && git add . && git commit -m "Cold Call: first version"
  git branch -M main
  git remote add origin https://github.com/<you>/coldcall.git
  git push -u origin main
  ```
  Then on GitHub: **Settings → Pages → Deploy from a branch → `main` / root**.
  Your app lives at `https://<you>.github.io/coldcall/`.

## Files

```
index.html                  the whole app (no build, no dependencies)
PROMPT.md                   prompt that turns any source into a pack
packs/index.json            list of packs the app loads automatically
packs/sample-sql-basics.json  example pack
```

`index.html` also contains a copy of the sample pack and the prompt so it works as a single file.
If you edit `PROMPT.md`, update the copy inside `<script id="prompt-template">` too.
