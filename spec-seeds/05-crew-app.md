# Spec seed 5 — The Ritual (Kiro Crew app)

Build this in a **separate public repo** named `necropolis-crew` (needed for the Best Kiro Crew App bonus). Start from `kirocrew app init necropolis-ritual --ui` and read kiro.dev/docs/crew/apps first.

---

Create a spec for a Kiro Crew app called **Ritual** that runs the Necropolis resurrection pipeline.

- **Crewmates:** Coroner, Surgeon, Inquisitor, Medium, reusing the agent definitions from the main repo's `.kiro/agents/`.
- **Pipeline:** pick a package → Coroner writes AUTOPSY.md → Surgeon rebuilds in a worktree → Inquisitor runs the Mirror Test → on pass, Medium drafts SEANCE.md; on fail, the counterexample goes back to the Surgeon (max 3 loops, then stop and ask a human).
- **Cron:** nightly Census run; weekly "next candidates" list (top 5 undead pure-function packages not yet resurrected).
- **Dashboard (React, `@kirocrew/app-sdk/ui`):** candidate queue, live stage of each ritual, Mirror Test counter, links to Certificates, credits used per ritual.
- **Human gates:** a person approves before the Surgeon starts and before anything is published or any issue is posted.

Requirements (EARS form) must cover: every stage writes its artefact to the resurrection folder; a failed stage never leaves a half-certified package; the dashboard shows why a ritual stopped.
