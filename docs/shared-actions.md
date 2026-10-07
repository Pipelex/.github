# Shared actions

`actions/` here holds composite GitHub Actions that Pipelex repositories run instead of each keeping its own copy of the same steps. A repository references one at `@main`, so a change to a shared action reaches every repository when `dev` is promoted to `main` here, and not before.

They are composite actions rather than reusable workflows on purpose: the job stays in the calling repository's own workflow, so its check keeps the job's name, and a ruleset that requires the check by that name is untouched when a repository moves onto a shared action.

## `actions/cla` — the CLA Assistant

Every public Pipelex repository that asks contributors to sign a contributor licence agreement runs the CLA Assistant through this action. The repository carries its own `CLA.md` on `main`, which is the document a contributor is asked to sign, and this workflow, identical in every repository, as `.github/workflows/cla.yml`:

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
  CLAAssistant:
    runs-on: ubuntu-latest
    steps:
      - uses: Pipelex/.github/actions/cla@main
        with:
          app-id: ${{ secrets.CLA_GH_APP_ID }}
          private-key: ${{ secrets.CLA_GH_APP_PRIVATE_KEY }}
          allowlist: ${{ vars.CLA_ALLOWLIST }}
```

The workflow passes in the secrets and the allowlist because an action cannot read them by itself. The action reads everything else from the calling repository: its name, its organisation, and the link to its `CLA.md`. Signatures are recorded in `Pipelex/cla-signatures`, so a contributor who signs once is signed everywhere. The allowlist of people and bots who never need to sign is the organisation variable `CLA_ALLOWLIST`, and the GitHub App that writes signatures authenticates with the organisation secrets `CLA_GH_APP_ID` and `CLA_GH_APP_PRIVATE_KEY`. All three are managed in `github-manager`, which must grant both secrets to a repository before its workflow can work.

The check this produces is named `CLAAssistant`. A repository requires it on `dev`, the branch contributions are proposed against, through its ruleset in `github-manager`. It is not required on `main` or on release branches: a release only promotes commits whose authors already passed the check on `dev`.

GitHub runs a `pull_request_target` workflow as it exists on the repository's default branch, `main`, whatever branch the pull request targets and whatever the pull request changes. So a repository that adds or changes this workflow runs the new version only after a release has brought it to `main`, and a repository whose `main` has no `cla.yml` runs no CLA check at all.
