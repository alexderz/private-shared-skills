# Sources

Pin every third-party cherry-pick here **before** the body lands. Empty SHA cells are expected in Stage 0.

Do not install Superpowers, Pocock, or Addy whole. Argus intake before any third-party content. No auto-update.

| Skill | Upstream | SHA | License | Notes |
| --- | --- | --- | --- | --- |
| court-linear-sdlc | court-owned (this repo) | | | Court Linear SDLC skill. No vendor body. |
| cursor-cloud-agents-when | court-owned (this repo) | | | When to use Cursor Cloud Agents. No vendor body. |
| tdd | obra/superpowers (test-driven-development) | intent b36e0829c6d0140e93cfef2ca599b1b07d4a7797; merge afb2b6f4b8a6f9c62633b32a9166ca50de72c1c6 (PR #9); blob 461521bf0f16d5436dad93daf4101d346ea093b1 for skills/tdd/SKILL.md | MIT upstream / court rewrite | Argus CLEAR Spector 0; remint; compress not paste; Heph |
| pr-review | obra/superpowers (requesting-code-review) + mattpocock/skills (engineering/code-review) | superpowers b36e0829c6d0140e93cfef2ca599b1b07d4a7797; pocock 3cca18b368ae95cdbdebbff572ccafa662551015 (intent pins; body court rewrite) | MIT upstream / court rewrite | Court id pr-review (not /code-review); fresh-context + Standards/Spec; eduardo-sl no-write; Heph READY#3 |
| security-hardening | court-owned (this repo) | e207b9012d33b55014053617cf2992dca1619c70 (merge of PR #3); blob 94c76a9977d7d22542f8b26d93d818b2488d40ae for skills/security-hardening/SKILL.md | court | Argus DER-50 Always/Ask/Never compress + docs/INTAKE.md; not a vendor body |
| shell-safety | court-owned Always/Ask/Never; obra/superpowers `using-superpowers` (intent) | court-owned (body); Superpowers `b36e0829c6d0140e93cfef2ca599b1b07d4a7797` (intent pin) | court / MIT upstream intent | Argus/Cedalion. Superpowers has no dedicated shell-safety skill — `using-superpowers` (do not skip the gate) is the process pin. konstruktoid bash-secure is **reference only** — not a vendor install. No `scripts/`. Compatible with `security-hardening`. Heph READY#4 after pr-review. |
| verify-before-done | obra/superpowers (verification-before-completion) | b36e0829c6d0140e93cfef2ca599b1b07d4a7797 (intent pin; body court rewrite) | MIT upstream / court rewrite | Argus intake; compress not paste; HITL on flaky/MEDIUM; Heph READY#2 |
| yagni | TBD — pin after Argus intake | | | Do not install Superpowers/Pocock/Addy whole. |
| modern-python | trailofbits/skills (`plugins/modern-python/skills/modern-python`) | d3323cefbcf645678b8dc481de204b02ad3d02dc; blob cf5e416095b166547d383e96515377695827defd for upstream SKILL.md | CC-BY-SA 4.0 upstream / court rewrite (ShareAlike) | SKILL only; no cookiecutter, templates/, assets/, hooks/, agents/, or scripts/; Argus CLEAR conditional ~9:56pm CT Sat Sep 5; Heph |
| golang-testing | samber/cc-skills-golang (`golang-testing`) | 22c58a55a0a799b901aa251172923180bad9e010 | MIT upstream / court rewrite | SKILL only; skip evals/clawhub; Argus CLEAR conditional; Heph |
| golang-security | samber/cc-skills-golang (`golang-security`) | 22c58a55a0a799b901aa251172923180bad9e010 (intent pin; body court rewrite) | MIT upstream / court rewrite | Argus CLEAR ~9:58pm CT Sat Sep 5 (conditional); SKILL only / no evals / no scripts; pairs with golang-testing / golang-safety (separate PRs); Heph |
