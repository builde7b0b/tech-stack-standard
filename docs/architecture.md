# Architecture Standard

## Platform responsibilities

### Netlify
Use Netlify for:
- frontend hosting
- branch previews
- redirects/rewrites
- forms
- tiny helper functions if needed

Do **not** use Netlify as your primary backend.

### Supabase
Use Supabase for:
- Postgres
- Auth
- Storage
- Realtime
- Row Level Security

Supabase is the application data platform and identity source of truth.

### Railway
Use Railway for:
- API services
- background workers
- webhook handlers
- scheduled jobs
- queues/retries
- privileged business logic

Railway is the main execution layer for backend logic.

## Golden path

```text
Client -> Railway API -> Supabase
```
