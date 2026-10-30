# Spec seed 4 — The Ward (MCP server + Kiro power)

---

Create a spec for `packages/ward-mcp` and `powers/necropolis-ward`.

`ward-mcp` is a stdio MCP server built with `@modelcontextprotocol/sdk` that answers from the Necropolis dataset (local file or the published URL), falling back to a live npm registry lookup for packages not in the dataset.

Tools:
- `check_package(name, version?)` → verdict (`alive`, `undead`, `certified-twin-available`, `not-found`), Undead Index, cause of death, last publish date, suggested replacement (certified twin first, then a living alternative if known).
- `scan_manifest(path)` → the same verdict for every dependency in a `package.json`.
- `get_certificate(name)` → the Certificate summary for a resurrected package.

Also a CLI entry `necropolis-ward scan <package.json>` that exits non-zero when any dependency is `undead` or `not-found` (used by a Kiro hook and CI).

`powers/necropolis-ward` packages the server as a Kiro power in the Agent Plugins layout: `mcp.json`, a `skills/` folder with one skill ("vet dependencies before installing") and a short steering note. Check the current layout at kiro.dev/docs/powers and agent-plugins.org before building.

Requirements (EARS form) must cover: response time under 200 ms for dataset hits, never executing package code, clear messages an agent can act on, and graceful behaviour offline.

Enable **property-based tests**: `scan_manifest` returns exactly one verdict per dependency; verdicts for the same input are deterministic.
