# Git

This document outlines best practices and conventions to follow when using Git in development.

For effective collaboration, it is important to maintain a clear version history and a systematic workflow for deployments. The following sections detail conventions on branch naming, commit messages and history revision, and include concrete examples and workflow steps.

## 1. Branch Management

- **Primary Branches**: The project uses two primary protected branches:
    - `main`: Contains stable code ready for production.
    - `develop`: Serves as the integration branch for new features before they are released, developers work in this branch.
- **Isolation**: Since the `develop` branch is protected, isolate each new feature on a dedicated branch and then submit a Merge Request for integration.

## 2. Commit Messages

Commit messages should be clear, well-structured, and categorized to enable the automatic generation of changelogs for each release. Every commit must fall into one of the following categories:

- **feat**: Adding a new feature or improving an existing one.
- **fix**: Resolving an issue, whether it's functional, related to QA, or even a simple typo.
- **test**: Adding or improving tests to increase coverage or enhance existing test cases.
- **chore**: Technical tasks related to the project, such as updating dependencies, refactoring code, or performing post-deployment maintenance.
- **docs**: Creating or updating documentation, including API testing documentation (e.g., Bruno).

### Expected Format

Commit messages must follow this specific format:

```
[category]([one_word_identifier]): [commit description]
```

Additionally, commit messages should match the following regular expression:  
`((feat|fix|test|doc|chore)(\((.*)\)): (.*)|Merge(.*)|Revert(.*))`

### Examples

Here are several examples of properly formatted commit messages:

- `feat(auth): add new authentication module`
- `fix(login): resolve issue with login redirection`
- `test(coverage): add unit tests for user service`
- `chore(deps): update Symfony to version 7.1`
- `docs(readme): update installation instructions`

By adhering to these conventions, you ensure a more readable Git history and facilitate the generation of changelogs for each release.

