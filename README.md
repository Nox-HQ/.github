# Nox-HQ/.github

[![nox security grade](.github/nox-badge.svg)](https://github.com/nox-hq/nox)

Organization-wide defaults for Nox-HQ: the profile shown on the organization
page (`profile/README.md`) and the reusable workflows the repositories call.

| Workflow | What it does |
|---|---|
| `nox-remediate.yml` | Weekly dependency and GitHub Actions remediation with a pinned nox, verified before the PR opens |
| `nox-badge.yml` | Scans the default branch with a pinned nox and commits its grade to `.github/nox-badge.svg` |
| `plugin-ci.yml`, `plugin-release.yml` | Deprecated: kept working for plugins scaffolded before nox v1.38.3 |
