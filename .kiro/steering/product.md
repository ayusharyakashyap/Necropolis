---
inclusion: always
---

# Product: Necropolis

Necropolis finds the *undead* of npm — packages that are still heavily downloaded but have no living maintainer — resurrects them with a crew of Kiro agents, and **proves** each resurrected package behaves exactly like the original.

## Who it is for

- **JavaScript teams** stuck on abandoned dependencies they cannot easily replace.
- **AI coding agents** (and the people supervising them) that keep pulling dead packages into new code.
- **Open-source maintainers and funders** who want to know which abandoned packages matter most.

## The one idea that matters

Rewriting code with AI is easy; trusting the rewrite is hard. Every resurrection must pass the **Mirror Test** (differential property-based testing: original vs reanimated, same inputs, same outputs, same thrown error types, same input mutation) and ships with a **Certificate of Resurrection**. If a feature does not serve that trust story, it is lower priority.

## Parts, in priority order

1. **Census** — nightly scoring of top npm packages on the Undead Index; publishes a public JSON dataset.
2. **Necropolis web app** — graveyard map + accessible table view, Autopsy pages, Certificates.
3. **Mirror Test** — the differential PBT harness and its self-checks.
4. **Autopsy** — exported API surface, cause of death, reanimation plan.
5. **Ritual** — the resurrection pipeline as a Kiro Crew app (Coroner, Surgeon, Inquisitor, Medium).
6. **Ward** — MCP server + Kiro power that stops agents from adding undead packages.
7. **Séance** — drafts one respectful issue offering the resurrection back to the original maintainer.

## Non-goals

- Publishing anything under an original package's name.
- Resurrecting packages with heavy I/O, native addons or non-deterministic behaviour (for now).
- Claiming statistics we did not compute ourselves.
