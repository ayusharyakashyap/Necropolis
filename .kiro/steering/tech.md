---
inclusion: always
---

# Tech stack

- **Language:** TypeScript everywhere, `strict: true`. Node 22+. ESM first.
- **Monorepo:** pnpm workspaces.
- **Testing:** Vitest for unit tests; **fast-check** for all property-based tests.
- **Census:** plain Node script, `fetch` + `p-limit` for concurrency, a local SQLite cache (`better-sqlite3`) so reruns do not hammer public APIs. Output: `data/undead.json` (+ a smaller `data/undead.top.json` for the web app).
- **Mirror Test:** fast-check + the TypeScript compiler API (to read the exported surface from `.d.ts` or JSDoc); runs the original from the npm tarball of its last published version.
- **Ward:** `@modelcontextprotocol/sdk`, stdio transport.
- **Web:** Vite + React, static build, no server. Reads the JSON dataset at build time and fetch time.
- **Crew app:** separate repo, Kiro Crew App SDK (`@kirocrew/app-sdk`, `@kirocrew/app-sdk/ui` as build externals).

## Public data sources (free)

| Source | Use |
| --- | --- |
| npm registry (`registry.npmjs.org`) | versions, publish dates, deprecation flags, repository URL |
| npm downloads API (`api.npmjs.org/downloads`) | weekly downloads |
| OSV.dev (`api.osv.dev/v1/query`, `querybatch`) | known advisories per version |
| deps.dev (`api.deps.dev/v3alpha`) | package metadata, licences, links |
| OpenSSF Scorecard (`api.scorecard.dev`) | the *Maintained* check |
| GitHub REST API | last commit date, archived flag (needs `GITHUB_TOKEN`) |

## Rules

- Cache every network response; never fetch on web page load except the static dataset.
- Respect rate limits: bounded concurrency, retries with backoff, `User-Agent` set to `necropolis (+repo URL)`.
- Code from original (dead) packages runs **only** inside the local command sandbox or a container with networking off.
- No new runtime dependency without a one-line reason in the PR/spec task.
