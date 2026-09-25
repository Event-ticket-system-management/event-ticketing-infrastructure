# Git Workflow & Branching Strategy

## Core Branches
- `main`: Production release code. Strictly protected.
- `develop`: Integration branch for active feature development. Protected.

## Feature Branches
- Format: `feature/<feature-name>`
- Example: `feature/user-registration`, `feature/payment-processing`

## Branch Protection Rules
Across all repositories, `main` and `develop` branches are protected with the following rules:
1. **Require a pull request before merging**: Direct pushes are prohibited. All changes must be merged via Pull Requests.
2. **Require status checks to pass before merging**: Automated CI test/build pipelines must pass before code can be merged.
3. **Do not allow bypassing the above settings**: Enforced strictly for all contributors, including administrators.

## Repository Hygiene & Environment Standards
- **Standard Ignore Rules**: Configured `.gitignore` across all microservices and infrastructure code to prevent build artifacts (`target/`, `dist/`), dependencies (`node_modules/`), Terraform state files, and local environment files (`.env`) from entering source control.
- **Cross-Platform Line Ending Strategy**: Normalized text files to `LF` end-of-line (EOL) sequence across environments to prevent multi-OS git diff conflicts (Windows CRLF vs Linux/macOS LF).
