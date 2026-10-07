# The CLA Assistant

Every public Pipelex repository that asks contributors to sign a contributor licence agreement runs the CLA Assistant from one workflow, [`.github/workflows/cla.yml`](../.github/workflows/cla.yml) here, and carries no copy of it.

**Which repositories run it is declared in `github-manager`**, in `config/organization.yaml`, in two places side by side: the organization ruleset `cla`, whose `repository_ids` are the repositories it covers and which requires this workflow on pull requests into their `dev`, and the organization secrets `CLA_GH_APP_ID` and `CLA_GH_APP_PRIVATE_KEY`, granted to the same repositories. Adding a repository means adding it to both, in one pull request there, and giving the repository its own `CLA.md` on `main`, the document a contributor is asked to sign.

GitHub runs the workflow as it is on this repository's `main`, in the context of the pull request's repository: the secrets it reads are the ones granted to that repository, the allowlist is the organization variable `CLA_ALLOWLIST`, and the document it links is that repository's `CLA.md`. Signatures are recorded in `Pipelex/cla-signatures`, so a contributor who signs once is signed for every repository. A change to the workflow therefore reaches every repository when `dev` is promoted to `main` here.

**A signature takes effect at the next run.** A workflow required by a ruleset runs only on pull request events, never on a comment, so after a contributor comments the signing sentence, the check passes once the contributor pushes again or a maintainer re-runs the failed `CLAAssistant` job; that run reads the comment and records the signature.
