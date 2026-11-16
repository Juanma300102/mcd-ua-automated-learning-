# Design

## Context

uv 0.11.6 and Python 3.12.3 are already on the machine. The repository holds only the notebook, `data/` (ignored by git through `data/*`) and the OpenSpec and agent folders. Motivation: see proposal.md.

## Goals / Non-Goals

**Goals:**
- One-command reproducible setup and headless notebook execution.

**Non-Goals:**
- Packaging the project as an installable library.
- Changing how Colab runs the notebook.
- Adding analysis libraries the stages do not need yet, such as statsmodels. A stage change adds such a library with `uv add` if it needs one.

## Decisions

- **Non-packaged uv project** (`[tool.uv] package = false`) rather than `uv init --lib` or `--package`. The repository is coursework, not a library, so a build backend adds nothing.
- **Dev group for notebook tooling.** `ipykernel` and `nbconvert` go under `[dependency-groups] dev`. uv syncs that group by default, so `uv sync` stays the only command. We use `nbconvert` instead of the full `jupyter` metapackage, which pulls in a much larger dependency tree. A user who wants an interactive UI can still run `uv run --with jupyterlab jupyter lab`.
- **Python 3.12**, matching the system interpreter, so uv does not download another one. It is also supported by current pandas and seaborn releases.
- **Unpinned lower bounds in `pyproject.toml`; exact versions come from `uv.lock`.** We add them with `uv add`, not by editing the file by hand, so uv computes the bounds.

## Risks / Trade-offs

- [The local versions differ from Colab's preinstalled versions] → The notebook uses only stable, mainstream APIs. A version mismatch could change how plots look, but not the results.
- [The CSV is ignored by git, so a fresh clone cannot run the notebook] → Document in the README that the CSV must be placed in `data/`. This change does not alter the ignore rule; committing the data is the user's decision.
