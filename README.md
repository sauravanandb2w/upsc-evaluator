# UPSC Mains AI Evaluator

Single-file web app that evaluates UPSC Mains answers using Llama 4 (via Groq free API).

Works for **GS-1, GS-2, GS-3, GS-4 (Ethics), and Essay** papers.

## Live Demo

Open `index.html` directly in any browser — no build step, no server.

## Features

- **Three input modes**: type/paste text, upload images (JPG/PNG/WebP) of handwritten copies, or upload a PDF (multi-page auto-converted)
- Llama 4 vision transcribes the handwritten answer and evaluates it in one pass
- Score out of 10 with grade (Outstanding → Poor)
- 6 sub-scores: structure, directive adherence, content depth, multi-dimensionality, substantiation, word limit/presentation
- Examiner's verdict (2-3 sentence summary)
- Specific strengths with reasoning
- Weaknesses with concrete fixes (not generic advice)
- Missing points a topper would have covered
- 3 actionable improvement suggestions
- A 250-word model answer written by the AI for reference
- Word counter with limit-aware highlighting
- Paper-specific evaluation logic (GS-4 ethics ≠ GS-2 polity)

## Setup

1. Get a free Groq API key at [console.groq.com/keys](https://console.groq.com/keys) (no credit card required)
2. Open `index.html` in a browser
3. Paste the key, click Save (stored in browser localStorage only)
4. Pick paper, word limit, model
5. Paste the question and your answer → click Evaluate

## Models supported

- **Llama 4 Scout** (default) — fast, generous free limits
- **Llama 4 Maverick** — larger, more thorough
- **Llama 3.3 70B** — fallback

All free on Groq's free tier (~14,400 requests/day for smaller models).

## Privacy

- API key stays in browser localStorage on your machine
- Question + answer are sent directly to Groq's API from your browser
- No backend, no analytics, no tracking

## Tech stack

- Vanilla HTML/CSS/JS — zero dependencies
- Groq API (OpenAI-compatible) for inference
- JSON-mode output for structured rendering

## Roadmap

- [x] OCR for handwritten answer copies (Llama 4 vision)
- [x] PDF upload (auto-split into page images)
- [ ] RAG with topper answer corpus for richer benchmarking
- [ ] Eval history (Supabase)
- [ ] Daily question of the day
- [ ] Side-by-side compare with model answer
- [ ] Mobile-first PWA build

## License

MIT
