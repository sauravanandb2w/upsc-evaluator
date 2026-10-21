# Full JSON backup & restore (recommended)

User guide (setup + backup routine): **[HOW_TO_USE.md](./HOW_TO_USE.md)** §2.

Use this instead of GitHub Gist when you want **no token**, **no gist size limit**, and a file you control in **iCloud Drive / Google Drive / OneDrive / USB**.

Live app: [upsc-evaluator](https://sauravanandb2w.github.io/upsc-evaluator/)

---

## What’s in the file

One JSON file (`upsc-evaluator-backup-YYYY-MM-DD.json`) with:

- Mains evaluation history (last 500 entries kept in the app)
- Prelims tests, tricks, blogs, suggestions, tags, deleted list, draft (if any)
- Articulation practice log
- Tombstone timestamps for deleted mains entries

Legacy files that are **only a JSON array** still import as **mains-only** (old exports).

---

## Laptop A — export

1. Open the evaluator → **Settings** (gear).
2. Under **Full backup — JSON file**, click **Export full backup**.
3. Save the downloaded file to cloud (e.g. iCloud Drive → `UPSC/upsc-evaluator-backup.json`).

You can also use **History** → **Export full backup** (same file).

---

## Laptop B — import

1. Download the **same** JSON from cloud to the new machine.
2. Open the evaluator → **Settings** → **Import full backup** (or History → **Import backup**).
3. Choose the file → confirm **Merge**.
4. Check **History** and **Prelims** tabs.

Import **adds** new items; it does not delete what is already on this browser. Duplicates are skipped (mains by `ts`, prelims tests by `id`).

---

## Routine

| When | Action |
|------|--------|
| After a study session on A | **Export full backup** → overwrite or date the file in cloud |
| Before using B | **Import full backup** from latest cloud file |
| Both machines active | Pick one “source of truth” file; always **import latest** before working on the other device, then export when done — avoids two divergent copies |

---

## Limits (honest)

| Limit | Detail |
|-------|--------|
| **JSON file size** | No GitHub gist cap; very large files are fine on disk. |
| **Browser `localStorage`** | Still ~5–10 MB per origin; app keeps at most **500** mains evals and **500** practice log rows. |
| **API keys** | Not included in backup (re-enter Groq etc. in Settings on each device). |
| **Two-way sync** | Not automatic — you move the file manually or via cloud sync of the file itself. |

---

## Gist backup

Optional. See [GIST_BACKUP.md](./GIST_BACKUP.md). Prefer JSON if you hit gist errors or do not want a GitHub token.
