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

Skill ids with `SKILL.md` on `main` (do not remint #16–#20):

- `tdd`
- `verify-before-done`
- `pr-review`
- `shell-safety`
- `security-hardening`
- `modern-python`
- `golang-testing`
- `golang-security`
- `golang-safety`
- `yagni`

Court-owned placeholders / empty dirs (no body claim until SHA + `SKILL.md` on `main`):

- `court-linear-sdlc`
- `cursor-cloud-agents-when`

Load by id from this repo — never from managed Superpowers. Spector hygiene refine landed as PSS #20 (shell-safety FP soften + security-hardening AE1).

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
