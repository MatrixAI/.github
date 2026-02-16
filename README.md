# Templates

## Issues, Pull Requests, Merge Requests

This repository stories issue, pull request and merge request templates for Matrix AI

GitHub templates are stored in `.github`. This repository must be placed under https://github.com/MatrixAI/.github. The `.github` repository name is essential for GitHub to recognise it as a special organisation-template repository.

GitLab templates are stored in `.gitlab`. This repository must be selected as the templates repository under `Settings > General > Templates`.

Note that template syntax differs by a little bit. In particular GitHub templates require a stanza at the beginning while GitLab templates use special slash commands. When updating the templates for GitHub or GitLab, ensure that it is also updated for the other system as well so we can have a consistent set of templates.

Ensure that this repository is mirrored from GitLab to GitHub.

## Workflows

This is where we centralized re-usable workflows for GitHub actions. Workflows
are grouped together into different kinds of projects.

### Windows runners and Node.js

On GitHub-hosted Windows runners it is common to have multiple Node versions on `PATH` (for example Node 22 may be preinstalled). If a workflow calls `refreshenv` / `Update-SessionEnvironment` after selecting Node, it can rebuild `PATH` and cause `npm.cmd` to come from a different Node installation than `node.exe`.

To avoid the Node/npm mismatch:

* Windows jobs are pinned to `windows-2022`.
* Windows execution is split into two steps:
  1. **Bootstrap** runs repo-local `./scripts/choco-install.ps1` and prints:
     `where.exe node`, `where.exe npm`, `node -v`, `npm -v`, `npm exec --yes node -v`.
  2. **Build/Test** runs npm commands in a separate step so `$GITHUB_PATH` updates from the bootstrap step are applied deterministically.
* Reusable workflows in this repository do not use `actions/setup-node` for Windows; they delegate Node selection to the downstream repo’s `./scripts/choco-install.ps1`.

* library-js - TS/JS projects that produce libraries as NPM packages.
  - feature - for feature branches
  - staging - for staging branches
  - tag - for tag branches
* library-js-native - TS/JS projects that produce libraries using native code as NPM packages.
  - feature
  - staging
  - tag
* application-js-cloudflare - TS/JS projects that produce Cloudflare applications
  - feature
  - staging
  - master
  - feature-closed

To use them, for example in a library-js project. You create 3 caller workflows
in `/.github/workflows`:

* `feature.yml`
  ```yml
  name: "CI / Feature"

  on:
  push:
      branches:
      - feature*
  workflow_dispatch:

  concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

  jobs:
  use-library-js-feature:
      permissions:
      contents: read
      actions: write
      checks: write
      uses: MatrixAI/.github/.github/workflows/library-js-feature.yml@master
  ```
* `staging.yml`
  ```yml
  name: "CI / Staging"
  
  on:
    push:
      branches:
        - staging
    workflow_dispatch:
  
  concurrency:
    group: ${{ github.workflow }}-${{ github.ref }}
    cancel-in-progress: true
  
  jobs:
    use-library-js-staging:
      permissions:
        contents: read
        actions: write
        checks: write
        pull-requests: write
      uses: MatrixAI/.github/.github/workflows/library-js-staging.yml@master
      secrets: inherit
  ```
* `tag.yml`
  ```yml
  name: "CI / Tag"
  
  on:
    push:
      tags:
        - 'v*.*.*'
    workflow_dispatch:
  
  jobs:
    use-library-js-tag:
      permissions:
        contents: read
        actions: write
      uses: MatrixAI/.github/.github/workflows/library-js-tag.yml@master
      secrets: inherit
  ```
