# Court SDLC

GitHub copy of the court SDLC (Alex: **designs on GitHub from onset**, not Origin-only).

Companion (heph-forge#9 amended): `projects/upping-coding-game/COURT-SDLC.md` on [heph-forge](https://cursor.com/codebase/alexderz/heph-forge).

Linear track: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9).

Skills home: this repo (`alexderz/private-shared-skills`). Origin is inbound from GitHub.

Alex locks (~9:04pm CT Sat Sep 5): GitHub designs from onset; Stage −1 Repo before HLD; Stage 4 loop until DoD; CA/grok with bot oversight; notify landed+verified.

No third-party skill bodies live in this file or in Stage 0 `skills/` directories. Pin SHAs in [SOURCES.md](../SOURCES.md). Argus intake before any vendor content.

## Hierarchy (Linear)

| Layer | Linear object | Meaning |
| --- | --- | --- |
| Track | **Project** | One court track |
| Chunk | **Parent issue** labeled `Epic` | Discrete, parallel slice |
| Work item | **Issue** labeled `Task` or `Bug` | Implementable unit; may nest sub-issues |

Team: `Derzhi Grok Bot`. After-act Themis with America/Chicago timestamps. Linear is the board; git holds durable artifacts. PRs cite a Linear ID.

## Stages

### Stage −1 Repo — GitHub ready + bots aware

Before Stage 0 HLD:

- GitHub repo or subdir exists (private as needed).
- README / AGENTS stub so bots who need access are aware.
- Cedalion watch if applicable.
- **Designs live on GitHub from onset.** Do not keep HLD/LLD Origin-only.

This skills home already existed as GitHub PRIVATE + Origin inbound ([DER-48](https://linear.app/derzhi-grok-bot/issue/DER-48/stage-1-repo-github-ready-bots-aware)). Product tracks still run Stage −1 per repo before HLD.

### Stage 0 HLD

Publish HLD on the Linear project and a git copy on GitHub. Lock hierarchy, persistence, and worker rules.

### Stage 1 PoC

Only if needed. Evidence in git on GitHub.

### Stage 2 LLD

Document + git copy on GitHub. Templates, status mapping, bot after-act, path conventions.

### Stage 3 Groom

Break into Tasks/Bugs with acceptance criteria and an LLD link.

### Stage 4 — loop until DoD

Implement and test at max safe parallelism. **Do not exit Stage 4 after one pass.** Loop implement → test → fix until the ticket Definition of Done is actually met.

DoD includes: acceptance on the Linear issue, tests/verification evidence, PR cites Linear ID, no silent scope leftover. Notify **landed+verified** — not “pushed” and not “LGTM without evidence.”

### Stage 5 Review gate

Review agent approves the PR only if it meets the ticket + LLD.

### Stage 6 Integration

More Tasks, not a special ceremony.

### Stage 7 Release

Coherent chunk. CHANGELOG in the repo.

### Stage 8 Monthly

Vuln / updates / new solutions review. Recurrence note only until Themis/Alex cut a Task. No watcher, no cron ([DER-45](https://linear.app/derzhi-grok-bot/issue/DER-45/epic-monthly-vulnupdate-review)).

## Workers (CA / grok)

| Worker | When |
| --- | --- |
| **Cloud Agent (CA)** | Remote repo / PR work |
| **grok CLI** | Box-local gated builds; use when CA credit degrades |
| **Origin** | Inbound mirror of GitHub. Not the design source of truth. |

Bot oversight: Heph adversarial-reviews other bots’ tools when the work needs it. Cedalion owns mechanical CI/hooks. Argus owns security gates and skill intake. Themis after-acts the board; does not bless before ship.

Notify only when work is **landed and verified**.

## GitHub designs from onset

- HLD, LLD, PoC notes, decisions, changelogs, and this SDLC land on **GitHub** from Stage −1.
- Origin may mirror (inbound). Do not treat Origin as an independent write path for designs.
- heph-forge keeps a companion copy at `projects/upping-coding-game/COURT-SDLC.md` (amended on heph-forge#9).
- This file is the GitHub copy for the skills home and for agents who only have this repo.

## Pantheon roles

Skills are **tools**, keyed by role. Improvise beyond predefinition. Do not remint a skill that already has an id.

| Role | Job |
| --- | --- |
| **Heph** | Architect and delivery |
| **Cedalion** | Mechanical CI, hooks, cleanup |
| **Argus** | Security gates across the SDLC, including skill intake |
| **Themis** | Court process and SDLC after-act |

## Skill table

Ids and ownership: [SOURCES.md](../SOURCES.md). Empty SHA = no body yet. Do not install Superpowers / Pocock / Addy whole. No marketplace install. No auto-update.

| Skill | Role | Upstream (Stage 0) | Notes |
| --- | --- | --- | --- |
| `court-linear-sdlc` | Themis / Heph | court-owned | Empty dir until court body |
| `cursor-cloud-agents-when` | Heph | court-owned | Empty dir until court body |
| `tdd` | Heph | TBD — Argus intake | No vendor body |
| `pr-review` | Heph / Argus | TBD — Argus intake | No vendor body |
| `security-hardening` | Argus | TBD — Argus intake | Compress after Argus intake |
| `shell-safety` | Argus / Cedalion | TBD — Argus intake | No vendor body |
| `verify-before-done` | Heph | TBD — Argus intake | Stage 4 / notify landed+verified |
| `yagni` | Heph | TBD — Argus intake | No vendor body |
| `modern-python` | Heph | TBD — Argus intake | No vendor body |
| `golang-testing` | Heph | samber placeholder | No vendor body |

## Pilot order

1. **heph-forge `AGENTS.md`** — first product-repo pilot of this SDLC.
2. **`alexderz/spending-tracker` `AGENTS.md`** — second.

This skills home is layout + SDLC copy only in Stage 0. Later cuts on the track (Cedalion CI hooks; Argus intake + `security-hardening` compress) follow Argus rules and do not skip the pilot order.
