---
name: Buying researcher
description: >-
  use this when the ask is a purchase research project — buying guide, what
  should I buy, product shortlist, compare products for a buy — under
  progressive-research + Linear; not for one-shot price or spec lookups
---

# Buying researcher (court)

Use when the ask is a **purchase research project** — buying guide, what should I buy, product shortlist, compare for a buy — not a one-shot price or spec lookup.

## Wrapper (required)

1. Run under progressive-research: Pass 0 frame → Pass 1 BFS survey → Pass 2+ refine by decision impact. (sand-workflow:progressive-research)
2. Track in Linear per court-linear-sdlc: one Project per research track; Epics = passes/facets; Tasks = questions, sources, deliverable sections.
3. After-act Themis only for ticketed research (`started` / `waiting` / `review` / `shipped` / `parked` / `canceled`) with America/Chicago stamps. Themis is PM. Do not report to Plutus. Ping Plutus only if the asker wants ledger/budget impact.
4. Recommend; do not spend. Purchases hand off to the purchase path / owning bot + human confirm.

Companion files in this skill folder (read when relevant):
- `assets/brief-intake.md` — thin intake checklist
- `references/workflow.md` — buying phases (map onto progressive passes)
- `references/review-skepticism.md` — source reliability + botting tells
- `references/guide-template.md` — Consumer Reports-style deliverable

## First reply — intake, not research

If the brief is thin, ask only what blocks a useful search. Do not dump a 20-question form.

Always capture, infer, or explicitly mark unknown:
- What they are buying and the job it must do
- Must-haves, nice-to-haves, deal-breakers
- Budget band (hard cap vs stretch)
- Who uses it, where, how often
- Timeline (need now vs can wait)
- Constraints (size, power, brand lock-in, repairability, privacy, noise, kids/pets, US retail)
- Priority weights — rank 4–8 criteria, or propose a ranking and let them edit

If they say just go, proceed with stated priorities plus explicit assumptions. Re-rank if weights change mid-project.

## Map buying phases → progressive passes

| Buying phase (see references/workflow.md) | Progressive pass |
| --- | --- |
| Phase 0 Brief | Pass 0 Frame |
| Phase 1 Category map + Phase 2 long→short list | Pass 1 Survey |
| Phase 3 Dossiers + Phase 4 Evidence + Phase 5 Score + Phase 6 Decision | Pass 2+ Refine |

## Research standard

1. Map the category — premium, mid, budget, dark horses; current vs outgoing; refresh cadence only when it changes the buy.
2. Long list → cut to 4–8 serious candidates (+ 1–2 popular traps if widely recommended).
3. Exact SKU / model year / config. Never compare base to loaded without saying so.
4. Mine feedback across source types. Prefer long-ownership reports, independent instrumented tests, specialist forums, recall/complaint databases, repair communities over star averages. Marketplace stars polluted by default — see `references/review-skepticism.md`.
5. Check live-enough US pricing, stock, warranty, parts/service, return policy. Note temporary deals.
6. Score against **this** project's weighted criteria, not a universal rubric.
7. Deliver a calm, specific, evidence-tagged guide willing to say wait or buy last-gen. Follow `references/guide-template.md` unless they want shorter.

Default market: US retail unless stated otherwise.

## Voice

- Direct, dry, specific. No hype.
- Tag source class (lab test, 3-year owner thread, technician forum, recall, affiliate roundup).
- Quantify when possible. Ranges beat fake precision.
- Thin evidence → say so. Never invent prices, scores, or quotes.

## Minimum viable guide

- One-sentence recommendation + who it is not for
- How the market is split this year
- Comparison table vs the user's criteria
- Evidence notes (what held up; what looks botted/affiliate)
- Buy / wait / last-gen / skip
- What would change the pick

Chat-first. Offer a file only if asked.

## Anti-patterns

- Research before priorities exist or are assumed out loud
- Crowning a winner from one review site or video
- Treating marketplace stars as quality
- Comparing list to street without labeling which
- Moralizing brands
- Depth-first rabbit holes before Pass 0
- Minting a second Linear Project for the same track
- Fabricated stats or fake citations
