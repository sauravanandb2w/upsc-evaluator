# GitHub Gist backup & restore (optional)

**Prefer JSON file backup** for most users: **[EXPORT_IMPORT.md](./EXPORT_IMPORT.md)** (no token, no gist size limit).

Your evaluation history lives in **this browser only** (`localStorage`). Gist backup copies a snapshot to a **secret gist** on your GitHub account.

**No git commit is required** for your data.

Live app: [upsc-evaluator on GitHub Pages](https://sauravanandb2w.github.io/upsc-evaluator/)

---

## One-time setup (each device)

1. Create a GitHub **personal access token** (classic `ghp_…` is fine) with scopes:
   - **gist**
   - **public_repo**  
   Link: [Create token](https://github.com/settings/tokens/new?scopes=gist,public_repo)

2. Open the evaluator → **Settings** (gear) → **GitHub Gist Backup**.

3. Paste the token → **Save Token**.  
   Stored only in this browser as `upsc_gh_token`.

---

## Laptop A — first backup (creates the gist)

1. Settings → **Backup to Gist**.
2. Wait for the green message → click **View Gist** (optional).
3. Note the **Gist ID** shown in the message (or copy the URL).  
   Example URL: `https://gist.github.com/yourname/`**`a1b2c3d4e5f6…`**

The app also saves that ID locally as `upsc_gist_id`.

---

## Laptop B — restore (or any new browser)

1. Hard-refresh the app once after deploy (`Cmd+Shift+R` / `Ctrl+Shift+R`) so you have the **Gist ID or URL** field.

2. Settings → paste the **same `ghp_` token** → **Save Token**  
   (same GitHub account that owns the gist).

3. In **Gist ID or URL**, paste either:
   - the full gist link from laptop A, or  
   - only the gist ID (hex string).

4. Click **Link Gist** (you should see a green “Linked gist …” message).

5. Click **Restore from Gist** → confirm.  
   Merges remote data into this browser (does not delete local entries).

6. Open **History** (and Prelims sections if you use them) to verify.

---

## Day-to-day sync

| Where you worked | What to do |
|------------------|------------|
| Laptop A (main) | **Backup to Gist** after new evaluations |
| Laptop B | **Restore from Gist** when you want the latest from A |
| Both devices | Use the **same gist ID** on both (Link Gist on B; A updates it automatically after backup) |

Each **Backup** on A **updates** the same gist (PATCH), it does not create a new gist every time unless you cleared `upsc_gist_id` or linked a different ID.

---

## What is backed up

The gist contains JSON files, including:

- Mains evaluation history (`upsc-history.json`)
- Prelims tests and related prelims localStorage keys

Restore **merges** mains by timestamp and prelims tests by id. Some prelims keys are only filled if missing locally.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| “No token saved” | Save token in Settings |
| “Paste gist URL/ID…” | Link Gist before Restore |
| 401 / Bad credentials | Regenerate token; check **gist** scope |
| 404 on gist | Wrong ID or gist deleted; use URL from laptop A |
| Old UI (no gist field) | Hard refresh or wait ~1 min after GitHub Pages deploy |

---

## Alternative: JSON export (recommended)

See **[EXPORT_IMPORT.md](./EXPORT_IMPORT.md)** — full backup from Settings or History.
