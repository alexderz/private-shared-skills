---
name: modern-python
description: use this when creating, configuring, or migrating a Python project or standalone script — uv, ruff, ty, pytest; do not reach for pip, Poetry, mypy, or black unless the operator keeps legacy.
---

# Modern Python

Rewrite of Trail of Bits `modern-python` (trailofbits/skills @ `d3323cef`). **CC-BY-SA 4.0** upstream — this file is adapted, not a verbatim paste. License: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Upstream SKILL: [plugins/modern-python/skills/modern-python/SKILL.md](https://github.com/trailofbits/skills/blob/d3323cefbcf645678b8dc481de204b02ad3d02dc/plugins/modern-python/skills/modern-python/SKILL.md).

Id: `modern-python`. **SKILL.md only.** Do not copy cookiecutter, `templates/`, `assets/`, `hooks/`, `agents/`, or `scripts/`. **Not** a marketplace plugin. **Not** Superpowers / Pocock / Addy.

**security** CLEAR was **conditional**: this body only, under those exclusions.

## Iron law

**`uv add` / `uv remove` manage deps. `uv run` runs commands. Do not activate venvs or hand-edit dependency lists.**

Python ≥ 3.11. New work uses uv + ruff + ty + pytest. Legacy stacks stay only when the operator (or the pairing human) says keep them.

## Always

| Rule | Why |
| --- | --- |
| `uv add` / `uv remove` / `uv sync` | `uv.lock` is the truth; do not `uv pip install` |
| `uv run <cmd>` | No `source .venv/bin/activate` |
| `[dependency-groups]` (PEP 735) for lint/test/docs | Not `[project.optional-dependencies]` for dev tools |
| `src/` layout for packages; `requires-python = ">=3.11"` | Matches the tool pin |
| ruff for lint **and** format (`select = ["ALL"]` + explicit ignores) | Replaces flake8 / black / isort / pyupgrade |
| ty for types (`[tool.ty.environment]` `python-version`) | Replaces mypy / pyright |
| pytest + coverage floor (80%+) | `unittest` is not the default |
| Commit `uv.lock` | Reproducible installs |
| PEP 723 inline metadata for single-file scripts | No `requirements.txt` for a script |
| This `SKILL.md` only | **security** quarantine: no upstream extras |

## Ask first

| Topic | Why it is a stop |
| --- | --- |
| Keep pip / Poetry / mypy / black / pyright | User may own that workflow |
| Python < 3.11 | This pin does not target it |
| Migrate a working production tree | Blast radius; confirm before deleting `requirements.txt` / `setup.py` |
| Cookiecutter or trailofbits/cookiecutter-python | **Excluded** from this remint — not the first-party path |
| prek / pre-commit hook installers | Upstream hooks are quarantined; **tester** owns CI |
| `uv pip install` as an escape hatch | Bypasses the lockfile |
| Publish / extra indexes / private registries | Trust + credentials |

Do not self-except.

## Never

| Never | Why |
| --- | --- |
| Copy `templates/`, `assets/`, `hooks/`, `agents/`, `scripts/`, or cookiecutter from upstream | **security** CLEAR condition |
| `npx skills add`, `/plugin install`, marketplace sync | INTAKE: clone, do not run installers; no auto-update |
| Superpowers / Pocock / Addy packs for Python tooling | Dual routers |
| Hand-edit `pyproject.toml` to add/remove deps | `uv add` / `uv remove` only |
| `[tool.ty] python-version` | Belongs under `[tool.ty.environment]` |
| hatchling as the default backend | `uv_build` unless a later Ask says otherwise |
| Secrets in `pyproject.toml`, scripts, or lockfiles | History is forever |

## Decision

| Doing | Path |
| --- | --- |
| Single-file script + deps | PEP 723 (below) |
| Multi-file, not published | `uv init` + groups |
| Reusable package | `uv init --package` + full `pyproject` |
| Existing tree | Migration table — Ask first if it already ships |

## Tools

| Tool | Purpose | Replaces |
| --- | --- | --- |
| **uv** | Deps, venv, run, build | pip, virtualenv, pip-tools, pipx, pyenv, Poetry |
| **ruff** | Lint + format | flake8, black, isort, pyupgrade, pydocstyle |
| **ty** | Types | mypy, pyright |
| **pytest** | Tests + coverage | unittest |
| **prek** | Fast hooks (Ask first) | pre-commit — do not copy upstream hook dirs |

Security scanners (shellcheck, detect-secrets, actionlint, zizmor, pip-audit, Dependabot) are **tester / security**, not this skill. Pair with `security-hardening`. Do not vendor their configs from trailofbits.

## Minimal project

```bash
uv init myproject
cd myproject
uv add requests
uv add --group dev pytest ruff ty
uv sync --all-groups
uv run pytest
uv run ruff check .
uv run ruff format --check
uv run ty check .
```

Package:

```bash
uv init --package myproject
cd myproject
uv sync --all-groups
uv build
```

## pyproject (first-party defaults)

```toml
[project]
name = "myproject"
version = "0.1.0"
requires-python = ">=3.11"
dependencies = []

[dependency-groups]
dev = [{include-group = "lint"}, {include-group = "test"}, {include-group = "audit"}]
lint = ["ruff", "ty"]
test = ["pytest", "pytest-cov"]
audit = ["pip-audit"]

[tool.ruff]
line-length = 100
target-version = "py311"

[tool.ruff.lint]
select = ["ALL"]
ignore = ["D", "COM812", "ISC001"]

[tool.pytest.ini_options]
addopts = ["--cov=myproject", "--cov-fail-under=80"]

[tool.ty.terminal]
error-on-warning = true

[tool.ty.environment]
python-version = "3.11"

[tool.ty.rules]
possibly-unresolved-reference = "error"
unused-ignore-comment = "warn"
```

`uv add` still owns `[project].dependencies` and group membership. The block is the shape, not a license to hand-edit dep lists.

## PEP 723 scripts

```python
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.11"
# dependencies = [
#     "httpx",
# ]
# ///

import httpx
print(httpx.get("https://example.com").status_code)
```

```bash
uv init --script myscript.py
uv add --script myscript.py httpx
uv run myscript.py
```

No lockfile, no groups, no local path deps. Multi-file? Use `pyproject.toml`.

`uv run --with pkg` is for one-off probes. Project need? `uv add`.

## Migration (only when asked)

| From | Do | Then delete |
| --- | --- | --- |
| `requirements.txt` + pip | `uv init --bare`; `uv add` each reviewed package (or a reviewed loop over non-comment, non-flag lines) | `requirements*.txt`, old `venv/` / `.venv/`; commit `uv.lock` |
| `setup.py` / `setup.cfg` | `uv init --bare`; `uv add` from `install_requires`; copy name/version/description into `[project]` | `setup.py`, `setup.cfg`, `MANIFEST.in` |
| flake8 + black + isort | `uv remove` them; drop their config; `uv add --group dev ruff`; `uv run ruff check --fix .` then `uv run ruff format .` | `.flake8`, `[tool.black]`, `[tool.isort]` |
| mypy / pyright | `uv remove`; `uv add --group dev ty`; `uv run ty check src/` | `mypy.ini`, `pyrightconfig.json`, `[tool.mypy]`, `[tool.pyright]` |

Complex markers / VCS deps: stop and handle by hand. Do not blind-import a lock you have not read.

## uv (short)

| Command | Use |
| --- | --- |
| `uv init` / `uv init --package` | App vs distributable |
| `uv add <pkg>` / `uv add --group dev <pkg>` | Deps |
| `uv remove <pkg>` | Drop a dep |
| `uv sync` / `uv sync --all-groups` | Install |
| `uv run <cmd>` | Run in the project env |
| `uv run --with <pkg>` | Temporary extra |
| `uv build` / `uv publish` | Package; publish is Ask first |

## Roles

| Role | Owns | Does not own |
| --- | --- | --- |
| **builder** | Applying this toolchain on product work | Pulling quarantined upstream extras |
| **tester** | ruff/fmt hooks when `.py` appears | Shipping trailofbits hook yaml |
| **security** | Intake + this CLEAR condition | Day-to-day `uv add` coaching |
| **manager** | After-act | Blessing a pack install |

## Red flags

- “I’ll pip install just this once”
- “source the venv”
- “npx / plugin-install the ToB skill”
- “run the cookiecutter”
- “copy hooks/templates so we match upstream”
- “keep requirements.txt and uv”
- “hand-edit pyproject to add the package”

Stop. Use uv. Or Ask first.

## Upstream pin

trailofbits/skills `modern-python` @ `d3323cefbcf645678b8dc481de204b02ad3d02dc` (SKILL blob `cf5e416095b166547d383e96515377695827defd`). Rewrite. CC-BY-SA 4.0. See [SOURCES.md](../../SOURCES.md).
