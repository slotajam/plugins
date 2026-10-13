# Base44 Development Environment

## What This Repo Is

A curated collection of Codex plugin definitions (JSON manifests, skill markdown, MCP configs). It is **not** a traditional web application — there is no single frontend or backend server.

## What Runs in the Preview

The `plugins/data-analytics` plugin has a Vite dev server (`npm run preview:widgets`) that serves interactive widget HTML pages. The Base44 compose file runs this Vite dev server on port 3000.

- **Landing page**: `/` → `plugins/data-analytics/src/index.html` (links to all widgets)
- **Chart widget**: `/datascience-chart-widget.html`
- **Table widget**: `/datascience-table-widget.html`
- **Artifact widget**: `/datascience-artifact-widget.html`
- **Portable reader**: `/portable-artifact-reader.html`

Widgets use fallback sample data when no MCP host is connected (which is the case in the preview).

## Setup

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

The compose service installs npm dependencies (`npm ci`) from `plugins/data-analytics/package-lock.json` on each startup, then runs `npx vite --host 0.0.0.0 --port 3000`.

## No External Secrets Required

This repo does not require any external credentials. All widget data is fallback/sample data in the preview.
