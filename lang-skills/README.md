# Language guides + router (court drop-in)

Full agentic guides for every identified language, plus a router so the
agent loads **at most one or two**. Written for
`alexderz/private-shared-skills` after Argus intake.

No `scripts/`. No marketplace install. No remint of existing court ids.

## What "full agentic set" means

Every `lang-*` body has the same skeleton:

1. Iron law
2. Tooling / verify-before-done commands
3. Idioms a linter misses
4. Errors
5. Concurrency (or explicit N/A)
6. Testing
7. PR review checklist
8. Security footguns
9. Always / Ask first / Never
10. Red flags

Pointers for Go / Python / Shell exist so every identified language has
a file. They **route** to `golang-*`, `modern-python`, and `shell-safety`.
They do not count as a second skill load.

## Inventory

| Id | Kind |
| --- | --- |
| `language-router` | map |
| `lang-go` | pointer → court Go ids |
| `lang-python` | pointer → `modern-python` |
| `lang-shell` | pointer → `shell-safety` |
| `lang-rust` | full guide |
| `lang-js-ts` | full guide (JS+TS) |
| `lang-c` | full guide |
| `lang-cpp` | full guide |
| `lang-csharp` | full guide |
| `lang-java` | full guide |
| `lang-kotlin` | full guide |
| `lang-ruby` | full guide |
| `lang-php` | full guide |
| `lang-swift` | full guide |
| `lang-dart` | full guide |
| `lang-sql` | full guide |
| `lang-web-markup` | full guide (HTML+CSS) |
| `lang-lua` | full guide |
| `lang-docker` | full guide |
| `lang-terraform` | full guide |
| `lang-makefile` | full guide |
| `lang-powershell` | full guide |
| `lang-protobuf` | full guide |

Stubs (router only, no body): Elixir, Scala, Haskell, Zig, Solidity,
Perl, Objective-C, R, Assembly.

Human index: [guides/INDEX.md](guides/INDEX.md).

## Cap

- One language-family skill per turn.
- A second only for a mixed diff (Go+SQL, TS+CSS, proto+host).
- Process skills (`tdd`, `verify-before-done`, `pr-review`,
  `security-hardening`, `yagni`) may ride along.
- Pointer files do not count toward the cap.

## Intake

1. Append `docs/SOURCES-rows.md` to court `SOURCES.md` **before** bodies.
2. Copy `skills/*` into the court `skills/` tree.
3. Merge `AGENTS.md` into court `AGENTS.md`.
4. Argus clear. Do not remint `golang-*` / `modern-python` / `shell-safety`.

First slice if you do not want all 23 dirs at once:

`language-router` + `lang-go` + `lang-python` + `lang-shell` + `lang-rust`
+ `lang-js-ts` + `lang-sql` + `lang-lua`.
