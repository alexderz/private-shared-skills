# Cedalion CI hooks — first cut

Thin plan for what to wire **first**. **No CI yaml in this Task.** **No skill bodies.**

Linear: [DER-52](https://linear.app/derzhi-grok-bot/issue/DER-52/cedalion-first-cut-ci-hooks-plan-fmtlint-only) (parent [DER-49](https://linear.app/derzhi-grok-bot/issue/DER-49/epic-skill-intake-first-cherry-picks)). Track: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9). Court SDLC: [docs/COURT-SDLC.md](COURT-SDLC.md). Candidates: [docs/CHERRY-PICK-CANDIDATES.md](CHERRY-PICK-CANDIDATES.md). Pins: [SOURCES.md](../SOURCES.md).

Owner: Cedalion (tooling pick). Argus still owns intake. Heph owns the candidate list.

Alex / Themis locks (~9:21pm CT Sat Sep 5).

## Repos

| Repo | Role |
| --- | --- |
| [alexderz/private-shared-skills](https://github.com/alexderz/private-shared-skills) | GitHub source of truth (this repo) |
| heph-forge | Origin companion (`projects/upping-coding-game/`) |

Same first-cut policy on both. GitHub is the design source of truth. Origin is inbound.

## Wire first (fmt / lint only)

Run **only** when matching files appear on the PR:

| Tool | When |
| --- | --- |
| **ruff** | Python appears |
| **gofmt** | Go appears |
| **shellcheck** | Shell scripts appear |
| markdown / prettier | **Optional skip** this cut |

Do **not** gate on third-party skill bodies yet. Argus intake is still running on `tdd` (and the rest of the Heph list). Empty `.gitkeep` dirs and unpinned vendor ids are not a CI fail.

Court-owned `security-hardening` is already pinned (`e207b901`, merge of [#3](https://github.com/alexderz/private-shared-skills/pull/3)). Hooks do **not** special-case it beyond normal path globs.

## Pre-commit vs GHA

Prefer **GitHub Actions on PR** for both repos if hooks are painful on Origin. Cedalion picks the exact action, image, and versions. Local pre-commit is optional, not required for this cut.

## Success

A PR **fails if format is dirty** (ruff / gofmt / shellcheck as applicable). No secret scan in this first cut — park for later (Argus / Cedalion).

## Non-goals (this cut)

- SkillSpector in CI — intake stays [docs/INTAKE.md](INTAKE.md) / Argus, before a body lands
- Full test suites
- Vendor skill SHA verification in CI — stays Argus + [SOURCES.md](../SOURCES.md) until more pins exist
- CI yaml or skill bodies in this PR
- Secret scan / dependency-audit hooks (Cedalion owns those later; see `security-hardening`)

## Later (not this Task)

Secret scan, dep audit, a CI echo of SkillSpector only if Argus asks, SHA-pin check once more vendor rows are pinned, prettier after the fmt gate exists.
