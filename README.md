# Tech Stack Standard

Opinionated engineering standard for a modern product stack built with:

- Vite + React + TypeScript
- Supabase
- Railway
- Netlify
- Netlify Functions (small helpers only)

## Core principle

Use each platform for one job:

- **Netlify**: static frontend hosting, previews, redirects
- **Supabase**: Postgres, Auth, Storage, Realtime, RLS
- **Railway**: real backend services, workers, webhooks, cron, privileged logic
- **Netlify Functions**: tiny site-adjacent helpers only

## Golden path

```text
Browser -> Railway API -> Supabase
```

Avoid splitting core backend logic across Railway and Netlify Functions.

## Repo contents

- `README.md` — overview
- `docs/architecture.md` — architecture standard
- `docs/build-standard.md` — engineering rules
- `docs/decision-matrix.md` — when to use Supabase vs Railway vs Netlify Functions
- `docs/pr-checklist.md` — PR and release checklist
- `templates/.env.example` — env naming standard
- `templates/netlify.toml` — starter Netlify config
- `templates/repo-structure.txt` — suggested monorepo structure
- `.github/workflows/ci.yml` — starter CI pipeline

## Standard summary

### Frontend
- Vite + React + TypeScript
- feature-based folders
- route-level code splitting
- shared API client layer
- runtime form validation

### Backend
- Railway hosts the primary API
- server validates all writes
- payments, webhooks, cron, queues, and privileged actions stay server-side

### Data and auth
- Supabase is source of truth
- all user-facing tables use RLS
- all schema changes go through migrations
- service role keys never touch the browser

### Functions
Use Netlify Functions only if all of this is true:
- tiny
- site-adjacent
- not core business logic
- not worth a permanent API route

## Anti-patterns to ban

- exposing `SUPABASE_SERVICE_ROLE_KEY` to client code
- putting important backend logic in both Railway and Netlify Functions
- no migration history
- direct browser writes to tables without RLS
- duplicated validation logic
- env var naming chaos
- frontend orchestrating multi-step server workflows

## How to use this repo

1. Fork or copy it into your GitHub account
2. Adjust the standards to your actual app and team
3. Keep it as the source of truth for architecture decisions
4. Link it from your main product repos

## Recommended next step

Turn this into:
- an internal playbook repo
- a public engineering standard repo
- or a template monorepo with `/apps/web`, `/apps/api`, and `/packages/*`
