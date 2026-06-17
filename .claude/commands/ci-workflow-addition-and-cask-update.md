---
name: ci-workflow-addition-and-cask-update
description: Workflow command scaffold for ci-workflow-addition-and-cask-update in homebrew-tap.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /ci-workflow-addition-and-cask-update

Use this workflow when working on **ci-workflow-addition-and-cask-update** in `homebrew-tap`.

## Goal

Adds or updates CI workflows for Homebrew Cask validation and updates, often alongside cask formula changes.

## Common Files

- `.github/workflows/validate-cask.yml`
- `.github/workflows/update-cask.yml`
- `Casks/*.rb`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Modify or add workflow YAML files under .github/workflows/ (e.g., validate-cask.yml, update-cask.yml)
- Edit or update a Cask formula file under Casks/ (e.g., keyden.rb)
- Commit changes together to ensure CI and formula are in sync

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.