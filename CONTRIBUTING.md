# Contributing to MedRecord

Thank you for your interest in contributing to MedRecord! This document provides guidelines and instructions for contributing to the project.

## Code of Conduct

This project adheres to a Code of Conduct that all contributors are expected to follow. Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) before contributing.

## How to Report Bugs

If you find a bug, please create an issue on GitHub with the following information:

1. **Clear title** - Summarize the issue in one line
2. **Description** - Detailed explanation of the bug
3. **Steps to reproduce** - How to recreate the issue
4. **Expected behavior** - What should happen
5. **Actual behavior** - What actually happens
6. **Environment** - OS, Java version, relevant configurations
7. **Logs** - Any relevant error messages or logs

## How to Suggest Features

We welcome feature suggestions! To propose a new feature:

1. **Check existing issues** - Ensure it hasn't been suggested already
2. **Create a feature request** - Use the feature request template
3. **Describe the problem** - What problem does this solve?
4. **Describe the solution** - What would you like to see?
5. **Consider alternatives** - What other approaches did you consider?

## Development Workflow

### 1. Fork the Repository

Fork the repository to your GitHub account and clone it locally:

```bash
git clone https://github.com/your-username/medRecord.git
cd medRecord
git remote add upstream https://github.com/original-owner/medRecord.git
```

### 2. Create a Feature Branch

Always create a new branch from `develop` for your work:

```bash
git checkout develop
git pull upstream develop
git checkout -b feature/your-feature-name
```

### Branch Naming Convention

Use the following prefixes for branch names:

- `feature/` - New features (e.g., `feature/add-patient-search`)
- `bugfix/` - Bug fixes (e.g., `bugfix/fix-auth-token-expiry`)
- `hotfix/` - Urgent fixes for production (e.g., `hotfix/security-patch`)
- `refactor/` - Code refactoring (e.g., `refactor/improve-database-queries`)
- `docs/` - Documentation updates (e.g., `docs/update-api-documentation`)
- `test/` - Test additions or fixes (e.g., `test/add-integration-tests`)

### 3. Make Your Changes

Follow the coding standards outlined below and ensure your code is well-tested.

### 4. Commit Your Changes

Use clear, descriptive commit messages. We follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, no logic change)
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `chore` - Maintenance tasks

**Examples:**
```bash
git commit -m "feat(patient-service): add patient search by diagnosis"
git commit -m "fix(auth-service): resolve JWT token expiration issue"
git commit -m "docs(readme): update deployment instructions"
```

### 5. Push and Create a Pull Request

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub with:

- **Clear title** - Summarize the changes
- **Description** - Explain what and why
- **Related issues** - Link any related issues (e.g., "Closes #123")
- **Testing** - Describe how you tested the changes
- **Screenshots** - If applicable, add screenshots

## Code Standards

### Java Code

- Follow the [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- Use meaningful variable and method names
- Write Javadoc comments for public methods and classes
- Keep methods small and focused (single responsibility)
- Use Java 21 features appropriately (records, pattern matching, etc.)

**Formatting:**
```bash
# Use your IDE's formatter or:
mvn spotless:apply
```

### Python Code

- Follow [PEP 8](https://pep8.org/) style guide
- Use type hints for function parameters and return values
- Write docstrings for functions and classes
- Use meaningful variable names (no single-letter variables except in loops)

**Formatting:**
```bash
# Format with black
black lambda/

# Check style with flake8
flake8 lambda/
```

### Terraform Code

- Use `terraform fmt` to format all Terraform files
- Use descriptive resource names
- Add comments for complex configurations
- Use variables for reusable values
- Include outputs for important resources

**Formatting:**
```bash
terraform fmt -recursive terraform/
```

## Testing Requirements

All contributions must include appropriate tests:

### Unit Tests

- **Required** for all new code
- Aim for 80%+ code coverage
- Test edge cases and error conditions
- Use descriptive test names

**Java:**
```bash
mvn test
```

**Python:**
```bash
pytest tests/ --cov
```

### Integration Tests

- **Required** for API changes
- Test service interactions
- Use test containers when possible
- Clean up resources after tests

**Java:**
```bash
mvn verify
```

## Pull Request Review Process

1. **Automated checks** - CI pipeline must pass
2. **Code review** - At least one maintainer must approve
3. **Testing** - All tests must pass
4. **Documentation** - Update docs if needed
5. **Merge** - Maintainer will merge after approval

## Questions?

If you have questions about contributing, feel free to:

- Open a discussion on GitHub
- Ask in pull request comments
- Contact the maintainers

Thank you for contributing to MedRecord!
