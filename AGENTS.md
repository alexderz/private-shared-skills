# AGENTS

This repository is a **shared skills home**. It is not an application
repo.

Git is the source of truth. Do not write skill bodies only on a local or
vendor mirror.

**Do not use the managed Superpowers plugin.** Process skills live under
`skills/<id>/` in this repo. Load skills from this repo by id — never
from a managed Superpowers pack.

## Skills are tools, keyed by role

| Role | Job |
| --- | --- |
| architect | Design, HLD/LLD, adversarial review of approach |
| builder | Implement and ship |
| tester | Mechanical CI, hooks, cleanup |
| security | Security gates and skill intake |
| manager | Process, SDLC after-act, land path (PR vs merge-and-delete) |
| operator | HITL, exceptions, vuln severity |

Pick the tool that matches the role. Improvise when the work needs it.
Do not remint a skill that already has an id here.

Per work item: mint a **clean builder** and a **clean verifier** on the
first pass; **resume** those subagents for later builds and verifies of
the same item. Do not reuse the builder as the verifier.

Branch items off **project-main** (`integrate/<slug>`), land each
merge-ready item there (serialized), then land project-main on trunk.
**manager** picks PR vs merge-and-delete from how many items are in
flight. Full rules: [docs/SDLC.md](docs/SDLC.md) (Project-main,
Subagents per work item).

## Inventory

Authoritative table: [SOURCES.md](SOURCES.md). Bundles: [README.md](README.md).

Skill ids with `SKILL.md` (do not remint without a new **security** cut):

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

Language pack. Do not remint the Go / Python / Shell ids above.

- `language-router`
- `lang-go` (pointer → one of `golang-safety` / `golang-testing` / `golang-security`)
- `lang-python` (pointer → `modern-python`)
- `lang-shell` (pointer → `shell-safety`)
- `lang-rust`
- `lang-js-ts`
- `lang-c`
- `lang-cpp`
- `lang-csharp`
- `lang-java`
- `lang-kotlin`
- `lang-ruby`
- `lang-php`
- `lang-swift`
- `lang-dart`
- `lang-sql`
- `lang-web-markup`
- `lang-lua`
- `lang-docker`
- `lang-terraform`
- `lang-makefile`
- `lang-powershell`
- `lang-protobuf`

First-party placeholders / empty dirs (no body claim until SHA +
`SKILL.md` on `main`):

- `tracker-sdlc`
- `cursor-cloud-agents-when`

Load by id from this repo — never from managed Superpowers.

## Language routing

Load **at most one** language-family skill per turn. A second is allowed
only for a truly mixed-language diff. Never load the catalog.
`tdd` / `verify-before-done` / `pr-review` / `security-hardening` /
`yagni` may load alongside.

If `language-router` is installed and the table is ambiguous, load it
first, then the one skill it names.

Pointer ids (`lang-go`, `lang-python`, `lang-shell`) exist so every
identified language has a file. They do **not** count as a skill load.
They route to the ids below.

| Files / signals | Load |
| --- | --- |
| `*.go`, `go.mod` | `golang-safety` by default. `golang-testing` when writing tests. `golang-security` when the change touches input, auth, SQL, files, subprocesses, or crypto. Pick **one**. Optional pointer: `lang-go`. |
| `*.py`, `pyproject.toml`, `uv.lock` | `modern-python`. Optional pointer: `lang-python`. |
| `*.sh`, `*.bash`, shebang bash/sh, agent shell | `shell-safety`. Optional pointer: `lang-shell`. |
| `*.rs`, `Cargo.toml` | `lang-rust` |
| `*.ts`, `*.tsx`, `*.js`, `*.mjs`, `*.cjs`, `tsconfig.json`, `package.json` | `lang-js-ts` |
| `*.c`, `*.h` and no C++ files | `lang-c` |
| `*.cpp`, `*.cc`, `*.cxx`, `*.hpp` | `lang-cpp` |
| `*.cs`, `*.csproj`, `*.sln` | `lang-csharp` |
| `*.java`, `pom.xml`, `build.gradle` | `lang-java` |
| `*.kt`, `*.kts` | `lang-kotlin` |
| `*.rb`, `Gemfile` | `lang-ruby` |
| `*.php`, `composer.json` | `lang-php` |
| `*.swift`, `Package.swift` | `lang-swift` |
| `*.dart`, `pubspec.yaml` | `lang-dart` |
| `*.sql` | `lang-sql` |
| `*.html`, `*.htm`, `*.css`, `*.scss` | `lang-web-markup` |
| `Dockerfile`, `*.dockerfile`, `compose.y*ml` | `lang-docker` |
| `*.tf`, `*.hcl` | `lang-terraform` |
| `Makefile`, `GNUmakefile` | `lang-makefile` |
| `*.ps1`, `*.psm1` | `lang-powershell` |
| `*.proto` | `lang-protobuf` |
| `*.lua` | `lang-lua` |

Stubs (no skill body — official docs only): Elixir, Scala, Haskell, Zig,
Solidity, Perl, Objective-C, R, Assembly.

Frameworks (React, Spring, Rails, FastAPI, Flutter) are **not** language
skills. Do not invent one mid-session.

## Intake (security)

Before any third-party content:

1. Do **not** install Superpowers, Pocock, or Addy as a whole pack.
2. Pin the cherry-pick SHA in [SOURCES.md](SOURCES.md).
3. Complete **security** intake ([docs/INTAKE.md](docs/INTAKE.md)).
4. No marketplace install, no auto-update, no scripts, no secrets in this
   repo.

Empty SHA cells mean the body must not exist yet.

## Related

- README: [README.md](README.md)
- SDLC: [docs/SDLC.md](docs/SDLC.md)
- Role mapping (transitional): [docs/ROLE-MAPPING.md](docs/ROLE-MAPPING.md)
