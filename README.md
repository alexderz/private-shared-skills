# Shared coding skills

Skills here are **tools**, not a marketplace dump. Coding agents pick the
right tool for the job. SDLC work is keyed by **role** (`architect`,
`builder`, `tester`, `security`, `manager`, `operator`) — not by a named
pantheon.

Git is the source of truth. A local or vendor mirror may follow. Do not
treat a mirror as an independent write path for skill bodies.

## Roles

| Role | Job |
| --- | --- |
| **architect** | Design, HLD/LLD, adversarial review of approach |
| **builder** | Implement and ship |
| **tester** | Mechanical CI, hooks, cleanup |
| **security** | Security gates across the SDLC, including skill intake |
| **manager** | Process and SDLC after-act. Does not bless ships |
| **operator** | Human in the loop: exceptions, vuln severity, extra hosts |

Improvise beyond predefinition when the work needs it. Do not remint a
skill that already lives here.

Bot / workflow owners: previous pantheon names map in
[docs/ROLE-MAPPING.md](docs/ROLE-MAPPING.md).

## Bundles

There is no plugin manifest yet. For a public copy, these are the
natural install groups:

| Bundle | Skills | When |
| --- | --- | --- |
| **sdlc-process** | `tdd`, `verify-before-done`, `pr-review`, `yagni`, `security-hardening`, `shell-safety` | Any coding repo |
| **languages** | `language-router`, `lang-*`, `golang-safety`, `golang-testing`, `golang-security`, `modern-python` | Writing or reviewing code. Load **at most one** language-family skill per turn |
| **optional / empty** | `tracker-sdlc`, `cursor-cloud-agents-when` | Placeholders. No `SKILL.md` yet. Drop or fill before a public copy |

`lang-go`, `lang-python`, and `lang-shell` are **pointers**. They do not
count as a skill load. They route to `golang-*`, `modern-python`, and
`shell-safety`. `shell-safety` sits in **sdlc-process** because every
agent shell is in scope; `lang-shell` only points at it.

Authoritative pins: [SOURCES.md](SOURCES.md). Routing table:
[skills/language-router/SKILL.md](skills/language-router/SKILL.md).

## Intake rules (security first)

Placeholders remain for empty ids. Bodies land via **security** intake
and a compress, not a vendor paste.

- Do **not** install Superpowers, Pocock, or Addy as a whole pack.
- Pin every third-party cherry-pick **SHA** in [SOURCES.md](SOURCES.md).
  Empty SHA cells mean the body is not here yet.
- **security** intake before any third-party content lands in this repo.
- **No auto-update.** No marketplace install. No scripts. No secrets.
- First-party skills (`tracker-sdlc`, `cursor-cloud-agents-when`,
  language guides) are written here; they are not vendor copies.

Directories under `skills/<id>/` are placeholders (`.gitkeep` only) until
a body lands.

## Skill ids

See [SOURCES.md](SOURCES.md) for upstream, SHA, license, and notes.

### sdlc-process

| Id | Ownership |
| --- | --- |
| `tdd` | Rewrite of Superpowers TDD (MIT) |
| `verify-before-done` | Rewrite of Superpowers verification-before-completion (MIT) |
| `pr-review` | Rewrite of Superpowers requesting-code-review + Pocock dual-axis (MIT) |
| `yagni` | First-party restraint |
| `security-hardening` | First-party Always/Ask/Never |
| `shell-safety` | First-party Always/Ask/Never; Superpowers `using-superpowers` intent pin |

### languages

| Id | Ownership |
| --- | --- |
| `language-router` | First-party map |
| `lang-go` / `lang-python` / `lang-shell` | First-party pointers |
| `golang-safety` / `golang-testing` / `golang-security` | Rewrite of samber/cc-skills-golang (MIT) |
| `modern-python` | Rewrite of trailofbits/skills (CC-BY-SA 4.0) |
| `lang-rust`, `lang-js-ts`, `lang-c`, `lang-cpp`, `lang-csharp`, `lang-java`, `lang-kotlin`, `lang-ruby`, `lang-php`, `lang-swift`, `lang-dart`, `lang-sql`, `lang-web-markup`, `lang-lua`, `lang-docker`, `lang-terraform`, `lang-makefile`, `lang-powershell`, `lang-protobuf` | First-party language guides |

### optional / empty

| Id | Ownership |
| --- | --- |
| `tracker-sdlc` | First-party placeholder |
| `cursor-cloud-agents-when` | First-party placeholder (Cursor-specific) |

## Related

- SDLC: [docs/SDLC.md](docs/SDLC.md)
- Architecture: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)
- Intake: [docs/INTAKE.md](docs/INTAKE.md)
- First cherry-pick candidates: [docs/CHERRY-PICK-CANDIDATES.md](docs/CHERRY-PICK-CANDIDATES.md)
- CI hooks (fmt/lint): [docs/CI-HOOKS-PLAN.md](docs/CI-HOOKS-PLAN.md)

Agents landing in this repo: start at [AGENTS.md](AGENTS.md). Claude
Code reads [CLAUDE.md](CLAUDE.md), which only points at AGENTS.md.
