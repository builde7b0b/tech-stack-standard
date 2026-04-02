# Build Standard

## Monorepo standard

```text
/apps
  /web
  /api
/packages
  /ui
  /types
  /config
  /supabase
  /utils
/supabase
  /migrations
  /seed
/netlify
  /functions
```

## Type safety

- TypeScript everywhere
- shared schemas for request/response validation
- generated DB types from Supabase
- env vars validated on startup
- request payloads validated at API boundaries

## API standard

- route namespace: `/v1`
- required `/health` endpoint
- structured error shape
- request IDs in logs
- idempotency for critical writes
- signature verification for webhooks
- server-side validation for every mutation

## Database standard

- migration-only schema changes
- constraints first, not just app logic
- indexes for real query paths
- foreign keys where appropriate
- clear ownership and delete behavior for every table

## Frontend standard

- feature-first folders
- one API layer, not random fetch calls everywhere
- route-based code splitting
- separate server state from UI state
- forms use shared validation schemas
- design primitives live in a shared package

## Release standard

Every schema-affecting PR should include:
- migration
- generated types update
- backend changes
- frontend changes
- rollout notes if needed
