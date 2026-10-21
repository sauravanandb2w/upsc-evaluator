# How to use UPSC Evaluator

Live app: [upsc-evaluator](https://sauravanandb2w.github.io/upsc-evaluator/)

All evaluation history and prelims data stay in **this browser** (`localStorage`). To use the app on another laptop or browser, copy your data with a **JSON backup file** (recommended) or optional GitHub Gist.

---

## 1. First-time setup

1. Open the app (GitHub Pages link above, or `index.html` locally).
2. Click the **gear (Settings)** in the header.
3. Add an API key ( **OpenRouter** is recommended for best mains eval quality; **Groq** or **Gemini** work too) → **Save**.
4. Go to **Mains** → paste or upload your answer → **Evaluate**.

Keys are stored only in this browser. They are **not** included in JSON backup — re-enter them on each device.

---

## 2. Sync data across devices (JSON backup) — recommended

No GitHub token, no ~1 MB gist limit. You keep one file in **iCloud Drive**, **Google Drive**, **OneDrive**, or on a **USB stick**.

### What’s in the backup file

One download: `upsc-evaluator-backup-YYYY-MM-DD.json`

- Mains evaluation history (app keeps the latest **500** entries)
- Prelims tests, tricks, blogs, suggestions, custom tags, deleted list, in-progress draft
- Articulation practice log
- Tombstones for mains entries you deleted (so they don’t come back on import)

Old exports that are **only a JSON array** still import as **mains-only**.

### Laptop A — export

1. **Settings** → **Full backup — JSON file** → **Export full backup**  
   (Same action: **History** → **Export full backup**.)
2. Save the file to cloud, e.g. `UPSC/upsc-evaluator-backup.json` (overwrite or use a dated name).

### Laptop B — import

1. Download the **same** JSON from cloud onto the new machine.
2. Open the app → **Settings** → **Import full backup** (or **History** → **Import backup**).
3. Select the file → confirm **Merge**.
4. Check **History** and **Prelims** tabs.

Import **merges**: it does not wipe this browser. Duplicates are skipped (mains by timestamp, prelims tests by `id`).

### Day-to-day routine

| When | What to do |
|------|------------|
| After studying on laptop A | **Export full backup** → save to your cloud file |
| Before using laptop B | **Import full backup** from the latest cloud file |
| You use both machines often | Treat one cloud file as source of truth: **import latest** before working on the other device, then **export** when you finish |

### Limits (honest)

| Topic | Detail |
|-------|--------|
| JSON file on disk | No gist size cap; large files are fine. |
| Browser storage | Still ~5–10 MB per site; app caps mains history and practice log at **500** rows each. |
| API keys | Not in the backup — set again in Settings on each device. |
| Automatic sync | No — you move the file (or let cloud sync the file itself). |

More detail: [EXPORT_IMPORT.md](./EXPORT_IMPORT.md).

---

## 3. Optional: GitHub Gist backup

If you prefer a token + secret gist instead of a file, see [GIST_BACKUP.md](./GIST_BACKUP.md). JSON backup is simpler for most people.

---

## 4. Mains workflow (quick)

1. Choose paper, marks/word limit, and model on the evaluate form.
2. Paste text, upload images, or upload a PDF.
3. Read score, verdict, strengths/weaknesses, and model answer.
4. Use **History** to reopen past evals; **Compare** / **Rewrite** from there when available.

---

## 5. Prelims workflow (quick)

1. Open the **Prelims** top tab.
2. Enter or import a test, mark answers, add notes/tricks/tags as you go.
3. Include prelims in the **full JSON backup** so they move with mains history.

---

## 6. Privacy

- Evaluations go from your browser to the AI provider you chose (Groq, Gemini, OpenRouter, etc.).
- No app backend; no account required except optional Supabase for **API key sync** in Settings.
- Backup files are yours — store them wherever you trust.

Source code: [upsc-evaluator on GitHub](https://github.com/sauravanandb2w/upsc-evaluator).
