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
| **manager** | Process, board after-act, and land path (PR vs merge-and-delete). Does not bless ships |
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

Break into Tasks/Bugs with acceptance criteria and an LLD link. Name the
**project-main** branch for this chunk (see [Project-main](#project-main-intermediate-integration)).
**manager** sets the land path for the chunk: PR into project-main, or
merge-and-delete the item branch.

### Stage 4 — loop until merge-ready

Implement and test at max safe parallelism. **Do not exit Stage 4 after
one pass.** Loop implement → test → fix until the ticket Definition of
Done is actually met. Use **one builder subagent and one verifier
subagent per work item** for that loop (see [Subagents per work
item](#subagents-per-work-item)).

Each item **branches off project-main**, not off a pile of sibling
item branches. Independent items may **build** in parallel. When an item
is merge-ready (DoD + Stage 5), **land it on project-main** — do not
stockpile finished-but-unmerged branches for a batch integrate. Lands
are one at a time.

DoD includes: acceptance on the ticket, tests/verification evidence,
land path cites a ticket ID when the project uses tickets, no silent
scope leftover. Notify **landed+verified** on **project-main** — not
“pushed to an item branch” and not “LGTM without evidence.”

**Skill-home DoD (this repo):** any skill-body diff must match the pinned
SHA in [SOURCES.md](../SOURCES.md) for that id. Empty SHA means no body
may land. Remote agent PRs into this repo still pass **security intake**.
Workers **do not bypass** intake, SHA pins, or security LLD/PR gates.

### Stage 5 Review gate (before land on project-main)

Review **before** the item lands on project-main. The reviewer is **not**
the builder who wrote the diff. Same-session self-review does not count.
Merge-and-delete does **not** skip this gate.

First review of this item: mint a **clean reviewer**. Later review rounds
on the same item (after fixes): **resume that reviewer**. Do not mint a
new reviewer each round, and do not feed it the builder’s transcript.

Reviewer approves only if the item meets the ticket + LLD **and** the
**security** gate (intake, SHA pins, trust-boundary deltas). Security at
land is a gate, not deferred to Stage 8 monthly. Diff range is versus
**project-main**, not versus trunk.

### Stage 6 — land project-main on trunk

After the chunk’s items are on project-main, merge project-main to the
repo’s protected default (**trunk**, usually `main`). That is the
coherent integrate. CHANGELOG may wait for Stage 7. Delete project-main
after it is on trunk (or if **manager** cancels the chunk).

### Stage 7 Release

Coherent chunk on trunk. CHANGELOG in the repo.

### Stage 8 Monthly

Vuln / updates / new solutions review. Recurrence note only until
**manager** / **operator** cut a Task. No watcher, no cron required.

Monthly is **not** the security gate. **security** already gated trust
boundaries at LLD and the PR. Monthly is cadence review of
vulns/updates/new solutions, not a substitute for those gates.

## Project-main (intermediate integration)

Do not build a stack of isolated item branches and integrate them once
at the end. Integrate **each** merge-ready item onto a temporary
project branch, then land that branch on trunk as the chunk.

| Branch | What | Lifetime |
| --- | --- | --- |
| **trunk** | Repo default (`main` / protected). Release target. | Permanent |
| **project-main** | Integration branch for this project or chunk. Tip is the latest landed items. | Stage 3 → Stage 6 |
| **item branch** | One work item. Created from current project-main. | Until that item lands |

Name project-main `integrate/<project-or-chunk-slug>` unless the repo
already has a convention. Create it from trunk at Stage 3. Builders
**branch off the current project-main tip.** After an item lands, in-flight
builders rebase or merge project-main and resume; the verifier re-runs.

**Lands on project-main are serialized.** Builds may run in parallel;
only one item merges at a time. The landing builder de-conflicts against
the current project-main tip (resume that builder; then resume its
verifier). Do not race two merges onto project-main.

### Land path (manager)

**manager** chooses, and may change when parallelism changes:

| Situation | Default |
| --- | --- |
| Two or more items in flight on this project-main | **PR** into project-main (queue is visible; conflicts show on the PR) |
| One item at a time | **Merge and delete** the item branch after Stage 5 |

PRs are allowed and useful. They are not mandatory when manager has
chosen merge-and-delete. Builders follow the current manager call; they
do not pick a path that contradicts it. Ticket ID goes on the PR or the
merge commit.

**Never**

- Branch an item off trunk or off another item branch while project-main
  exists.
- Leave merge-ready items unmerged so they can “integrate together later.”
- Skip Stage 5 because the land path is merge-and-delete.
- Force-push project-main to win a race (shared branch; **shell-safety**
  Ask first).
- Treat a green item branch as landed+verified. Landed means **on
  project-main**.

## Subagents per work item

A **work item** is one Task, Bug, or PR — one implementable unit. The
orchestrator (manager session, parent agent, or workflow) keeps two ids
per item: `builder_id` and `verifier_id`. Stage 5 adds `reviewer_id`.
Those three must not be the same agent.

| Role | First pass on this item | Later passes on this item |
| --- | --- | --- |
| **builder** | Mint a **clean** subagent. Store `builder_id`. | **Resume** `builder_id`. Prompt only the delta. |
| **verifier** | Mint a **clean** subagent. Never the builder. Store `verifier_id`. | **Resume** `verifier_id`. Prompt only the delta. Re-run proving commands. |
| **reviewer** (Stage 5) | Mint a **clean** subagent. Never the builder. Store `reviewer_id`. | **Resume** `reviewer_id` for re-review of the same item. |

**Clean** means an empty transcript except the crafted task: ticket /
LLD / acceptance, paths, and standards. Do not seed it with another
role’s chat, and do not use the orchestrator as the builder or verifier.

**Resume** means continue that subagent (`resume_from` that id, or the
host’s equivalent). The agent already read the item. Do not re-paste the
spec, the tree, or prior logs it produced. Send what changed, what
failed, and what to do next.

**Never**

- Builder verifies (or reviewer-reviews) its own work as the only gate.
- Verifier or reviewer is given the builder’s transcript as memory.
- An item’s builder / verifier / reviewer is reused on a **different**
  item.
- A new builder or verifier is minted on every Stage 4 loop when the
  previous one for this item is still resumable.

**Fallback.** If resume fails (expired, quota, host error), mint a new
clean agent of the **same role** for this item and replace the stored
id. Pass a short handoff (paths, decisions, open failures) — still not
the other role’s transcript.

**Overflow.** If a resumed transcript is too large to be useful, replace
that role’s agent the same way (clean mint + short handoff). Do not
rotate roles to “save” context.

Orchestrators that spawn in parallel still mint **one pair per item**,
not one pair per loop. Independent items get independent pairs.

### Spawn prompts (pack vs point)

On each **mint**, the orchestrator (**manager**) picks the cheaper prompt
for that child. There is no default that is always right.

| Mode | Prompt | Child does |
| --- | --- | --- |
| **Pack** | Comprehensive: ticket/LLD, the skill bodies it will need, and any MCP tool schemas it will call. Name the ids packed. Tell it **not** to reload those. | Work. Do not `read_file` the packed skills or re-fetch packed MCP schemas. |
| **Point** | High-level task + which skill ids / MCP servers to load (or the host default: “read the matching `SKILL.md`”). | Load those itself. Still **at most one** language-family skill. |

**Pack** when the parent already has the bodies, the child will use most
of them, and one round-trip to re-read would cost more than inlining.
Typical: first builder mint with one language skill + `tdd` / `yagni`;
verifier mint with `verify-before-done` plus the proving commands;
reviewer mint with `pr-review` plus the range vs project-main.

**Point** when several skills or MCP servers might apply, the parent
does not already have the bodies, or only a thin slice of a large guide
matters. Do not load a catalog into the parent just to pack it.

**Resume** is always delta-only. Do not re-pack skills or MCP guides
already in that child’s transcript. If a new skill or tool is required
on this pass, pack that slice or name it — not the whole set again.

**Never**

- Pack the language catalog, every MCP server, or skills for a
  different role “just in case.”
- Pack a skill and also tell the child to go read the same file.
- Point at “load whatever you need” with no ids when the parent already
  knows the one or two that apply.

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
| `pr-review` | architect / security | Reviewer ≠ builder; vs project-main; resume later rounds; Standards vs Spec |
| `security-hardening` | security | Always / Ask first / Never |
| `shell-safety` | security / tester | Classify before a command runs |
| `verify-before-done` | builder / tester | Stage 4 / notify landed+verified; resume verifier |
| `yagni` | architect / builder | Smallest change that meets this Task |
| `modern-python` | builder | uv / ruff / ty / pytest |
| `golang-testing` | builder / tester | Go test shape |
| `golang-safety` | builder | Nil / slice / numeric traps |
| `golang-security` | security / builder | Exploitable Go issues |
| `language-router` | builder | Pick at most one language-family skill |
| `lang-*` | builder | Pointers or language guides |

Pin SHAs in [SOURCES.md](../SOURCES.md). **security** intake before any
vendor content. See [INTAKE.md](INTAKE.md).
