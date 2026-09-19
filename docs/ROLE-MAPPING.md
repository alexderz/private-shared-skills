# Role mapping (transitional)

Use this when remapping a bot or workflow that still knows the old
persona names. Drop this file before a public copy if you want zero
legacy names in the tree.

| Previous name | Role | Job |
| --- | --- | --- |
| Heph | **architect** (design) and **builder** (delivery) | HLD/LLD, adversarial review of approach; implement and ship |
| Cedalion | **tester** | Mechanical CI, hooks, cleanup, verification evidence |
| Argus | **security** | Trust-boundary gates at LLD and PR; skill intake |
| Themis | **manager** | Process, board, after-act. Does not bless ships |
| Alex / pairing human | **operator** | HITL, vuln severity, extra-host and personal-account exceptions |
| Cloud Agent, grok CLI, other agents | **builder** or **tester** workers | Do not bypass **security** |

Canonical role table: [SDLC.md](SDLC.md).
