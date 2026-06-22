# ComfyUI Contributor License Agreements

This repository stores contributors' signatures of our CLA.

## How It Works

When a contributor opens a pull request in one of our projects, a GitHub Action ([contributor-assistant/github-action](https://github.com/contributor-assistant/github-action)) automatically checks whether everyone who authored commits in that PR has signed our [Contributor License Agreement](comfyui_icla.md). If anyone hasn't, the bot asks them to sign by replying with a short, fixed phrase.

Once a contributor signs, their identity is recorded in [`signatures/cla.json`](signatures/cla.json) in this central repository, the pull request's status check turns green, and they won't be asked again for future contributions. Known bot accounts are allow-listed so they never need to sign.

This keeps all signatures in one place across every project, with no server or database to maintain — everything runs through GitHub Actions.

## Setup

To enable the CLA check on a new repository:

1. Copy the workflow file [`.github/workflows/cla.yml`](.github/workflows/cla.yml) from this repository into the same path in the target repository.

2. Add a secret in the target repository named `PERSONAL_ACCESS_TOKEN` containing the token of the service account `comfy-legal`: `Settings` > `Secrets and variables` > `New repository secret`. The token is used by the GitHub action workflow to record signatures here.

3. Add a branch protection rule on the target repository to prevent merging without signing the CLA: `Settings` > `Code and automation` > `Branches` > `Add a classic branch protection rule`

  - Type the branch name (ex: `master` or `main`)
  - Select **Require status checks to pass before merging**
  - Select `license/cla`

Once the workflow and secret are in place, the CLA check runs automatically on every new pull request.
