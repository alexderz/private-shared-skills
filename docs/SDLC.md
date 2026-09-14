# SDLC

Shared software process for work that uses this skills home. Git holds
durable artifacts. The issue tracker is the board. Pull requests cite a
ticket ID when the project uses tickets.

## Roles

Skills are **tools**, keyed by role. Improvise when the work needs it.
Do not remint a skill that already has an id here.

| Role | Job |
| --- | --- |
| **architect** | Design, HLD/LLD, adversarial review of approach |
| **builder** | Implement and ship |
| **tester** | Mechanical CI, hooks, cleanup, verification evidence |
| **security** | Gates at LLD (trust boundaries) and PR, plus skill intake — not only a monthly vuln pass |
| **manager** | Process and board after-act. Does not bless ships |
| **operator** | Human in the loop: exceptions, vuln severity, extra hosts, personal accounts |

Workers (coding agents, CI bots) act as **builder** or **tester**. They
do not bypass **security**.

## Hierarchy (issue tracker)

| Layer | Typical object | Meaning |
| --- | --- | --- |
| Track | Project | One product or process track |
| Chunk | Parent issue labeled Epic | Discrete, parallel slice |
| Work item | Issue labeled Task or Bug | Implementable unit; may nest sub-issues |

After-act **manager** with the operator's timezone. The board is the
tracker; git holds the files. Designs live in git from onset — do not
keep HLD/LLD only on a local mirror.

## Stages

### Stage −1 Repo — git ready + agents aware

Before Stage 0 HLD:

- Repo or subdir exists (private as needed).
- README / AGENTS stub so agents who need access are aware.
- **tester** watch if applicable.
- **Designs live in git from onset.**

### Stage 0 HLD

Publish HLD on the tracker project and a git copy. Lock hierarchy,
persistence, and worker rules.

### Stage 1 PoC

Only if needed. Evidence in git.

### Stage 2 LLD

Document + git copy. Templates, status mapping, bot after-act, path
conventions.

**security gate (trust boundaries):** before groom/implement, **security**
reviews the LLD for trust boundaries (authn/z, secrets, egress, data
class, who may write what). This is a gate, not a later monthly note. Do
not skip to Stage 4 without it when the change touches a boundary.

### Stage 3 Groom

Break into Tasks/Bugs with acceptance criteria and an LLD link.

### Stage 4 — loop until DoD

Implement and test at max safe parallelism. **Do not exit Stage 4 after
one pass.** Loop implement → test → fix until the ticket Definition of
Done is actually met.

DoD includes: acceptance on the ticket, tests/verification evidence, PR
cites a ticket ID when the project uses tickets, no silent scope leftover.
Notify **landed+verified** — not “pushed” and not “LGTM without evidence.”

**Skill-home DoD (this repo):** any skill-body diff must match the pinned
SHA in [SOURCES.md](../SOURCES.md) for that id. Empty SHA means no body
may land. Remote agent PRs into this repo still pass **security intake**.
Workers **do not bypass** intake, SHA pins, or security LLD/PR gates.

### Stage 5 Review gate (fresh-context, before integrate)

Review **before** Stage 6 integrate. The reviewer is a **fresh-context**
session — not the implementer session that wrote the diff. Same-session
self-review does not count.

Reviewer approves only if the PR meets the ticket + LLD **and** the
**security** PR gate (intake, SHA pins, trust-boundary deltas). Security
at PR is a gate, not deferred to Stage 8 monthly.

### Stage 6 Integration

Only after Stage 5 fresh-context review. More Tasks, not a special
ceremony.

### Stage 7 Release

Coherent chunk. CHANGELOG in the repo.

### Stage 8 Monthly

Vuln / updates / new solutions review. Recurrence note only until
**manager** / **operator** cut a Task. No watcher, no cron required.

Monthly is **not** the security gate. **security** already gated trust
boundaries at LLD and the PR. Monthly is cadence review of
vulns/updates/new solutions, not a substitute for those gates.

## Workers

| Worker | When |
| --- | --- |
| Remote coding agent | Remote repo / PR work |
| Local coding CLI | Box-local gated builds |
| Local mirror | Inbound copy of git. Not the design source of truth |

**architect** adversarial-reviews other agents’ tools when the work needs
it. **tester** owns mechanical CI/hooks. **security** owns gates (LLD
trust boundaries + PR) and skill intake. **manager** after-acts the
board; does not bless before ship.

**Workers do not bypass security.** A remote or local agent PR into this
skills home still requires intake and SHA-pin match. Worker choice is not
an exemption.

Notify only when work is **landed and verified**.

## Git designs from onset

- HLD, LLD, PoC notes, decisions, changelogs, and this SDLC land in
  **git** from Stage −1.
- A local or vendor mirror may follow. Do not treat a mirror as an
  independent write path for designs.

## Skill table

Ids and ownership: [SOURCES.md](../SOURCES.md). Empty SHA = no body yet.
Do not install Superpowers / Pocock / Addy whole. No marketplace install.
No auto-update.

| Skill | Role | Notes |
| --- | --- | --- |
| `tracker-sdlc` | manager / architect | Empty dir until a first-party body |
| `cursor-cloud-agents-when` | architect | Empty dir until a first-party body |
| `tdd` | builder | Fail-first |
| `pr-review` | architect / security | Fresh-context; Standards vs Spec |
| `security-hardening` | security | Always / Ask first / Never |
| `shell-safety` | security / tester | Classify before a command runs |
| `verify-before-done` | builder / tester | Stage 4 / notify landed+verified |
| `yagni` | architect / builder | Smallest change that meets this Task |
| `modern-python` | builder | uv / ruff / ty / pytest |
| `golang-testing` | builder / tester | Go test shape |
| `golang-safety` | builder | Nil / slice / numeric traps |
| `golang-security` | security / builder | Exploitable Go issues |
| `language-router` | builder | Pick at most one language-family skill |
| `lang-*` | builder | Pointers or language guides |

Pin SHAs in [SOURCES.md](../SOURCES.md). **security** intake before any
vendor content. See [INTAKE.md](INTAKE.md).
