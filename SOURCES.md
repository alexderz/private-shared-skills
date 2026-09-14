# Sources

Pin every third-party cherry-pick here **before** the body lands. Empty
SHA cells mean no body may land.

Do not install Superpowers, Pocock, or Addy whole. **security** intake
before any third-party content. No auto-update.

| Skill | Upstream | SHA | License | Notes |
| --- | --- | --- | --- | --- |
| tracker-sdlc | first-party (this repo) | | | Tracker/board SDLC skill. No vendor body. |
| cursor-cloud-agents-when | first-party (this repo) | | | When to use Cursor Cloud Agents. No vendor body. |
| tdd | obra/superpowers (test-driven-development) | intent b36e0829c6d0140e93cfef2ca599b1b07d4a7797; merge afb2b6f4b8a6f9c62633b32a9166ca50de72c1c6 (PR #9); blob 461521bf0f16d5436dad93daf4101d346ea093b1 for skills/tdd/SKILL.md | MIT upstream / rewrite | Compress not paste |
| pr-review | obra/superpowers (requesting-code-review) + mattpocock/skills (engineering/code-review) | superpowers b36e0829c6d0140e93cfef2ca599b1b07d4a7797; pocock 3cca18b368ae95cdbdebbff572ccafa662551015 (intent pins; body rewrite) | MIT upstream / rewrite | Id `pr-review` (not `/code-review`); fresh-context + Standards/Spec; review skills do not write |
| security-hardening | first-party (this repo) | e207b9012d33b55014053617cf2992dca1619c70 (merge of PR #3); current merge 97a0469776978c9f83bf74c9dfa8bb6947d4100b (PR #20 scanner AE1); blob ca871e2d0c7a3481671bcdb8f2eb81258d2bc7e0 for skills/security-hardening/SKILL.md | first-party | Always/Ask/Never compress + docs/INTAKE.md; not a vendor body |
| shell-safety | first-party Always/Ask/Never; obra/superpowers `using-superpowers` (intent) | first-party (body); Superpowers `b36e0829c6d0140e93cfef2ca599b1b07d4a7797` (intent pin) | first-party / MIT upstream intent | Superpowers has no dedicated shell-safety skill — `using-superpowers` (do not skip the gate) is the process pin. konstruktoid bash-secure is **reference only** — not a vendor install. No `scripts/`. Compatible with `security-hardening`. |
| verify-before-done | obra/superpowers (verification-before-completion) | b36e0829c6d0140e93cfef2ca599b1b07d4a7797 (intent pin; body rewrite) | MIT upstream / rewrite | Compress not paste; HITL on flaky/MEDIUM |
| yagni | first-party restraint | first-party (body) | first-party | Thin Always/Ask/Never; ≤40 lines |
| modern-python | trailofbits/skills (`plugins/modern-python/skills/modern-python`) | d3323cefbcf645678b8dc481de204b02ad3d02dc; blob cf5e416095b166547d383e96515377695827defd for upstream SKILL.md | CC-BY-SA 4.0 upstream / rewrite (ShareAlike) | SKILL only; no cookiecutter, templates/, assets/, hooks/, agents/, or scripts/ |
| golang-testing | samber/cc-skills-golang (`golang-testing`) | 22c58a55a0a799b901aa251172923180bad9e010 | MIT upstream / rewrite | SKILL only; skip evals/clawhub |
| golang-security | samber/cc-skills-golang (`golang-security`) | 22c58a55a0a799b901aa251172923180bad9e010 (intent pin; body rewrite) | MIT upstream / rewrite | SKILL only / no evals / no scripts; pairs with golang-testing / golang-safety |
| golang-safety | samber/cc-skills-golang (`golang-safety`) | 22c58a55a0a799b901aa251172923180bad9e010 | MIT upstream / rewrite | SKILL only / no evals / no scripts/; compress not paste; pair golang-testing + golang-security |
| language-router | first-party (this repo) | first-party | first-party | Map only. Pointers do not count as a load. Cap 1–2 language skills. |
| lang-go | first-party pointer (this repo) | first-party | first-party | Routes to golang-safety / golang-testing / golang-security. Does not remint. |
| lang-python | first-party pointer (this repo) | first-party | first-party | Routes to modern-python. Does not remint. |
| lang-shell | first-party pointer (this repo) | first-party | first-party | Routes to shell-safety. Does not remint. |
| lang-rust | first-party (this repo) | first-party | first-party | Distill, not Microsoft/leonardomso dump. |
| lang-js-ts | first-party (this repo) | first-party | first-party | TS-strict default; JS is the subset. |
| lang-c | first-party (this repo) | first-party | first-party | Bounds, alloc, sanitizers. strncpy is not safe strcpy. |
| lang-cpp | first-party (this repo) | first-party | first-party | RAII, Rule of 0. Split from C. |
| lang-csharp | first-party (this repo) | first-party | first-party | Nullable, IDisposable, async. |
| lang-java | first-party (this repo) | first-party | first-party | Language only. No Spring. |
| lang-kotlin | first-party (this repo) | first-party | first-party | Null safety, coroutines. No Compose religion. |
| lang-ruby | first-party (this repo) | first-party | first-party | Language only. No Rails religion. |
| lang-php | first-party (this repo) | first-party | first-party | PHP 8+ types. No eval. No md5 passwords. |
| lang-swift | first-party (this repo) | first-party | first-party | Optionals, value types, Sendable. |
| lang-dart | first-party (this repo) | first-party | first-party | Language only. No Flutter architecture. |
| lang-sql | first-party (this repo) | first-party | first-party | Parameterize. Postgres default. |
| lang-web-markup | first-party (this repo) | first-party | first-party | HTML+CSS+a11y. One skill. |
| lang-lua | first-party (this repo) | first-party | first-party | 1-based, pairs vs ipairs. |
| lang-docker | first-party (this repo) | first-party | first-party | Non-root, pinned bases, no secrets in layers. |
| lang-terraform | first-party (this repo) | first-party | first-party | Plan is read. State is sensitive. |
| lang-makefile | first-party (this repo) | first-party | first-party | Real DAG. Quoted vars. |
| lang-powershell | first-party (this repo) | first-party | first-party | No iex. Stop on error. |
| lang-protobuf | first-party (this repo) | first-party | first-party | Fields forever. Do not edit generated stubs. |
