# Argus third-party skill intake

Checklist before any third-party skill **body** lands in `alexderz/private-shared-skills`. Argus owns this gate. Workers (Cloud Agent, grok CLI, Origin) do not bypass it.

Court-owned files written in this repo (this checklist, `skills/security-hardening/SKILL.md`) are not vendor intake. They still must not ship secrets or `scripts/`.

## Checklist

1. **Clone, do not `npx`.** Fetch the upstream git repo (clone or fetch + checkout). Do not marketplace-install a pack. Do not `npx` an installer, skill runner, or “add this skill” command.
2. **Quarantine scripts.** Do not copy `scripts/`. Do not run upstream install, postinstall, or bootstrap scripts. Treat executable skill helpers as untrusted until Argus says otherwise — default is drop them.
3. **Scan the candidate.** Run SkillSpector, cisco skill-scanner, and/or a **verified** obielin skillguard. **Verify the GitHub org** on the tool before you trust the binary or action (name collisions are not a clear).
4. **Pin SHA in [SOURCES.md](../SOURCES.md) before the body.** The table row must name upstream, SHA, license, and notes. Empty SHA means no body may land. Court-owned rows use `court-owned` in the SHA cell.
5. **Rewrite ≤250 lines + least privilege.** Do not paste a vendor `SKILL.md` verbatim. Compress into court voice. Review skills must not write (eduardo-sl). No secrets. No extra skill bodies in the same PR unless Argus asked for them.
6. **No auto-update.** Pin stays until a later Argus-cleared bump. No marketplace sync, no “latest”, no unattended vendor pull.

## Workers

Cloud Agent PRs into this repo **still need Argus clear**. Remote authoring is not an exemption. Stage 4 DoD still requires the diff to match the pinned SHA (or `court-owned` for court prose).

## Layout-only exception

Empty skill directories that only hold `.gitkeep` (layout, no `SKILL.md`, no scripts) are **OK without scan**. Intake and scanners start when a body, script, or third-party file would land.
