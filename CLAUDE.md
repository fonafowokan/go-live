# GO-LIVE — Claude Code Operating Rules

## 1. Project Intent

Landing page and website for the **Go Live** brand — a static site served via nginx on Railway.

## 2. Architecture

```
/go-live/
  index.html        # Single-page static site
  Dockerfile         # nginx:alpine, serves static files on port 80
  .dockerignore      # Excludes .claude, .vscode, .git, Dockerfile
```

## 3. Deploy

**Stack**: nginx:alpine Docker image on Railway, deployed via GitHub integration.
**Repo**: `fonafowokan/go-live` (private) on GitHub, branch `master`.
**Railway Project**: go-live
**Live URL**: https://exhorter.org
**Railway URL**: https://go-live-production.up.railway.app
**Domain**: `exhorter.org` (Cloudflare DNS → Railway)

- `Dockerfile` copies all files into nginx serve directory
- Auto-deploys on `git push origin master`
- Cloudflare CNAME must be **DNS only** (gray cloud) — Railway handles SSL
- nginx listens on port 80 (do not use `$PORT` template — custom domains route to port 80)
- Sibling repos: `fonafowokan/hlthcr` (healthcare course), `fonafowokan/autoins` (auto insurance course)

### All Sites on exhorter.org

| Domain | Railway Project | Repo |
|--------|-----------------|------|
| `exhorter.org` | go-live | go-live |
| `hlthcr.exhorter.org` | hlthcr | hlthcr |
| `autoins.exhorter.org` | autoins-foundations | autoins |
| `grp-frm.exhorter.org` | grp-frm | grp-frm |

## 4. Conventions

- Never delete files — archive instead
- Commit changes only when explicitly asked
- Use PR workflow — master auto-deploys to Railway
