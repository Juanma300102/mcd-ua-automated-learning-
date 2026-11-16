# Tasks

## 1. uv project setup

- [x] 1.1 Run `uv init --bare --python 3.12` (or write an equivalent minimal `pyproject.toml`), set `[tool.uv] package = false`, and verify that `pyproject.toml` and `.python-version` exist and `.python-version` contains `3.12`
- [x] 1.2 Run `uv add pandas numpy matplotlib seaborn` and `uv add --dev ipykernel nbconvert`; verify that `uv.lock` exists and `uv run python -c "import pandas, numpy, matplotlib, seaborn"` exits 0
- [x] 1.3 Append `.venv/` to `.gitignore` while keeping `data/*`; verify that `git check-ignore .venv` prints `.venv`

## 2. Execution check and docs

- [x] 2.1 Execute the notebook headlessly on a scratch copy outside the repository (`uv run jupyter nbconvert --to notebook --execute --output <scratch path> TP_Analisis_de_Dataset_v3.ipynb`) and verify exit code 0, leaving the tracked notebook untouched
- [x] 2.2 Add a `README.md` setup section covering `uv sync`, the headless execute command, the interactive option (`uv run --with jupyterlab jupyter lab`) and the note that the CSV must be placed in `data/`; verify by running the documented `uv sync` and `uv lock --check` commands exactly as written
