# .github

Shared GitHub configuration and reusable workflows for the Bothrs organization.

## Reusable Workflows

### Validate PR Title

Enforces conventional commit format on PR titles using [semantic-pull-request](https://github.com/amannn/action-semantic-pull-request).

```yaml
name: Validate PR title

on:
  pull_request:
    types: [opened, edited, synchronize]

jobs:
  validate:
    uses: bothrs/.github/.github/workflows/validate-pr-title.yml@main
    secrets: inherit
```

### PR Labeler

Automatically labels PRs based on branch name prefixes (e.g., `feat/` -> `feature`, `fix/` -> `bug`).

```yaml
name: PR Labeler

on:
  pull_request:
    types: [opened, edited]

jobs:
  labeler:
    uses: bothrs/.github/.github/workflows/labeler.yml@main
    secrets: inherit
```

### Release Please

Automates changelog generation and release PRs using [release-please](https://github.com/googleapis/release-please). Requires `release-please-config.json` and `.release-please-manifest.json` in the consuming repo.

```yaml
name: Release Please

on:
  push:
    branches: [main]

jobs:
  release-please:
    uses: bothrs/.github/.github/workflows/release-please.yml@main
    secrets: inherit
```

## Org-wide Files

- `pull_request_template.md` — Default PR template for all repos
