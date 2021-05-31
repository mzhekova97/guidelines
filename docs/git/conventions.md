# Conventions

### Repositories

- Repository names should be in snake case.

- Repositories meant for versioning workspaces should be named with the project name and carry the `_ws` prefix.

- Repositories should always contain a `.gitignore`. Use [this](https://www.toptal.com/developers/gitignore) to generate one.

## Branches

- Any repository should always have at least two branches: `main` and `dev`, with the former always containing a stable version of the software.

- New branches should always be created from `dev`, never from `main`, and should be named in lower case, with hyphens as separators. Ideally, branches should be very well-scoped, with this reflecting on their naming. We suggest utilizing the following prefixes

    - `feature/...`: for indicating new features;
    - `bugfix/...`: for indicating code refactoring;
    - `refactor/...`: for indicating new features;

- Once a branch has fulfilled its purpose, a new pull request should be created, and assigned to another team member who will be responsible for reviewing the code and merging it into the `dev` branch.

## Commits

- Commits should be well-scoped and frequent. This should reflect on the commit messages, which are expected to be short (with a maximum of 72 characters) and clear, indicating exactly what the commit does. 

- Commit messages should start with a capital letter, be written in the imperative (`Fix bug x`) and end without a period.

## Issues

- Whenever you find a bug or would like to suggest a new feature, an issue should be created in the repository. In the case of a bug, the issue should provide instructions for reproducing it. In the case of a feature, the issue should describe in detail why the feature is needed, what is expected, and provide suggestions of how it could be implemented.

- Issues can too be created for discussing high-level concepts and ideas.


