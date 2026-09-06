# First cherry-pick candidates (Argus intake)

Heph list for Argus. **Names, upstream repos, and why only.** No skill bodies in this Task. No vendor `SKILL.md`. No marketplace pack.

Linear: [DER-51](https://linear.app/derzhi-grok-bot/issue/DER-51/first-cherry-pick-candidates-list-no-bodies) (parent [DER-49](https://linear.app/derzhi-grok-bot/issue/DER-49/epic-skill-intake-first-cherry-picks)). Court SDLC: [docs/COURT-SDLC.md](COURT-SDLC.md). Intake gate: [docs/INTAKE.md](INTAKE.md). Pins: [SOURCES.md](../SOURCES.md).

Owner: Heph (this list + SHA pin after clear) + Argus (intake).

## Gates before any body lands

Do **not** install Superpowers, Pocock, or Addy as a whole pack.

1. Argus intake per [docs/INTAKE.md](INTAKE.md). Workers do not bypass.
2. **SkillSpector** (and/or cisco skill-scanner / verified obielin skillguard — verify the GitHub org) **before a body lands**. Layout-only `.gitkeep` dirs do not need a scan.
3. Pin the cherry-pick **SHA** in [SOURCES.md](../SOURCES.md) **after Argus clear**, before the body. Empty SHA = no body. Court-owned rows use `court-owned` in the SHA cell.
4. Rewrite ≤250 lines in court voice. No verbatim vendor paste. No `scripts/`. No secrets. No auto-update.

Heph names the SHA set after the first Argus clear. This file is not a pin list.

## Candidates

| Candidate id | Upstream | Why | Notes |
| --- | --- | --- | --- |
| `tdd` | [obra/superpowers](https://github.com/obra/superpowers) (`test-driven-development`) | Iron law fail-first | May overlap managed Superpowers; Argus decides |
| `verify-before-done` | [obra/superpowers](https://github.com/obra/superpowers) (`verification-before-completion`) | No done without fresh evidence | Same overlap risk; Argus decides |
| `pr-review` | [mattpocock/skills](https://github.com/mattpocock/skills) (`code-review` dual-axis) | Standards vs Spec unmerged | **Rename** off `/code-review` collision. Court id stays `pr-review` |
| `security-hardening` | court-owned (Argus Always/Ask/Never compress) | [DER-50](https://linear.app/derzhi-grok-bot/issue/DER-50/argus-alwaysasknever-security-hardening-compress) — not a vendor cherry-pick | Already landed on `main` ([#3](https://github.com/alexderz/private-shared-skills/pull/3)). Do not remint |
| `shell-safety` | court-owned ≤80 lines preferred | Safe shell defaults for Cedalion/Argus | konstruktoid bash-secure as **reference only** — not a vendor install |
| `modern-python` | [trailofbits/skills](https://github.com/trailofbits/skills) `modern-python` | uv / ruff / ty / pytest | CC-BY-SA; on-demand later |
| `golang-testing` | [samber/cc-skills-golang](https://github.com/samber/cc-skills-golang) (`golang-testing`) | Go idioms the Big Three lack | On-demand later |

Placeholders already exist under `skills/<id>/` (`.gitkeep` except `security-hardening`, which has a court-owned body). This list does not authorize copying those upstream files.

## Not in this cut

- Whole Superpowers / Pocock / Addy packs — do not install.
- `yagni` — Stage 0 placeholder in [SOURCES.md](../SOURCES.md); not a first-cut Argus intake item unless Argus pulls it.
- Court-owned still-empty ids (`court-linear-sdlc`, `cursor-cloud-agents-when`) — written here later; not vendor cherry-picks.

## Suggested intake order

Argus decides order. Suggested only:

1. `security-hardening` — done (court-owned; skip vendor intake).
2. `tdd`, `verify-before-done`, `pr-review` — process cut; check managed-Superpowers overlap before any SHA.
3. `shell-safety` — court-owned compress; reference-only look at konstruktoid, then SkillSpector if any third-party lines remain.
4. `modern-python`, `golang-testing` — on-demand later; still need Argus clear + SHA pin + SkillSpector before a body.
