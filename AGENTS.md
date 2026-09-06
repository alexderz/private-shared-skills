# AGENTS

This repository is the **Court shared skills home** (Alex private). It is not an application repo.

GitHub is the source of truth. Origin is inbound from GitHub ([codebase](https://cursor.com/codebase/alexderz/private-shared-skills)). Do not write skill bodies only on Origin.

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

- `court-linear-sdlc` — court-owned
- `cursor-cloud-agents-when` — court-owned
- `tdd`
- `pr-review`
- `security-hardening`
- `shell-safety`
- `verify-before-done`
- `yagni`
- `modern-python`
- `golang-testing` — samber placeholder

Stage 0: each directory is a placeholder (`.gitkeep` only). **No `SKILL.md` bodies yet.**

## Intake (Argus)

Before any third-party content:

1. Do **not** install Superpowers, Pocock, or Addy as a whole pack.
2. Pin the cherry-pick SHA in [SOURCES.md](SOURCES.md).
3. Complete Argus intake.
4. No marketplace install, no auto-update, no scripts, no secrets in this repo.

Empty SHA cells mean the body must not exist yet.

## Related

- README: [README.md](README.md)
- Linear: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9)
- heph-forge COURT-SDLC: `projects/upping-coding-game/COURT-SDLC.md`
- Issue cut: [DER-46](https://linear.app/derzhi-grok-bot/issue/DER-46/stage-0-court-sdlc-skills-home-layout)
