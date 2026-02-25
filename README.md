# Creddy Plugin Registry

Central index of available Creddy plugins.

## How it works

1. Plugin repos trigger the `update-registry` workflow on release
2. The workflow updates `index.json` with the new version
3. The updated index is uploaded to `plugins.creddy.dev/index.json`

## Triggering an update

Plugin release workflows can trigger an update via repository dispatch:

```yaml
- name: Update registry
  uses: peter-evans/repository-dispatch@v2
  with:
    token: ${{ secrets.REGISTRY_TOKEN }}
    repository: getcreddy/registry
    event-type: plugin-release
    client-payload: '{"plugin": "github", "version": "v0.0.3", "description": "GitHub App installation tokens"}'
```

## Manual updates

You can also manually trigger the workflow or edit `index.json` directly.
Changes pushed to main are automatically synced to R2.
