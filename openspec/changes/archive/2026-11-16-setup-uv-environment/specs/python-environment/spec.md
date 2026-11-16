# Spec Delta

## Purpose

Defines how the project's Python environment is declared with uv, reproduced from the lockfile, and used to execute the analysis notebook.

## ADDED Requirements

### Requirement: Reproducible environment from lockfile
The repository SHALL declare its dependencies in `pyproject.toml` with a committed `uv.lock`, so that `uv sync` creates a working environment without manual package installs.

#### Scenario: Fresh clone sync
- **WHEN** a user runs `uv sync` in a fresh clone
- **THEN** a `.venv` is created and `uv run python -c "import pandas, numpy, matplotlib, seaborn"` exits with code 0

#### Scenario: Lockfile consistency
- **WHEN** `uv lock --check` runs
- **THEN** it exits with code 0

### Requirement: Pinned Python version
The project SHALL pin its Python version in `.python-version` and require a compatible version in `pyproject.toml`.

#### Scenario: Interpreter version
- **WHEN** `uv run python --version` runs
- **THEN** it prints the version pinned in `.python-version`

### Requirement: Headless notebook execution
The environment SHALL be able to execute the notebook from the command line through uv, without a globally installed Jupyter.

#### Scenario: Execute the notebook
- **WHEN** `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb` runs
- **THEN** the command exits with code 0 for the current template notebook

### Requirement: Environment not committed
The virtual environment directory SHALL be excluded from version control.

#### Scenario: Ignored venv
- **WHEN** `git check-ignore .venv` runs after `uv sync`
- **THEN** it prints `.venv`
