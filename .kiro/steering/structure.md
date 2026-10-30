---
inclusion: always
---

# Repository structure

```
necropolis/
├── .kiro/                 # specs, steering, hooks, agents — never gitignored
├── apps/
│   └── web/               # Necropolis map, Autopsy, Certificates (Vite + React)
├── packages/
│   ├── census/            # Undead Index scoring + dataset builder
│   ├── mirror/            # Mirror Test differential PBT harness
│   ├── autopsy/           # API surface extraction + cause-of-death analysis
│   └── ward-mcp/          # MCP server
├── powers/
│   └── necropolis-ward/   # Kiro power (Agent Plugins layout) wrapping ward-mcp
├── resurrections/
│   └── <package-name>/    # one folder per resurrected package + its CERTIFICATE.json
├── data/                  # generated datasets (committed snapshot for the demo)
└── KIRO_JOURNAL.md        # running log of how Kiro was used (feeds the write-up)
```

The Kiro Crew app lives in a **separate public repo** (`necropolis-crew`) so it can be installed through Crew's app model and submitted for the Best Kiro Crew App prize.

## Conventions

- Package names: `@necropolis/<name>`.
- One exported function per file in `packages/*/src`, named after the file.
- Pure functions for scoring and comparison logic so they are easy to property-test.
- Types live next to the code; shared types in `packages/census/src/types.ts` (the dataset schema is the contract between all parts).
