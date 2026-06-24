# Your AI Guy — Flagship Site

Standalone HTML page deployed on Railway. Light theme, 15 repos, category filtering.

## Deploy to Railway

```bash
# From this directory:
railway link    # link to your Railway project
railway up      # deploy
```

Or connect this repo to Railway via GitHub — it auto-detects `nixpacks.toml`.

The site is a single `index.html` file served by `npx serve`. No build step needed.

## Domain masking

Until you're ready to point a custom domain at it, the Railway URL works as-is:
`https://your-app-name.up.railway.app`

When ready: Railway → Settings → Networking → Add Custom Domain.

## Repo Safety Report

All 15 repos were scanned for exposed secrets, credentials, and PII.

### ✅ Clean Repos (8 public, verified safe)

| Repo | Status | Notes |
|------|--------|-------|
| super-saiyan-browser | ✅ Clean | Only `.env.example` (template, no real keys) |
| governance | ✅ Clean | Only `.env.example` |
| dial-desk-swarm | ✅ Clean | Only `.env.example` |
| titans-of-direct-response-mastermind-council | ✅ Clean | No env files at all |
| openswarm-builder | ✅ Clean | Only `.env.example` |
| hermes-desktop-os1 | ✅ Clean | Swift credential stores are code templates, not real credentials |

### ⚠️ Attention Needed (1 repo)

| Repo | Issue | Recommendation |
|------|-------|----------------|
| ai-integraterz-cold-email | Contains `data/tasks.db` (98KB SQLite), `data/concierge/journal.jsonl` (Slack message logs with user IDs), and 2 CSV exports with real prospect emails/names/companies in `data/exports/` | **Remove these from the repo or add to `.gitignore` + `git rm --cached`.** The `.gitignore` already excludes these paths but they were committed before the ignore rules were added. Run: `git rm --cached data/tasks.db data/concierge/journal.jsonl data/exports/*.csv` then commit. |

### 🔒 Not Yet Public (7 repos returned 404)

These repos are either private or don't exist yet:

1. super-agent-sales-director
2. experts-gtm-flywheel
3. Titan-Genome-Content-Multiplier
4. sovereign-trades-method
5. genius-tap-content-system
6. jay-abraham-power-partnerships
7. sovereign-audience-method

The site links to all 15 repos — the 7 private ones will show a 404 until made public. The cards still display with descriptions so visitors can see the full catalog.

## Structure

```
ai-guy-site/
├── index.html       # The complete site (HTML + CSS + JS inline)
├── package.json     # Railway serve config
├── nixpacks.toml    # Railway build config
└── README.md        # This file
```

## Customizing

- **Email links:** Search for `hello@youraiguy.com` in `index.html` and replace
- **Repo descriptions:** Edit the `<p>` tags inside each `.repo-card`
- **Colors:** Edit CSS `:root` variables at the top of `index.html`
- **Adding repos:** Copy a `.repo-card` block, set `data-cat` to `biz`, `growth`, or `dev`
