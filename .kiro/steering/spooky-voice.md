---
inclusion: auto
name: spooky-voice
description: UI copy, visual design and theming for the Necropolis web app and Crew app UI. Use when writing user-facing text, styling components, or designing the graveyard map.
---

# Voice and design

## Voice

- Gothic but useful: the metaphor decorates the information, never hides it. Every spooky label has the plain fact right next to it ("Last breath: Mar 2019 · last publish 7 years ago").
- Short sentences. No jokes in error messages; errors say what happened and what to do.
- Vocabulary: *undead* (popular but unmaintained), *autopsy* (analysis), *ritual* (resurrection pipeline), *mirror test* (equivalence proof), *certificate* (proof record), *séance* (maintainer outreach), *ward* (agent guard).

## Visual system

- Dark by default (moonlit graveyard), with a full light theme. Colours as CSS custom properties.
- Data encodings on tombstones are consistent everywhere: **height = weekly downloads (log scale)**, **moss = years since last publish**, **red glow = open advisories**. A legend is always visible.
- One accent colour for "certified / resurrected" (spectral green). Red only for advisories.
- Motion is atmosphere (fog drift, candle flicker) and must stop under `prefers-reduced-motion`.

## Accessibility (non-negotiable)

- Every map view has an equivalent sortable table view one click away.
- Full keyboard navigation of tombstones; visible focus ring.
- Text contrast WCAG AA in both themes; never encode meaning in colour alone.
