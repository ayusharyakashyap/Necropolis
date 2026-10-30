# Necropolis

> Your app depends on the dead. We raise them — and prove they're still themselves.

Necropolis finds heavily downloaded npm packages with no living maintainer, resurrects them with a crew of Kiro agents, and proves each resurrection behaves exactly like the original with the **Mirror Test** (differential property-based testing). Built for Kiroween 2026, category **Resurrection**.

---

## Starter kit: how to use it (delete this section before submitting)

This folder is a starting point, not the product. Kiro writes the code.

1. **Clone this repo** (MIT licence already in place; check it shows in the About panel). Do **not** gitignore `.kiro/`.
2. **Open the folder in Kiro IDE.** Read every file in `.kiro/steering/` and rewrite anything that isn't how you want it — the steering should be yours.
3. **Check the hooks load.** Open the Agent Hooks panel. If Kiro flags a trigger name, ask Kiro: *"Fix this hook file to match the current hook schema."* Some hooks start `"enabled": false` because the scripts they call don't exist yet; turn them on as each package lands.
4. **Generate the specs in order.** For each file in `spec-seeds/`, start a new spec in Kiro and paste the prompt. Review and edit `requirements.md` and `design.md` before letting Kiro run the tasks. Census → Mirror → Web are the must-haves.
5. **Keep `KIRO_JOURNAL.md` daily.** The Stop hook writes raw evidence to `.kiro/evidence-log.md`; turn it into readable notes. This becomes the "how Kiro was used" write-up.
6. **Custom agents** are in `.kiro/agents/` (Coroner, Surgeon, Inquisitor, Medium). Select them in the IDE or CLI for the matching stage; reuse them as crewmates in the Crew app.

Note for the write-up: the steering files, hooks, agent configs and spec seed prompts were first drafted with Claude as planning help; say so and describe how you changed them.

---

## Project layout

See `.kiro/steering/structure.md`.

## Running locally

_To be written as the packages land (Kiro: keep this section current)._

## Data sources

npm registry and downloads API, OSV.dev, deps.dev, OpenSSF Scorecard, GitHub API. All figures shown are computed by our own Census run and dated.

## Disclosure

As the Official Rules ask, pre-existing work is disclosed here: the initial `.kiro/` steering files, hook and agent configs, and the prompts in `spec-seeds/` were drafted with Claude as planning help on 2026-10-31 (inside the Submission Period), then reviewed and edited by me. All application code is written with Kiro during the Submission Period.

## Licence

MIT. Resurrected packages keep their original licences and credit their original authors.
