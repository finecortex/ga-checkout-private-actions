# Checkout private actions
![](https://img.shields.io/badge/github--action-1.0.1-green)

GitHub action to checkout private actions.

## Table of contents

- [Usage](#usage)
- [Inputs](#inputs)
  - [`token`](#token)
  - [`actions`](#actions)
  - [`directory`](#directory)
- [About](#about)


## Usage

```yaml
name: "Example workflow"
on: push
jobs:
  ci:
    runs-on: ubuntu-18.04
    steps:
    # ----------------------------------------------------------------------------
    #  Checkout private actions
    # ----------------------------------------------------------------------------
    - uses: finecortex/ga-checkout-private-actions@v1
      with:
        # Repository PAT (personal access token) or GITHUB_TOKEN.
        # Type: string
        # REQUIRED
        token: ${{ secrets.CLONE_PRIVATE_REPO }}

        # List of private actions to clone. Must be an array where each entry matches "owner/repo@ref" format.
        # Type: string[]
        # REQUIRED
        actions: |
          org/action-1@v1
          org/action-2@v1
          org/action-3@v1

        # Directory where action repositories will be cloned.
        # Type: string
        # Default: ./.github/actions
        directory: ./.github/actions

    # ----------------------------------------------------------------------------
    #  Use private actions
    # ----------------------------------------------------------------------------
    - uses: ./.github/actions/action-1
    - uses: ./.github/actions/action-2
    - uses: ./.github/actions/action-3
```
## Inputs

### `token`

Repository PAT (personal access token) or GITHUB_TOKEN.

**Type**: `string`

⚠️ **Required**

---

### `actions`

List of private actions to clone. Must be an array where each entry matches "owner/repo@ref" format.

**Type**: `string[]`

⚠️ **Required**

---

### `directory`

Directory where action repositories will be cloned.

**Type**: `string`

**Default**: `./.github/actions`



## About
This action was **automatically generated** on **Tue, 01 Sep 2020 15:32:21 GMT**
