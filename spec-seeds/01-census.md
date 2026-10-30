# Spec seed 1 — The Census

Paste this into Kiro's spec chat ("New spec") and let Kiro write requirements.md, design.md and tasks.md. Edit what it produces; that editing is part of your write-up.

---

Create a spec for `packages/census`: a Node 22 TypeScript tool that builds the Necropolis dataset.

Goal: score the most-downloaded npm packages on an **Undead Index** and write `data/undead.json` plus a compact `data/undead.top.json` (top 500 by index) for the web app.

Inputs:
- A seed list of package names (start with a public top-packages list; also accept a plain text file of names).
- npm registry metadata, npm weekly downloads, OSV advisories (use `querybatch`), deps.dev metadata, OpenSSF Scorecard *Maintained* check, GitHub last commit and archived flag.

Undead Index (0–100) must combine: weekly downloads (log-scaled, popularity), time since last publish, time since last commit, open advisories on the latest version, deprecation flag, archived repo, Scorecard Maintained score. Make the weights a config object, documented in design.md.

Requirements to include, written in EARS form:
- Every network response is cached in SQLite with a fetched-at timestamp; reruns within 24h hit the cache.
- Concurrency is bounded and failures retry with backoff; one failing package never aborts the run.
- Each record carries the raw signals, the index, the reasons ("cause of death" list) and the run date.
- The JSON schema is exported as TypeScript types and is the contract for every other package.

Enable **property-based tests** (fast-check) for the scoring function, with at least these properties:
- The index is always within 0–100 and never NaN.
- Holding everything else equal, more weekly downloads never lowers the index.
- Holding everything else equal, a more recent publish never raises the index.
- Adding an open advisory never lowers the index.
- An archived repository scores at least as high as the same package unarchived.
