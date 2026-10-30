# Spec seed 3 — The Necropolis web app

---

Create a spec for `apps/web`: a static Vite + React site that presents the Necropolis dataset. Follow the spooky-voice steering file for copy, visuals and accessibility.

Pages:
1. **The Necropolis (map)** — every package from `undead.top.json` as a tombstone on a scrollable, zoomable graveyard. Height = weekly downloads (log), moss = years since last publish, red glow = open advisories, spectral green = certified resurrection. Always-visible legend. Hover/focus shows name, index, last publish, weekly downloads.
2. **Table view** — the same data, sortable and filterable, one click from the map; the default for screen readers.
3. **Autopsy page** per package — API surface, cause of death with evidence, Undead Index breakdown, link to the resurrection if any.
4. **Certificate page** per resurrection — renders `CERTIFICATE.json`: inputs tried, divergences, functions covered, allowed differences, seed, date, and a "how to verify yourself" command.
5. **About** — what the Undead Index means, data sources, run date, limits.

Requirements (EARS form) must cover: keyboard navigation of tombstones, `prefers-reduced-motion`, light and dark themes, WCAG AA contrast, works on a phone (map falls back to table under 600 px), loads the dataset once, deep links to every package.
