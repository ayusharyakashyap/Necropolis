---
inclusion: always
---

# Ground rules (always apply)

- **Never** publish, or prepare to publish, anything under an original package's name. Resurrections use the `@necropolis/` scope and say "unofficial resurrection of <name>" in their README and `package.json` description.
- Keep the original licence file and copyright notices; add attribution to the original authors at the top of the README. Skip packages whose licence does not allow modification and redistribution.
- The Séance comes first: draft one polite issue to the original repository offering the work back. Never open more than one issue per repository, never ping individuals repeatedly.
- Do not run original package code outside the sandbox/container.
- Only show statistics that our own Census computed, with the date of the run. No borrowed or estimated numbers in the UI or the video.
- Never commit secrets. Tokens come from environment variables (`GITHUB_TOKEN`), documented in `.env.example`.
