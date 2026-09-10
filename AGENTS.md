# AGENTS

This repository is the **Court shared skills home** (Alex private). It is not an application repo.

GitHub is the source of truth. Origin is inbound from GitHub ([codebase](https://cursor.com/codebase/alexderz/private-shared-skills)). Do not write skill bodies only on Origin.

**Do not use the managed Superpowers plugin.** Court process skills live under `skills/<id>/` in this repo (or will after Argus remint). Prefer sand-workflow / installed court skills that twin these ids. Load court skills from this repo by id — never from Cursor managed Superpowers.

## Skills are tools, keyed by pantheon role

| Role | Job |
| --- | --- |
| Heph | Architect and delivery |
| Cedalion | Mechanical CI, hooks, cleanup |
| Argus | Security gates and skill intake |
| Themis | Court process and SDLC |

Pick the tool that matches the role. Improvise when the work needs it. Do not remint a skill that already has an id here.

## Inventory

Authoritative table: [SOURCES.md](SOURCES.md).

Skill ids with `SKILL.md` on `main` (do not remint #16–#20):

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

Language pack (this PR; Argus clear before merge). Do not remint the Go / Python / Shell court ids above.

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

Court-owned placeholders / empty dirs (no body claim until SHA + `SKILL.md` on `main`):

- `court-linear-sdlc`
- `cursor-cloud-agents-when`

Load by id from this repo — never from managed Superpowers. Spector hygiene refine landed as PSS #20 (shell-safety FP soften + security-hardening AE1).

## Language routing

Load **at most one** language-family skill per turn. A second is allowed only for a truly mixed-language diff. Never load the catalog.
`tdd` / `verify-before-done` / `pr-review` / `security-hardening` / `yagni` may load alongside.

If `language-router` is installed and the table is ambiguous, load it first, then the one skill it names.

Pointer ids (`lang-go`, `lang-python`, `lang-shell`) exist so every identified language has a file. They do **not** count as a skill load. They route to the court ids below.

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

Stubs (no skill body — official docs only): Elixir, Scala, Haskell, Zig, Solidity, Perl, Objective-C, R, Assembly.

Frameworks (React, Spring, Rails, FastAPI, Flutter) are **not** language skills. Do not invent one mid-session.

## Intake (Argus)

Before any third-party content:

1. Do **not** install Superpowers, Pocock, or Addy as a whole pack.
2. Pin the cherry-pick SHA in [SOURCES.md](SOURCES.md).
3. Complete Argus intake.
4. No marketplace install, no auto-update, no scripts, no secrets in this repo.

Empty SHA cells mean the body must not exist yet.

## Related

- README: [README.md](README.md)
- Court SDLC (GitHub copy): [docs/COURT-SDLC.md](docs/COURT-SDLC.md)
- Linear: [Upping our coding game](https://linear.app/derzhi-grok-bot/project/upping-our-coding-game-979b787dfbb9)
- heph-forge companion: `projects/upping-coding-game/COURT-SDLC.md` (heph-forge#9)
- Issue cut: [DER-46](https://linear.app/derzhi-grok-bot/issue/DER-46/stage-0-court-sdlc-skills-home-layout)
