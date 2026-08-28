# AGENTS.md

This file provides guidance to Claude Code, Codex, GitHub Copilot, and other coding agents
working in this repository.

## About This Project

`sweetrpg-db` (PyPI: `sweetrpg-db`, import name `sweetrpg_db`) is the MongoDB data access layer
shared across sweetrpg Python services - a generic repository/query-options abstraction over
`mongoengine`/`PyMongo`, used by services that persist to MongoDB (e.g. via `sweetrpg-model-core`
model/schema base classes).

Note: this repo's own git tags stop at `v0.0.20`, but the published `sweetrpg-db` PyPI package
had already reached `0.0.145` before this repo's history was reset/rewritten at some point in
the past - the version file was bumped to `0.0.146` (see pyproject.toml) to stay ahead of what's
already published; don't let a future release compute a lower next-version from this repo's own
tag history without checking PyPI first.

## Committing Code

[Conventional Commits](https://www.conventionalcommits.org/): `<type>(<scope>): <description>`.

## Branches and Workflow

Git-flow (see `docs/git-flow.md` in `sweetrpg/platform`): `develop` is the integration branch,
`master` reflects the latest release. Feature/fix branches off `develop`, PR back into `develop`.

Releasing: dispatch the "Prepare Release" workflow - it computes the next version via
`git-cliff`, bumps `__version__` in `src/sweetrpg_db/__init__.py`, updates `CHANGELOG.md`, and
opens a `release/<version>` PR into `master`. Merging that PR tags the release, which publishes
to PyPI (`.github/workflows/prepare-release.yaml`/`release.yaml`/`tag-release.yaml`, using the
`sweetrpg/github-actions` reusable Python release workflow family). Previously this repo had two
separate, uncoordinated ad hoc mechanisms: a `relekang/python-semantic-release` step auto-tagging
every `develop` push directly (no review, no changelog), and a manual `workflow_dispatch`
"Bump version" workflow that only tagged git refs without touching `__init__.py` - both removed
in favor of the above.

## Running Checks Locally

Python 3.14, managed via [uv](https://docs.astral.sh/uv/), which is the required Python tool on
this platform (`pyproject.toml` + committed `uv.lock`; do not use `pip`/`tox`/`setup.py`
directly).

```bash
uv sync --group test   # create .venv and install deps
uv run pytest tests    # run tests
uv lock --upgrade      # update dependencies
```

A local MongoDB is required - `mongod` on `localhost:27017`, or
`docker run -p 27017:27017 mongo:7.0`, is sufficient. Set `MONGODB_URI` accordingly (e.g.
`mongodb://localhost:27017/unit-tests`).
