# Contributing Guide

## Table of Contents

- [Overview](#overview)
- [Getting Started](#getting-started)
- [Adding a New Vertical](#adding-a-new-vertical)
- [Modifying an Existing Vertical](#modifying-an-existing-vertical)
- [Versioning](#versioning)
- [Pull Request Process](#pull-request-process)
- [Guidelines](#guidelines)
- [Code of Conduct](#code-of-conduct)
- [Questions & Support](#questions--support)

---

## Overview

This repository is designed to evolve with new demos and improvements.

We welcome contributions that include:

- Improving existing verticals
- Fixing bugs in flows
- Adding new industry demos
- Enhancing documentation
- Language variations
- Performance optimizations

All contributions help make our AI Agent demos more comprehensive and useful for the community.

---

## Getting Started

### Prerequisites

Before you contribute, ensure you have:

- A GitHub account
- Git installed on your machine
- A Cognigy account with package export capabilities
- Familiarity with Cognigy flow design

### Fork & Clone

1. **Fork this repository** to your GitHub account
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/ai-agents-demo.git
   cd ai-agents-demo
   ```

3. **Add upstream remote** (to sync with main repo):
   ```bash
   git remote add upstream https://github.com/original-owner/ai-agents-demo.git
   ```

4. **Create a new branch** for your work:
   ```bash
   git checkout -b feature/your-feature-name
   ```

---

## Adding a New Vertical

### Step 1: Create the Folder Structure

Create a new folder in the root directory with a clear, descriptive name:

```
/hospitality-vertical
   /hospitality-en
   /hospitality-pt
   /hospitality-es
   README.md
```

Or for simpler verticals:

```
/healthcare-vertical
   healthcare-package.zip
   README.md
```

### Step 2: Prepare Your Package

1. **Design your flow** in Cognigy
2. **Export the package** as a `.zip` file:
   - Open Cognigy → Settings → Packages
   - Click Export
   - Save with a clear name (e.g., `hospitality-booking-v1.0.zip`)
3. **Place the `.zip` file** in your vertical folder

### Step 3: Create a README

Each vertical must include a `README.md` describing:

- **Vertical Name** - Clear industry/use case
- **Description** - What problem it solves
- **Use Cases** - Specific scenarios covered
- **Flows Included** - List of available flows
- **Languages Supported** - pt-BR, es, en, etc.
- **Installation Instructions** - How to import
- **Features** - Key capabilities
- **Version History** - Version and date
- **Author** - Your name/team

**Example:**

```markdown
# Hospitality Booking Vertical

## Description
AI Agent for hotel and restaurant reservation management.

## Use Cases
- Hotel room booking
- Restaurant table reservation
- Guest support inquiries
- Cancellation and modifications

## Languages Supported
- English (en)
- Portuguese (pt-BR)
- Spanish (es)

## Version
- Version: 1.0
- Last Updated: 2025-05-04
- Author: Your Name
```

### Step 4: Include Assets (Optional)

Add relevant files to your vertical folder:

```
/your-vertical-name
   /assets
      logo.png
      sample-conversation.md
      use-case-diagram.png
   README.md
   your-vertical-package.zip
```

### Step 5: Commit and Push

```bash
git add your-vertical-name/
git commit -m "feat: Add hospitality vertical with booking flows"
git push origin feature/hospitality-vertical
```

---

## Modifying an Existing Vertical

### For Small Changes

1. **Make changes in Cognigy** directly
2. **Export the updated package**
3. **Replace the existing `.zip`** file:
   ```bash
   rm old-package.zip
   cp new-package.zip .
   ```
4. **Update the version** in the vertical README
5. **Add changelog entry**:
   ```
   ## Version History
   
   - **v1.1** (2025-05-04) - Improved conversation flow, fixed fallback handling
   - **v1.0** (2025-04-20) - Initial release
   ```
6. **Commit your changes**:
   ```bash
   git add vertical-name/
   git commit -m "fix: Improved fallback handling in hospitality flow"
   git push origin fix/hospitality-fallback
   ```

### For Major Changes

1. **Create a new branch**:
   ```bash
   git checkout -b feature/hospitality-v2-redesign
   ```
2. **Make comprehensive changes** in Cognigy
3. **Test thoroughly** before exporting
4. **Export new package** with version bump
5. **Update README** with new features and breaking changes
6. **Create detailed commit message**:
   ```bash
   git commit -m "feat: Redesign hospitality flow with new booking logic
   
   - Improved conversation flow structure
   - Added multi-language support improvements
   - Fixed edge cases in reservation handling
   - Version bumped from 1.0 to 2.0
   "
   ```

---

## Versioning

### Version Format

Use semantic versioning: `MAJOR.MINOR.PATCH`

- **MAJOR** - Breaking changes or significant redesign
- **MINOR** - New features or improvements
- **PATCH** - Bug fixes

### Changelog Format

In each vertical's README, maintain a version history:

```markdown
## Version History

- **v1.2.1** (2025-05-04)
  - Fixed: Typo in greeting message
  - Fixed: Improved form validation

- **v1.2.0** (2025-05-01)
  - Added: Multi-language support for Spanish
  - Improved: Conversation flow logic
  - Fixed: Fallback handling in edge cases

- **v1.1.0** (2025-04-20)
  - Added: Document upload capability
  - Improved: User experience in forms

- **v1.0.0** (2025-04-01)
  - Initial release
```

### When to Update Version

- **Every package export** - Update PATCH or MINOR
- **When adding features** - Update MINOR
- **When breaking flows** - Update MAJOR
- **For bug fixes** - Update PATCH

---

## Pull Request Process

### Before You Start

1. **Sync your fork** with the main repository:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Create a descriptive branch name**:
   - `feature/vertical-name` - For new verticals
   - `fix/issue-description` - For bug fixes
   - `docs/update-description` - For documentation
   - `improvement/flow-name` - For enhancements

### Making Your PR

1. **Push your branch** to your fork:
   ```bash
   git push origin your-branch-name
   ```

2. **Open a Pull Request** on GitHub with:
   - **Clear title**: "Add hospitality vertical" or "Fix fallback in insurance flow"
   - **Detailed description** including:
     - What changes were made
     - Why they were made
     - Files affected
     - Testing done
     - Screenshots or demos (if applicable)

### PR Description Template

```markdown
## Description
Brief explanation of what this PR does.

## Type of Change
- [ ] New vertical added
- [ ] Existing vertical improved
- [ ] Bug fix
- [ ] Documentation update
- [ ] Performance improvement

## Changes Made
- Change 1
- Change 2
- Change 3

## Testing
- [ ] Tested in Cognigy sandbox
- [ ] All flows working correctly
- [ ] Conversation flows tested
- [ ] Edge cases verified

## Related Issues
Closes #123

## Screenshots (if applicable)
Add screenshots or conversation transcripts here.
```

### Review Process

- A maintainer will review your PR
- Feedback may be provided for improvements
- Once approved, your PR will be merged
- Your contribution will be acknowledged in the repo

---

## Guidelines

### Flow Design

- **Keep it simple**: Focus on core use cases
- **Be clear**: Conversation should be natural and easy to follow
- **Test thoroughly**: Before exporting, test all paths
- **Avoid complexity**: Save advanced features for future versions

### Package & Naming

- **Use clear names**: `hospitality-booking-v1.0.zip` (not `file123.zip`)
- **Include versions**: Always version your packages
- **Document changes**: Update README with each change
- **Organize files**: Use subfolders for languages/variations

### Documentation

- **Write good READMEs**: Clear use cases and installation steps
- **Add examples**: Include conversation flow examples
- **Document features**: List what the vertical can do
- **Include screenshots**: Show UI elements and flows

### Code Quality

- **Test before submitting**: Ensure everything works
- **Avoid breaking changes**: Unless absolutely necessary
- **Maintain consistency**: Follow existing patterns
- **Clean up assets**: Remove test files before pushing

### Commit Messages

Write clear, descriptive commit messages:

```bash
# Good
git commit -m "feat: Add hotel booking flow to hospitality vertical"

# Also good
git commit -m "fix: Resolve conversation fallback issue in restaurant booking

- Fixed edge case where fallback wasn't triggered
- Improved error handling in form validation
- Tested with 10+ conversation scenarios"

# Avoid
git commit -m "fixed stuff"
git commit -m "update"
```

---

## Code of Conduct

We are committed to providing a welcoming and inclusive environment.

### Our Pledge

We pledge to make participation in this project a harassment-free experience for everyone, regardless of:
- Age
- Body size
- Disability
- Ethnicity
- Gender identity
- Level of experience
- Nationality
- Personal appearance
- Race
- Religion
- Sexual identity and orientation

### Our Standards

Examples of behavior that contributes to a positive environment:

- Using welcoming and inclusive language
- Being respectful of differing opinions
- Accepting constructive criticism gracefully
- Focusing on what is best for the community
- Showing empathy toward other community members

Examples of unacceptable behavior:

- Harassment or discrimination
- Insulting or derogatory comments
- Private attacks
- Publishing private information without consent
- Other conduct considered inappropriate

### Enforcement

Unacceptable behavior will not be tolerated. Violations may result in:
- Warnings
- Temporary or permanent ban from the project

---

## Questions & Support

### Getting Help

If you have questions or need support:

1. **Check existing issues** - Your question might already be answered
2. **Review the main README** - Common questions may be covered
3. **Open a Discussion** - Use GitHub Discussions for general questions
4. **Create an Issue** - For bugs or specific problems

### Asking Good Questions

When asking for help:

- **Be specific**: Describe what you're trying to do
- **Provide context**: Share relevant files or screenshots
- **Show what you've tried**: Explain troubleshooting steps taken
- **Be patient**: Wait for responses and provide follow-up info if needed

### Reporting Bugs

When reporting bugs:

- **Use the bug template**: Follow the issue template
- **Include reproduction steps**: Exactly how to reproduce the issue
- **Provide screenshots**: Visual evidence helps
- **Specify vertical**: Which vertical and version is affected
- **Include error messages**: Copy exact error text

---

## Additional Resources

### Learning Resources

- [Cognigy Documentation](https://docs.cognigy.com)
- [Git & GitHub Guide](https://guides.github.com)
- [Semantic Versioning](https://semver.org)
- [Conventional Commits](https://www.conventionalcommits.org)

### Repository Resources

- [Main README](README.md)
- [Issues](https://github.com/cala-verticals-cognigy/issues)
- [Discussions](https://github.com/cala-verticals-cognigy/discussions)

---

## Thank You!

Thank you for considering contributing to this project. Your efforts help make our AI Agent demos better for everyone!

---

**Last Updated:** May 4, 2025  
**Version:** 1.0  
**Maintained by:** CALA Solutions Engineering Team
