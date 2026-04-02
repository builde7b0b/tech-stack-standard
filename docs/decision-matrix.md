# Decision Matrix

## Use Supabase directly from the client when:
- simple CRUD
- user-scoped data
- RLS is correctly applied
- no privileged secrets required

## Use Railway API when:
- money or payments involved
- secrets involved
- multiple systems involved
- retries, queues, cron needed
- auditability required

## Use Netlify Functions only when:
- tiny
- site-adjacent
- not core logic

## Bad pattern
Mixing all three randomly from the client.
