# Proposal

## Why

The analysis notebook needs pandas, numpy, matplotlib and seaborn plus a Jupyter kernel, and none of them are installed: the system Python 3.12 has no pandas. The repository has no dependency manifest. We will manage the environment with uv so that anyone can reproduce it with one command, and so the stage changes (`load-store-traffic-dataset` through `define-store-traffic-model-use`) can execute the notebook locally.

## What Changes

- Add a uv-managed project: `pyproject.toml`, which declares the project as non-packaged, `.python-version` and a committed `uv.lock`.
- Declare runtime dependencies (pandas, numpy, matplotlib, seaborn) and notebook tooling (ipykernel, nbconvert) as a dev dependency group.
- Ignore `.venv/` in `.gitignore`. The existing `data/*` rule stays.
- Document the setup and run commands (`uv sync`, executing the notebook through `uv run`) in a short README section.

## Capabilities

### New Capabilities
- `python-environment`: how the project's Python environment is declared, reproduced and used to execute the notebook.

### Modified Capabilities
<!-- none -->

## Impact

- New files: `pyproject.toml`, `uv.lock`, `.python-version`, `README.md`. Modified file: `.gitignore`.
- Prerequisite for the five stage changes, which run notebook cells.
- Google Colab is not affected: Colab already ships these libraries and does not use uv.
