# Torq-PR-Sync

This repo is the Git-backed review and release store for Torq workflows.

## How it works

1. A workflow is submitted for review in Torq.
2. A Torq workflow opens a pull request here. It creates a branch named `<workflow>/<revision-id>` and commits the workflow definition to the `workflows/` folder.
3. A reviewer checks the changes in the pull request and merges it.
4. The merge triggers a webhook to Torq, which imports the approved revision into prod, tags it, and publishes it in dev.

## Notes

- Pull requests are created automatically by the Torq sync GitHub App. Do not edit the `workflows/` folder by hand.
- Each commit message ends with `Torq-Workflow-Id` and `Torq-Revision-Id`. These link the pull request back to the exact revision in Torq, so do not remove them.
- Merging is the approval step. Nothing reaches prod until a pull request is merged.
