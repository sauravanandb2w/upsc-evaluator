# UPSC Mains AI Evaluator

Single-file web app that evaluates UPSC Mains answers using Llama 4 (via Groq free API).

Works for **GS-1, GS-2, GS-3, GS-4 (Ethics), and Essay** papers. 100% client-side, no backend.

## Live Demo

Open `index.html` directly in any browser. Or visit GitHub Pages: `https://sauravanandb2w.github.io/upsc-evaluator/`

## Features

### Input modes
- Type / paste text answer
- Upload images (JPG / PNG / WebP) of handwritten copies
- Upload a PDF (multi-page auto-converted to images via pdf.js)

### Evaluation engine
- Score out of **10 or 15 marks** (matches word limit) + grade (Outstanding → Poor)
- 6 sub-scores: structure, directive adherence, content depth, multi-dimensionality, substantiation, word limit / presentation
- Examiner's verdict (2-3 sentence honest summary)
- Specific strengths with reasoning
- Weaknesses with concrete fixes (not generic advice)
- Missing points a topper would have covered
- 3 actionable improvement suggestions
- A model answer written by the AI for reference
- Handwriting / paper-aesthetics feedback (vision mode only)

### Five views, six killer features

**🎯 Multi-model consensus** — run the same answer through Llama 4 Scout + GPT-OSS 120B + Qwen 3.6 27B in parallel. Returns 3 scores + average + confidence band. When models disagree, the answer is borderline — flagged for human review.

**📍 Line-by-line highlight** — your answer rendered with green / red / yellow backgrounds showing which sentences are strong, weak, or missing context. Hover for the examiner's note.

**🎯 Self-score calibration** — predict your own score before evaluating. App shows the gap between your self-assessment and the AI's — trains you to think like an examiner over time.

**🎯 Directive auto-check** — extracts the directive word (examine / critically analyze / etc.) from the question and surfaces a dedicated verdict on whether the answer honored it. #1 cause of low scores.

**🌅 Daily question** — pulls a deterministic-by-date random PYQ from your [upsc-mains-pyq](https://github.com/sauravanandb2w/upsc-mains-pyq) repo. Same question for the whole day. Streak tracker + heatmap to build the habit.

**📚 PYQ picker** — browse 1000+ past year questions filtered by paper / year / marks / keyword. Click to auto-fill question + paper + word-limit fields.

### Quality-of-life
- **🔄 Compare two attempts** — paste old & new attempts of the same question. AI scores each + headline diff + delta + next steps. See yourself improve in numbers.
- **✨ Rewrite my answer** — AI rewrites your answer preserving your voice, fixes structure, adds missing facts. Learn by diff.
- **📋 Copy-to-Abhyas buttons** — one-click clipboard copy of Score / Comments / Strengths / Weaknesses, mapped 1:1 to the matching fields in [Abhyas](https://github.com/sauravanandb2w/adarsh) (personal practice log).
- **🔗 Shareable eval link** — encode the eval into a URL hash → share with mentor / peer group. Decoded client-side only; no server.
- **💡 Directive template hints** — when you paste a question, the app detects the directive word and shows the ideal answer skeleton inline.
- **🩹 Common-mistakes detector** — once you have 5+ evals, the app surfaces recurring weakness themes across your history.
- **📊 Streak + heatmap** — GitHub-style green-square grid of your eval activity. Stats: current streak, longest streak, total evals, avg score.
- **⏰ Evening reminder** — browser notification at a chosen time (while tab is open).
- **🌙 Dark mode** — toggle in header. Saved per browser.
- **📥 Export / Import history** — download full eval history as JSON; restore on another browser/device by importing the same file. Import merges with existing (de-duplicates by timestamp).

## Setup

1. Get a free Groq API key at [console.groq.com/keys](https://console.groq.com/keys) (no credit card required)
2. Open `index.html` in a browser
3. Settings tab → paste key → Save (stored in browser localStorage only)
4. Pick paper, word limit, model (or Multi-Model Consensus)
5. Paste / type / upload your answer → Evaluate

## Models supported

- **Llama 4 Scout** (default) — fast, generous free limits, vision-capable
- **Llama 4 Maverick** — larger, more thorough, vision-capable
- **Llama 3.3 70B** — fallback, text only
- **🎯 Multi-Model Consensus** — all three in parallel, averaged + confidence band

All free on Groq's free tier (~14,400 requests/day for smaller models).

## Privacy

- API key stays in browser localStorage on your machine
- All evaluations are sent directly to Groq's API from your browser
- All history, settings, and themes stored in browser only
- No backend, no analytics, no tracking

## Tech stack

- Vanilla HTML / CSS / JS — zero dependencies (only pdf.js loaded from CDN for PDF upload)
- Groq API (OpenAI-compatible) for inference
- localStorage for all persistence
- Fetches PYQ data from `https://sauravanandb2w.github.io/upsc-mains-pyq/data/` at runtime

## Roadmap

- [x] OCR for handwritten answer copies (Llama 4 vision)
- [x] PDF upload (auto-split into page images)
- [x] Multi-model consensus
- [x] Self-score calibration
- [x] Directive auto-check
- [x] Line-by-line highlights
- [x] Daily question
- [x] Streak + heatmap
- [x] PYQ picker
- [x] Compare two attempts
- [x] Rewrite my answer
- [x] Shareable links
- [x] Dark mode
- [x] Directive template hints
- [x] Common mistakes detector
- [x] Evening reminder
- [ ] PWA install + offline
- [ ] Voice answer input
- [ ] Topper-copy RAG (legal-licensed corpus only)
- [ ] Cluster mistakes by topic (ML, not word freq)

## License

MIT
