```markdown
# homebrew-tap Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the conventions and workflows for contributing to the `homebrew-tap` repository, which manages custom Homebrew Cask formulae using Ruby. You'll learn about file organization, coding style, commit patterns, and how to work with CI workflows for validating and updating Casks.

## Coding Conventions

### File Naming
- Use **kebab-case** for file names.
  - Example: `my-cask-formula.rb`

### Imports
- Use **relative imports** within Ruby files.
  - Example:
    ```ruby
    require_relative '../lib/some_helper'
    ```

### Exports
- Use **named exports** (explicitly define what is exported).
  - Example:
    ```ruby
    module MyCask
      def self.install
        # installation logic
      end
    end
    ```

### Commit Patterns
- Commit types are mixed, with some using the `fix` prefix.
- Average commit message length: 66 characters.
  - Example:
    ```
    fix: update sha256 for keyden cask to match upstream release
    ```

## Workflows

### CI Workflow Addition and Cask Update
**Trigger:** When introducing or updating automated CI validation/update workflows for Casks, especially when changing Cask formula requirements.  
**Command:** `/add-ci-cask-workflow`

1. **Modify or add workflow YAML files** under `.github/workflows/` (e.g., `validate-cask.yml`, `update-cask.yml`).
    - Example:
      ```yaml
      # .github/workflows/validate-cask.yml
      name: Validate Cask
      on: [push, pull_request]
      jobs:
        test:
          runs-on: ubuntu-latest
          steps:
            - uses: actions/checkout@v2
            - name: Run Homebrew Cask Audit
              run: brew audit --cask --strict Casks/keyden.rb
      ```
2. **Edit or update a Cask formula file** under `Casks/` (e.g., `keyden.rb`).
    - Example:
      ```ruby
      cask "keyden" do
        version "1.2.3"
        sha256 "abc123..."
        url "https://example.com/keyden-#{version}.dmg"
        name "Keyden"
        desc "A sample cask"
        homepage "https://example.com/keyden"
      end
      ```
3. **Commit changes together** to ensure CI and formula are in sync.
    - Example commit message:
      ```
      fix: add CI workflow and update keyden cask formula for v1.2.3
      ```

## Testing Patterns

- **Testing framework:** Unknown (no explicit framework detected).
- **Test file pattern:** Files are named with `*.test.*`.
  - Example: `keyden.test.rb`
- Tests, if present, are likely written in Ruby and follow the same conventions as formula files.

## Commands

| Command                | Purpose                                                        |
|------------------------|----------------------------------------------------------------|
| /add-ci-cask-workflow  | Add or update CI workflows for Cask validation and updates     |
```
