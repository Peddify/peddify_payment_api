# Peddify Code Collaboration Guideline Document

## Introduction

Welcome to the collaborative development of our app using Flutter! This document outlines the guidelines for our technical collaboration, including version control practices, commit message conventions, and code review processes. By following these guidelines, we aim to ensure smooth and efficient collaboration among all team members.

---

## Version Control System

We will use Git as our version control system and GitHub as our repository host. All project-related code and documentation will be stored in our GitHub repository.

### Repository Structure

- `main` branch: Stable production-ready code.
- `develop` branch: Latest development changes.
- Feature branches: Separate branches for new features, named using the format `feature/short-description`.
- Bugfix branches: Separate branches for bug fixes, named using the format `bugfix/short-description`.
- Hotfix branches: Separate branches for urgent fixes, named using the format `hotfix/short-description`.

### Branching Strategy

1. **Creating a new branch**: Before starting work on a new feature or bugfix, create a new branch from the `develop` branch.

   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/short-description
   ```

2. **Committing changes**: Commit changes regularly with clear and concise commit messages following the Angular Conventional Commits guidelines.

   ```bash
   git commit -m "feat: add user authentication"
   ```

3. **Pushing changes**: Push your branch to GitHub regularly.

   ```bash
   git push origin feature/short-description
   ```

4. **Creating a pull request (PR)**: Once your feature or bugfix is complete, create a PR to merge your branch into the `develop` branch. Request reviews from at least one other team member.

5. **Merging pull requests**: After receiving approval, merge the PR. Use the GitHub UI to merge PRs to ensure proper tracking.

## Commit Message Guidelines

As you might have already noticed, we will follow the [Angular Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) guidelines for our commit messages. This helps in generating consistent and informative commit history.

### Commit Message Format

Commit messages should adhere to the following format:

```bash
<type>(<scope>): <description>

[optional body]

[optional footer(s)]
```

### Types

From the format above, the type may be one of the following:

- `feat`: A new feature.
- `fix`: A bug fix.
- `docs`: Documentation only changes.
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- `refactor`: A code change that neither fixes a bug nor adds a feature.
- `perf`: A code change that improves performance.
- `test`: Adding missing or correcting existing tests.
- `chore`: Changes to the build process or auxiliary tools and libraries such as documentation generation.

### Scopes

Scopes can be anything specifying the place or part of the project the commit change is being made to. For this project, scope may be one of the following:

- `core`
- `ui`
- `api`
- `auth`
- `docs`
- `merchant/orders`
- `merchant/products`
- `merchant/dashboard`
- `buyer/home`
- `buyer/products`
- `buyer/cart`
- `buyer/checkout`
- `buyer/profile`
- `admin/users`
- `admin/orders`
- `admin/products`
- `admin/analytics`
- `notifications`
- `payments`
- `shipping`
- `reviews`

### Description

- Use the imperative mood in the description: "fix" not "fixed" or "fixes".
- Do not capitalize the first letter.
- Do not end the subject line with a period.

For more information on what conventional commits are and how they are to be formatted, please refer to the [Conventional Commits specifications.](https://www.conventionalcommits.org/en/v1.0.0/#specification)

### Examples

- `feat(auth): add user login`
- `fix(ui): correct button alignment`
- `docs(readme): update setup instructions`

## Git Hooks with Husky

To enforce our commit message guidelines, we will use [Husky](https://pub.dev/packages/husky) to set up Git hooks alongside [Commitlint](https://pub.dev/packages/commitlint_cli) and [Commitizen](https://www.npmjs.com/package/commitizen) to aid git prompting and enforce project types and scopes. Husky and Commitlint are project-specific dependencies while Commitizen is an NPM package that has to be installed globally to be used in this project. Read below to see how to set up Commitizen globally. Please check the Setting Up Husky section to see how to set up this workflow by yourself.

### Setup Commitizen

First clone the project's repository and install the dependecies

```bash
flutter pub get
```

Then install commitizen globally, if you have not already.

```bash
npm install -g commitizen
```

Next install the Conventional Commit Adapter.

```bash
npm install -g cz-conventional-changelog
```

Create a .czrc file in your home directory, with path referring to the preferred, globally-installed, commitizen adapter

```bash
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```

You are all set! Now cd into the project repository and use `git cz` instead of `git commit`, and you will find the commitizen prompt.

### Setting Up Commitlint with Husky on your own

1. **Install Commitlint**:

```bash
# Install and configure if needed
dart pub add --dev commitlint_cli

# Configure commitlint to use conventional cli config
echo "include: package:commitlint_cli/commitlint.yaml" > commitlint.yaml
```

2. **Install Husky**:

```bash
# Install Husky
dart pub add --dev **husky**

# Activate hooks
dart run husky install
```

3. **Add Husky pre-commit Hook**:

```bash
dart run husky add .husky/commit-msg  'dart run commitlint_cli --edit ${1}'
```

## Code Review Process

1. **Pull Request (PR)**: Create a PR for all changes. Ensure the PR description includes:

   - A summary of the changes.
   - The issue or feature number (if applicable).
   - Any relevant screenshots or documentation updates.

2. **Review**: At least one other team member must review the PR. Reviewers should:

   - Check for code quality, readability, and adherence to coding standards.
   - Verify that commit messages follow the Angular Conventional Commits guidelines.
   - Ensure that the changes do not introduce new bugs.

3. **Approval**: Once the PR is reviewed and approved, the reviewer can merge the PR into the `develop` branch.

## Coding Standards

- Follow the Flutter/Dart best practices and coding standards.
- Write clean, readable, and maintainable code.
- Comment code where necessary, especially for complex logic.

## Documentation

- Update relevant documentation (README, code comments, etc.) with each change.
- Ensure the documentation is clear and concise.

## Communication

- When decided, we will use the project's communication channel for discussing issues, proposing changes, and seeking feedback.
- Document important decisions and discussions in the project’s documentation or issue tracker.

## Conclusion

By adhering to these guidelines, we can maintain a high standard of code quality and ensure efficient collaboration among all team members. Happy coding!

---

Please feel free to suggest any changes or additions to this document as we continue to refine our collaboration process.
