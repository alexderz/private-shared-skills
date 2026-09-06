---
name: pr-review
description: use this when reviewing a PR or diff before merge — fresh-context reviewer, two axes (Standards vs Spec), no same-session self-review as the only gate.
---

# PR review

Court-owned rewrite. Process inspired by Superpowers `requesting-code-review` (fresh-context) @ `b36e0829`. Dual-axis shape inspired by Matt Pocock `code-review` (Standards vs Spec) @ `3cca18b3`. **Court id is `pr-review`** — do not install Pocock/Superpowers packs or use `/code-review` as the skill name.

**Review skills should not write** (eduardo-sl). Read, report, escalate. Fixes are a different pass.

Aligns with COURT-SDLC Stage 5: review before integrate; reviewer is **fresh-context**, not the implementer session.

## Iron law

**No merge on same-session self-review alone.** Dispatch or use a fresh context with crafted inputs — never the implementer’s full chat history as the reviewer’s memory.

## Always

1. **Pin the range.** Three-dot diff vs a fixed point (`main`, merge-base, tag, SHA). Confirm the ref resolves and the diff is non-empty.
2. **Craft context only.** Description, ticket/LLD/spec link, base/head SHAs, standards sources (`AGENTS.md`, `CODING_STANDARDS.md`, CONTRIBUTING). Not the implementer transcript.
3. **Two axes, separate:**
   - **Standards** — repo conventions + judgement smells (see baseline). Documented repo rules override smells.
   - **Spec** — ticket/LLD/acceptance: missing, wrong, or scope creep. Quote the requirement.
4. **Report both axes** under `## Standards` and `## Spec`. Do not merge or rerank across axes.
5. **Act:** Critical/Important before merge; Minor can follow. Push back with reasoning if the reviewer is wrong.

## Ask first

| Topic | Why |
| --- | --- |
| No spec/ticket available | Spec axis may skip — say so explicitly |
| Skipping fresh-context because “tiny diff” | Still prefer a second context for Stage 5 |
| Reviewer wants write/merge tools | Review skill must not grow write privilege |

## Never

| Never | Why |
| --- | --- |
| Self-review as the only Stage 5 gate | COURT-SDLC fresh-context rule |
| Trust “LGTM” without reading the diff | No evidence |
| Install Superpowers/Pocock review packs beside this skill | Dual routers; Alex removed Superpowers plugin |
| Review skill that deploys, merges, or rotates secrets | eduardo-sl |

## Smell baseline (judgement only)

Repo standards win. Skip what tooling already enforces. Label as heuristic, not hard fail unless a documented standard says so:

Mysterious Name · Duplicated Code · Feature Envy · Data Clumps · Primitive Obsession · Repeated Switches · Shotgun Surgery · Divergent Change · Speculative Generality · Message Chains · Middle Man · Refused Bequest

## Court roles

| Role | Owns | Does not own |
| --- | --- | --- |
| **Heph** | Requesting fresh-context review; fixing Critical/Important | Treating self-LGTM as Stage 5 |
| **Argus** | Security axis at PR (trust boundaries); intake | Rewriting product specs in review |
| **Cedalion** | CI evidence the reviewer can cite | Product Spec axis |
| **Themis** | After-act | Blessing merge without Stage 5 |

## Red flags

- “I’ll just skim it myself in this session”
- “The implementer explained why it’s fine”
- Merging Standards pass to hide Spec fail (or the reverse)
- Reviewer opening write tools “to finish the review”

## Upstream pins

- Process: obra/superpowers `requesting-code-review` @ `b36e0829c6d0140e93cfef2ca599b1b07d4a7797`
- Dual-axis: mattpocock/skills `skills/engineering/code-review` @ `3cca18b368ae95cdbdebbff572ccafa662551015`

See [SOURCES.md](../../SOURCES.md).
