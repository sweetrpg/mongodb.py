# Contributing

Thanks for considering a contribution to `sweetrpg-db`.

## Branching

This repo follows the sweetrpg platform's git-flow convention:

* `develop` is the integration branch. All feature and fix branches merge here.
* `master` reflects the latest released state. Nothing is committed here directly.
* Branch names: `feature/<description>` for new functionality, `fix/<description>` for bug
  fixes, `hotfix/<description>` for urgent fixes to a released version.

```bash
git checkout develop
git pull
git checkout -b feature/my-change
# ... work, commit ...
git push -u origin feature/my-change
# open a PR: feature/my-change -> develop
```

## Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>
```

## Running checks locally

```bash
uv sync --group test
uv run pytest tests
```

A local MongoDB is required - `mongod` on `localhost:27017`, or
`docker run -p 27017:27017 mongo:7.0`, is sufficient for tests. Set `MONGODB_URI` accordingly
(e.g. `mongodb://localhost:27017/unit-tests`).

## Pull requests

CI runs automatically on PRs targeting `develop`. Once checks pass, it can be merged (auto-merge
is enabled once required checks pass).
