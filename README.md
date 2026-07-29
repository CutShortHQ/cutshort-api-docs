# Cutshort Public API docs

Public Mintlify site source for the Cutshort REST API (v1). **No secrets** — safe to publish.

Canonical copy is maintained in the private monorepo at `cutshortio/docs/api/`. This repository is a **public mirror** so [Mintlify](https://mintlify.com) can deploy without access to private GitHub repos.

## Live site

- Custom domain (target): `https://developers.cutshort.io`
- Short link: `https://cutshort.io/a/devdocs`

Machine-readable specs (always current on production):

- OpenAPI: `https://cutshort.io/api/v1/openapi.json`
- Agent guide: `https://cutshort.io/api/v1/agent-guide`

## Local preview

```bash
npx mintlify dev
```

Default: http://localhost:3000

## Mintlify deploy

1. Mintlify dashboard → **Git settings** → connect **`CutShortHQ/cutshort-api-docs`** (this public repo).
2. Set **docs root** to `/` (repository root — `docs.json` is here).
3. Custom domain: `developers.cutshort.io`.
4. Publish. Pushes to `main` trigger deploys.

Remove or ignore any Mintlify web-editor pages that are not in this repo (old AI-generated MCP/API content).

## Sync from private monorepo

When API docs change in `cutshortio`, run from your machine:

```bash
# From cutshortio repo
./tools/sync-public-api-docs.sh
```

Or manually:

```bash
rsync -a --delete cutshortio/docs/api/ cutshort-api-docs/
cd cutshort-api-docs && git add -A && git commit -m "Sync API docs from cutshortio" && git push
```

OpenAPI subset source of truth in backend:

`cutshort-backend/src/PublicApi/docs/openapi.json`

Update `openapi/public-api-v1.json` here when shipping new Public API endpoints.
