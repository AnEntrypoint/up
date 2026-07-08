# up

Webhook worker — POST a file to the repo.

## Via Cloudflare Worker

```bash
curl -X POST https://up.<your-worker-subdomain>.workers.dev \
  -H 'Content-Type: application/json' \
  -d '{"path": "entries/hello.md", "content": "# Hello\n\nfrom the webhook"}'
```

Requires `GH_TOKEN` set as a worker secret with `repo` scope on `AnEntrypoint/up`.

## Via repository_dispatch (GitHub Actions)

```bash
gh api repos/AnEntrypoint/up/dispatches \
  --method POST \
  --field event_type="up" \
  --field client_payload='{"path": "entries/hello.md", "content": "# Hello\n\nfrom the webhook"}'
```

## Payload

| field     | required | description             |
|-----------|----------|-------------------------|
| `path`    | yes      | file path to create     |
| `content` | yes      | file content to write   |

## Deploy

```bash
wrangler deploy
wrangler secret put GH_TOKEN
```
