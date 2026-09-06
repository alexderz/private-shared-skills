---
name: shell-safety
description: use this when writing, reviewing, or running shell or bash — including agent tool commands, CI steps, one-liners, and scripts — classify Always / Ask first / Never before the command runs.
---

# Shell safety

Court-owned Always / Ask first / Never for Cedalion and Argus. Compatible with `security-hardening`: **LLM output is untrusted**; encode for the shell sink; the system prompt is not a boundary.

Process pin: Superpowers `using-superpowers` @ `b36e0829` — if this skill applies, use it; do not rationalize past the gate. **Not** a Superpowers plugin. **Not** a vendor paste. No `scripts/` in this skill dir.

konstruktoid bash-secure is **reference only** — do not install or copy that pack.

## Iron law

**No shell command runs until it is classified Always, Ask first, or Never.**

Model-chosen commands, generated scripts, and `$(...)` from untrusted text are client input.

## Always

| Rule | Why |
| --- | --- |
| Read the command before it runs | You cannot classify what you have not read |
| `set -euo pipefail` and `IFS=$'\n\t'` on scripts | Fail closed on error, unset, and pipe fail |
| Quote `"$var"` and `"$@"` | Word-split and glob are injection |
| Arrays, then `"${args[@]}"` | Do not build command strings |
| `${path:?}` before `rm` / `mv` / `chmod` on a variable path | Empty path becomes `/` or cwd |
| `[[ ]]` tests; `printf` not `echo` for untrusted text | `[` and `echo` are footguns |
| `mktemp` plus `trap` cleanup | Predictable temps; no `/tmp/foo` races |
| `cd -- "$dir" \|\| exit` | Failed cd must not continue |
| ShellCheck on committed scripts (Cedalion) | Static catch before CI |
| Allowlist / encode before model text reaches a shell | Same as security-hardening encode-for-sink |
| Workspace-scoped paths; non-interactive flags | Agents must not hang or roam |

## Ask first

| Topic | Why it is a stop |
| --- | --- |
| `sudo`, setuid, new capabilities | Privilege is a trust-boundary widen |
| `rm -rf` / wipe outside the repo or this task's `/tmp` | Blast radius |
| `curl \| sh`, `wget \| bash`, `npx` / vendor installers | INTAKE: clone, do not run installers |
| Force-push, history rewrite, deleting shared remote branches | Irreversible git |
| Writes under `~`, `/etc`, or credential dirs | Secrets and host config |
| New network egress or piping remote content | New trust |
| `set +e` / disabling strict mode for a whole script | Fail-open |
| Running an opaque script you have not read | Same as untrusted client input |

Record the decision. Do not self-except.

## Never

| Never | Why |
| --- | --- |
| `eval`, `bash -c`, or `source` of user or model text | Injection; security-hardening Never |
| `curl … \| sh` / unpinned remote scripts | Supply chain |
| `rm -rf /`, `rm -rf "$var"` without `${var:?}`, unquoted destructive globs | Host wipe |
| Secrets in scripts, git, or command lines that will be logged | History is forever |
| Install Superpowers / Pocock / Addy packs for this skill | Dual routers; Alex removed the plugin |
| Copy `scripts/` into a court skill dir | INTAKE quarantine |
| Alex-pc4 / Windows without Alex approval | Host lock |
| Bank / Gmail / LastPass via shell | Out of agent scope |
| Bind `0.0.0.0` or public mesh from a one-liner | Network becomes the client |
| `chmod 777` / world-writable secrets | Data-class fail |

Court host and account locks are **Never**, not Ask first.

## Court roles

| Role | Owns | Does not own |
| --- | --- | --- |
| **Argus** | This gate at LLD/PR when shell touches a boundary; skill intake | Writing Cedalion CI yaml |
| **Cedalion** | shellcheck hooks when `.sh` appears | Skipping Argus because CI is green |
| **Heph** | Classifying commands before they run | Self-excepting “just this once” |
| **Themis** | After-act | Blessing a ship that skipped the gate |

Workers do not bypass. A green ShellCheck is not an Argus clear.

## Red flags

- “The model said the command is safe”
- “I’ll pipe it to bash just this once”
- “sudo is faster than asking”
- “Empty path is fine”
- “Install the Superpowers plugin to get shell safety”
- “Alex-pc4 is convenient”

Stop. Classify. Ask or never — do not run.

## Upstream pin

Intent: obra/superpowers `using-superpowers` @ `b36e0829c6d0140e93cfef2ca599b1b07d4a7797`. Body is court-owned. See [SOURCES.md](../../SOURCES.md).
