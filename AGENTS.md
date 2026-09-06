# AGENTS

This repository is the **Court shared skills home** (Alex private). It is not an application repo.

GitHub is the source of truth. Origin is inbound from GitHub ([codebase](https://cursor.com/codebase/alexderz/private-shared-skills)). Do not write skill bodies only on Origin.

**Do not use the managed Superpowers plugin.** Court process skills live under `skills/<id>/` in this repo (or will after Argus remint). Prefer sand-workflow / installed court skills that twin these ids. Load court skills from this repo by id — never from Cursor managed Superpowers.

## Skills are tools, keyed by pantheon role

| Role | Job |
| --- | --- |
| Heph | Architect and delivery |
| Cedalion | Mechanical CI, hooks, cleanup |
| Argus | Security gates and skill intake |
| Themis | Court process and SDLC |

Pick the tool that matches the role. Improvise when the work needs it. Do not remint a skill that already has an id here.

## Inventory

Authoritative table: [SOURCES.md](SOURCES.md).

Skill ids (directories under `skills/`):

- `court-linear-sdlc` — court-owned (placeholder)
- `cursor-cloud-agents-when` — court-owned (placeholder)
- `tdd` — remint in flight after Alex ~9:24pm CT remint GO; body is not on `main` yet
- `pr-review`
- `security-hardening` — court-owned body on `main` (`skills/security-hardening/SKILL.md`)
- `shell-safety`
- `verify-before-done`
- `yagni`
- `modern-python`
- `golang-testing` — samber placeholder

Placeholders (`.gitkeep` only) remain for empty ids. `security-hardening` already has `SKILL.md` on `main`. Bodies land via Argus intake + court compress. Do not claim a remint body exists until it is on `main`.

## Intake (Argus)

Before any third-party content:

1. Do **not** install Superpowers, Pocock, or Addy as a whole pack.
2. Pin the cherry-pick SHA in [SOURCES.md](SOURCES.md).
3. Complete Argus intake.
4. No marketplace install, no auto-update, no scripts, no secrets in this repo.

Empty SHA cells mean the body must not exist yet.

## Related

- README: [README.md](README.md)
- Court SDLC (GitHub copy): [docs/COURT-SDLC.md](docs/COURT-SDLC.md)
- Linear: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9)
- heph-forge companion: `projects/upping-coding-game/COURT-SDLC.md` (heph-forge#9)
- Issue cut: [DER-46](https://linear.app/derzhi-grok-bot/issue/DER-46/stage-0-court-sdlc-skills-home-layout)
