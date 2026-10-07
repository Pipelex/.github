# Shared workflows

`.github/workflows/` here holds reusable GitHub Actions workflows that Pipelex repositories call instead of each keeping its own copy. A caller references one at `@main`, so a change to a shared workflow reaches every caller when `dev` is promoted to `main` here, and not before.

## `cla.yml` — the CLA Assistant

Every public Pipelex repository that asks contributors to sign a contributor licence agreement runs the CLA Assistant through this workflow. The repository carries its own `CLA.md` on `main`, which is the document a contributor is asked to sign, and the stub below, identical in every repository, as `.github/workflows/cla.yml`:

```yaml
name: CLA Assistant

on:
  issue_comment:
    types: [created]
  pull_request_target:
    types: [opened, closed, synchronize]

permissions:
  actions: write
  contents: read
  pull-requests: write
  statuses: write

jobs:
  cla:
    uses: Pipelex/.github/.github/workflows/cla.yml@main
    secrets: inherit
```

The shared workflow reads everything else from the calling repository: its name, its organisation, and the link to its `CLA.md`. Signatures are recorded in `Pipelex/cla-signatures`, so a contributor who signs once is signed everywhere. The allowlist of people and bots who never need to sign is the organisation variable `CLA_ALLOWLIST`, and the GitHub App that writes signatures authenticates with the organisation secrets `CLA_GH_APP_ID` and `CLA_GH_APP_PRIVATE_KEY`. All three are managed in `github-manager`, which must grant both secrets to a repository before its stub can work.

The check this produces is named `cla / CLAAssistant`, the calling job's name followed by the shared job's. A repository requires it on `dev`, the branch contributions are proposed against, through its ruleset in `github-manager`. It is not required on `main` or on release branches: a release only promotes commits whose authors already passed the check on `dev`.

`pull_request_target` runs the stub as it exists on the pull request's base branch, never the version in the pull request. So a repository that adds or changes its stub sees the change only on pull requests opened after it has merged.
