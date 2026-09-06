# Court shared skills home (Alex private)

Private GitHub repo: [alexderz/private-shared-skills](https://github.com/alexderz/private-shared-skills).

This is the Court shared skills home. Skills here are **tools**, not a marketplace dump. Each skill is keyed by pantheon role so agents pick the right tool for the job.

## Mirror

**Origin is inbound from GitHub.** GitHub is the source of truth. The Cursor Origin codebase at [cursor.com/codebase/alexderz/private-shared-skills](https://cursor.com/codebase/alexderz/private-shared-skills) mirrors this repo. Do not treat Origin as an independent write path for skill bodies.

## Pantheon roles

Skills are tools keyed by role:

| Role | Job |
| --- | --- |
| **Heph** | Architect and delivery |
| **Cedalion** | Mechanical CI, hooks, cleanup |
| **Argus** | Security gates across the SDLC, including skill intake |
| **Themis** | Court process and SDLC |

Improvise beyond predefinition when the work needs it. Do not remint a skill that already lives here.

## Intake rules (Argus first)

Stage 0 is an **empty skill home** ready for Argus intake and later cherry-picks.

- Do **not** install Superpowers, Pocock, or Addy as a whole pack.
- Pin every third-party cherry-pick **SHA** in [SOURCES.md](SOURCES.md). Empty SHA cells mean the body is not here yet.
- **Argus intake before any third-party content** lands in this repo.
- **No auto-update.** No marketplace install. No scripts. No secrets.
- Court-owned skills (`court-linear-sdlc`, `cursor-cloud-agents-when`) are written here; they are not vendor copies.

Directories under `skills/<id>/` exist as placeholders (`.gitkeep` only). There are **no `SKILL.md` bodies** in Stage 0.

## Skill ids

See [SOURCES.md](SOURCES.md) for upstream, SHA, license, and notes.

| Id | Ownership (Stage 0) |
| --- | --- |
| `court-linear-sdlc` | Court-owned |
| `cursor-cloud-agents-when` | Court-owned |
| `tdd` | Third-party candidate — Argus intake before content |
| `pr-review` | Third-party candidate — Argus intake before content |
| `security-hardening` | Third-party candidate — Argus intake before content |
| `shell-safety` | Third-party candidate — Argus intake before content |
| `verify-before-done` | Third-party candidate — Argus intake before content |
| `yagni` | Third-party candidate — Argus intake before content |
| `modern-python` | Third-party candidate — Argus intake before content |
| `golang-testing` | Placeholder for samber — Argus intake before content |

## Related

- First cherry-pick candidates (Argus intake): [docs/CHERRY-PICK-CANDIDATES.md](docs/CHERRY-PICK-CANDIDATES.md)
- Cedalion CI hooks (first cut, fmt/lint): [docs/CI-HOOKS-PLAN.md](docs/CI-HOOKS-PLAN.md)
- Court SDLC (GitHub copy): [docs/COURT-SDLC.md](docs/COURT-SDLC.md)
- Linear project: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9)
- heph-forge companion: `projects/upping-coding-game/COURT-SDLC.md` (heph-forge#9 amended)

Agents landing in this repo: start at [AGENTS.md](AGENTS.md).
