---
name: tdd
description: use this when implementing any feature or bugfix — write a failing test first, watch it fail for the right reason, then minimal code to green, then refactor.
---

# Test-driven development

Court-owned rewrite inspired by Superpowers TDD (obra/superpowers `test-driven-development` @ `b36e0829`). **Not** a managed Superpowers plugin install. **Not** a vendor paste. Argus intake cleared SkillSpector static 0 issues on the upstream skill dir.

**Heph owns delivery with this skill.** Cedalion owns CI hooks that keep tests runnable. Argus does not rewrite this body without a new intake.

## Iron law

**No production code without a failing test first.**

Wrote implementation before the test? **Delete it and restart.** Do not keep it as “reference,” do not “adapt” it while writing tests, do not glance at it. Fresh from the failing test.

## Always

| Step | Do | Prove |
| --- | --- | --- |
| RED | One minimal failing test for the next behavior | Run it — it must fail |
| Watch | Confirm the failure is for the **right reason** | Wrong fail → fix the test, not the product |
| GREEN | Smallest code that makes that test pass | All relevant tests green |
| REFACTOR | Clean structure only while staying green | Tests still green after each tidy |

Text loop is enough: red → watch → green → refactor → next. Skip huge ASCII/dot diagrams.

## Soften (Ask first / exceptions)

Stop and ask (Alex, or Themis on process) before skipping the iron law for:

| Exception | Why it is a stop |
| --- | --- |
| One-line rename / import path / dead-code delete with no behavior change | Ritual thrash; still prefer a quick compile/typecheck |
| Generated code / lockfiles / vendored blobs | Not hand-authored product logic |
| Throwaway spike you will delete | Mark it throwaway; do not ship without tests |
| Pure config with no executable behavior | Prefer a smoke check if the config is load-bearing |

“Just this once” for real behavior is **not** an exception. Rationalizing past the iron law fails the skill.

## Never

| Never | Why |
| --- | --- |
| Code-first “then I’ll add tests” | You already violated the iron law |
| Keep deleted code-first drafts nearby | They coach the next pass |
| Horizontal feature slices without a failing seam test | Green theater |
| Claiming done without watching red then green | No evidence |
| Installing Superpowers / marketplace TDD packs beside this skill | Dual routers; Alex removed the plugin |

## Good vs bad

**Good:** test names the behavior; fail message matches the missing behavior; green change is tiny; refactor does not add features.

**Bad:** test asserts implementation details only; fail is import/syntax noise you ignored; green is a rewrite; refactor smuggles new behavior.

## Court roles

| Role | Owns | Does not own |
| --- | --- | --- |
| **Heph** | Using this loop on product work | Skipping Argus intake for other skills |
| **Cedalion** | Keeping test/fmt CI green | Softening the iron law in YAML |
| **Argus** | Intake/PR gate if this file changes materially | Day-to-day TDD coaching |
| **Themis** | After-act | Blessing code-first ships |

## Red flags

- “I already know what the code should look like”
- “The test is hard; I’ll code first”
- “It failed, but not for the reason I expected — ship anyway”
- “Managed Superpowers already covers this”
- “Rename doesn’t need a test” used to skip real behavior changes

All of these fail the skill. Stop. Ask or restart from a failing test.

## Upstream pin

Intent pin (body is court rewrite): obra/superpowers @ `b36e0829c6d0140e93cfef2ca599b1b07d4a7797`. See [SOURCES.md](../../SOURCES.md).
