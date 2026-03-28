# GO-LIVE — Handoff Document

**Project**: Go Live Website
**Date**: 2026-03-27

---

## Current State: Placeholder Landing Page

The site is a single static HTML page ("Coming soon") served by nginx in a Docker container on Railway. No dynamic content, no assets beyond the HTML file.

---

## What Exists

### Files
| File | Status | Notes |
|------|--------|-------|
| `index.html` | Done | Dark-themed centered page with "Go Live" heading and "Coming soon" tagline |
| `Dockerfile` | Done | nginx:alpine, copies files to `/usr/share/nginx/html`, exposes port 80 |
| `.dockerignore` | Done | Excludes `.claude`, `.vscode`, `.git`, `.dockerignore`, `Dockerfile` |

### Config
| File | Status | Notes |
|------|--------|-------|
| `.claude/settings.local.json` | Done | Standard permissions (Read, Edit, Write, Glob, Grep, Agent, WebSearch, WebFetch, Bash, filesystem MCP) |
| `.vscode/settings.json` | Done | VS Code theme settings |

---

## What Remains

### Must Do
1. **Define site purpose and content** — currently a placeholder with no real content
2. **Design and build out pages** — based on whatever the site's purpose will be

### Should Do
3. **Add `nginx.conf`** — if needed for caching or routing rules (listen on port 80, do NOT use `$PORT` template)

### Nice to Have
5. **Favicon and meta tags** — SEO basics, Open Graph tags
6. **Mobile responsiveness** — current CSS is minimal but centered

---

## Deploy Status

**Railway Project**: go-live
**Custom Domain**: https://exhorter.org
**Railway URL**: https://go-live-production.up.railway.app
**Deploy**: GitHub integration — auto-deploys on `git push origin master`
**GitHub**: `fonafowokan/go-live` (private), branch `master`
**DNS**: Cloudflare (CNAME, DNS only / gray cloud — Railway handles SSL)

### All Sites on exhorter.org (configured 2026-03-27)

| Domain | Railway Project | Status |
|--------|-----------------|--------|
| `exhorter.org` | go-live | Live |
| `hlthcr.exhorter.org` | hlthcr | Live |
| `autoins.exhorter.org` | autoins-foundations | Live |
| `grp-frm.exhorter.org` | grp-frm | Live |

**Key lesson**: nginx must listen on port 80 (not `$PORT`). Railway custom domains route to port 80 on the container. The `$PORT` template causes a mismatch since Railway assigns a dynamic port at runtime.

---

## Git History

| Commit | Description |
|--------|-------------|
| `9ff99e9` | Initial static site with nginx Docker setup |
| `6ff0c6d` | Add VS Code theme settings |
| `ee8d82a` | Merge PR #1 (VS Code and Claude settings) |
