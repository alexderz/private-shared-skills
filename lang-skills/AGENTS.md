# AGENTS.md block — language router (merge into court AGENTS.md)

Do not remint existing ids. Load by id from this repo.

## Language routing

Load **at most one** language-family skill per turn. A second is allowed
only for a truly mixed-language diff. Never load the catalog.
`tdd` / `verify-before-done` / `pr-review` / `security-hardening` / `yagni`
may load alongside.

If `language-router` is installed and the table is ambiguous, load it
first, then the one skill it names.

Pointer ids (`lang-go`, `lang-python`, `lang-shell`) exist so every
identified language has a file. They do **not** count as a skill load.
They route to the court ids below.

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
