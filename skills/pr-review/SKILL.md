---
name: pr-review
description: use this when reviewing a PR or diff before merge — reviewer is not the builder; first review is a clean reviewer, later rounds on the same PR resume that reviewer; two axes (Standards vs Spec).
---

# PR review

Rewrite. Process inspired by Superpowers `requesting-code-review` (fresh-context) @ `b36e0829`. Dual-axis shape inspired by Matt Pocock `code-review` (Standards vs Spec) @ `3cca18b3`. **Id is `pr-review`** — do not install Pocock/Superpowers packs or use `/code-review` as the skill name.

**Review skills should not write.** Read, report, escalate. Fixes are a different pass.

Aligns with SDLC Stage 5: review before integrate. The reviewer is **not**
the builder. First review of this PR: mint a **clean** reviewer with
crafted inputs (ticket/LLD/spec, SHAs, standards). Later rounds on the
**same PR**: **resume that reviewer**. Do not mint a new reviewer each
round. Never give it the builder’s transcript. See
[docs/SDLC.md](../../docs/SDLC.md) (Subagents per work item).

## Iron law

**No merge on builder self-review alone.** First review is a clean
reviewer with crafted inputs — never the builder’s chat history as the
reviewer’s memory. Later reviews of this PR resume that reviewer.

## Always

1. **Pin the range.** Three-dot diff vs a fixed point (`main`, merge-base, tag, SHA). Confirm the ref resolves and the diff is non-empty.
2. **Craft context only (first launch).** Description, ticket/LLD/spec link, base/head SHAs, standards sources (`AGENTS.md`, `CODING_STANDARDS.md`, CONTRIBUTING). Not the builder transcript. **Later rounds:** resume the same reviewer; send the new range and what changed — do not re-paste the spec.
3. **Two axes, separate:**
   - **Standards** — repo conventions + judgement smells (see baseline). Documented repo rules override smells.
   - **Spec** — ticket/LLD/acceptance: missing, wrong, or scope creep. Quote the requirement.
4. **Report both axes** under `## Standards` and `## Spec`. Do not merge or rerank across axes.
5. **Act:** Critical/Important before merge; Minor can follow. Push back with reasoning if the reviewer is wrong.

## Ask first

| Topic | Why |
| --- | --- |
| No spec/ticket available | Spec axis may skip — say so explicitly |
| Skipping a separate reviewer because “tiny diff” | Still mint (or resume) the reviewer for Stage 5 |
| Reviewer wants write/merge tools | Review skill must not grow write privilege |

## Never

| Never | Why |
| --- | --- |
| Self-review as the only Stage 5 gate | SDLC: reviewer is not the builder |
| Trust “LGTM” without reading the diff | No evidence |
| Install Superpowers/Pocock review packs beside this skill | Dual routers |
| Review skill that deploys, merges, or rotates secrets | Review skills should not write |

## Smell baseline (judgement only)

Repo standards win. Skip what tooling already enforces. Label as heuristic, not hard fail unless a documented standard says so:

Mysterious Name · Duplicated Code · Feature Envy · Data Clumps · Primitive Obsession · Repeated Switches · Shotgun Surgery · Divergent Change · Speculative Generality · Message Chains · Middle Man · Refused Bequest

## Roles

| Role | Owns | Does not own |
| --- | --- | --- |
| **architect** | Requesting a clean reviewer (then resuming it) | Treating self-LGTM as Stage 5 |
| **builder** | Fixing Critical/Important after the review | Using builder-session memory as the review |
| **security** | Security axis at PR (trust boundaries); intake | Rewriting product specs in review |
| **tester** | CI evidence the reviewer can cite | Product Spec axis |
| **manager** | After-act | Blessing merge without Stage 5 |

## Red flags

- “I’ll just skim it myself in this session”
- “The builder explained why it’s fine”
- “Spawn a new reviewer every round so it stays fresh”
- Merging Standards pass to hide Spec fail (or the reverse)
- Reviewer opening write tools “to finish the review”

## Upstream pins

- Process: obra/superpowers `requesting-code-review` @ `b36e0829c6d0140e93cfef2ca599b1b07d4a7797`
- Dual-axis: mattpocock/skills `skills/engineering/code-review` @ `3cca18b368ae95cdbdebbff572ccafa662551015`

See [SOURCES.md](../../SOURCES.md).
