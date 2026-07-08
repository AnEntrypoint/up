# up

Webhook repo — POST a `repository_dispatch` event to add a file.

## Usage

```bash
gh api repos/AnEntrypoint/up/dispatches \
  --method POST \
  --field event_type="up" \
  --field client_payload='{"path": "entries/hello.md", "content": "# Hello\n\nfrom the webhook"}'
```

`client_payload` fields:

| field     | required | description             |
|-----------|----------|-------------------------|
| `path`    | yes      | file path to create     |
| `content` | yes      | file content to write   |

## Trigger URL

```
POST https://api.github.com/repos/AnEntrypoint/up/dispatches
```

Requires a token with `repo` scope.
