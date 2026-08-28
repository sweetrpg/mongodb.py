## [0.0.21] - 2026-08-28

### 🐛 Bug Fixes

- *(deps)* Bump PyMongo to 4.10.1 for Python 3.14 compatibility
- Sync __init__.py version to 0.0.146, matching pyproject.toml
- Unbreak tests under strict pytest config from #53
- Restore strict pytest warnings, fix the actual root causes

### 🚜 Refactor

- Migrate to uv packaging, add mongo service to CI, standardize release process
# Changelog

## [Unreleased]

- Migrated packaging to uv (pyproject.toml + uv.lock), replacing setup.py/setup.cfg/tox.ini.
- Fixed PyMongo 3.x/Python 3.14 incompatibility (`from collections import MutableMapping`,
  removed in 3.10+) - bumped to PyMongo 4.10.1+.
- Bumped requires-python to >=3.14 (platform floor) from >=3.12.
- Bumped the version file to 0.0.146 - this repo's own tags stop at v0.0.20, but the published
  PyPI package had already reached 0.0.145 before this repo's history was reset at some point.
- Added a `mongodb` service container to CI/PR workflows - tests require a live `MONGODB_URI`
  and previously had no service to provide one, failing on every run.
- Replaced two uncoordinated ad hoc release mechanisms (a `relekang/python-semantic-release`
  auto-tag-on-push step, and a manual "Bump version" workflow that only tagged refs without
  touching `__init__.py`) with the standard prepare-release/release/tag-release workflow family.
- Repo scaffolding brought up to platform baseline (community docs, AGENTS.md).

<!--next-version-placeholder-->

## v0.0.20 (2025-03-23)



## v0.0.19 (2025-03-16)



## v0.0.18 (2025-03-09)



## v0.0.17 (2025-03-02)



## v0.0.16 (2025-02-23)



## v0.0.15 (2025-02-16)



## v0.0.14 (2025-02-09)



## v0.0.13 (2025-02-02)



## v0.0.12 (2025-01-26)



## v0.0.11 (2025-01-19)



## v0.0.10 (2025-01-12)



## v0.0.9 (2025-01-05)



## v0.0.8 (2024-12-29)



## v0.0.7 (2024-12-22)



## v0.0.6 (2024-12-15)



## v0.0.5 (2024-12-08)



## v0.0.4 (2024-12-01)



## v0.0.3 (2024-11-24)



## v0.0.2 (2024-11-17)



## v0.0.1 (2024-11-15)


