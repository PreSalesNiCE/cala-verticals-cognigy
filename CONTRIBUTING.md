# Contributing Guide

Thank you for wanting to contribute! This guide explains how to add new verticals, improve existing ones, and report issues.

---

## 📋 Table of Contents

- [Getting Started](#getting-started)
- [Types of Contributions](#types-of-contributions)
- [Adding a New Vertical](#adding-a-new-vertical)
- [Modifying an Existing Vertical](#modifying-an-existing-vertical)
- [Pull Request Process](#pull-request-process)
- [Code of Conduct](#code-of-conduct)
- [Questions & Support](#questions--support)

---

## Getting Started

### Prerequisites

- GitHub account
- Cognigy instance (v5.0+)
- Basic understanding of git/GitHub
- Familiarity with Cognigy flows (for development)

### Fork & Clone

```bash
# 1. Fork repository (GitHub UI)
# 2. Clone your fork
git clone https://github.com/your-username/ai-agents-demo.git
cd ai-agents-demo

# 3. Add upstream remote
git remote add upstream https://github.com/original-repo/ai-agents-demo.git

# 4. Create feature branch
git checkout -b feature/your-feature-name
```

---

## Types of Contributions

### 1. Report Bugs 🐛

**Use:** [Bug report template](./.github/ISSUE_TEMPLATE/bug_report.md)

```bash
# Create issue on GitHub with template
# Title: [BUG] - Brief description
# Include: Steps, expected, actual behavior, screenshots
```

### 2. Request Features ✨

**Use:** [Feature request template](./.github/ISSUE_TEMPLATE/feature_request.md)

```bash
# Create issue describing:
# - What feature
# - Why it's needed
# - How it helps
# - Expected impact
```

### 3. Propose New Vertical 📊

**Use:** [New vertical template](./.github/ISSUE_TEMPLATE/new_vertical.md)

```bash
# Propose industry + use cases
# Include: Business case, timeline, resources
```

### 4. Add New Vertical 🚀 (See below)

### 5. Improve Documentation 📚

```bash
# Fix typos, improve clarity, add examples
# Update CHANGELOG with your changes
```

---

## Adding a New Vertical

### Step 1: Prepare Your Vertical

**Create folder structure:**

```bash
mkdir -p verticals/[industry]/[demo-name]/{packages,assets/{screenshots,docs,demo-scripts}}
```

**Example:**

```bash
mkdir -p verticals/hospitality/hotel-booking/{packages,assets/{screenshots,docs,demo-scripts}}
```

### Step 2: Build in Cognigy

1. Create flows in your Cognigy instance
2. Test all conversation paths
3. Verify integrations
4. Test on mobile
5. Record conversation examples

### Step 3: Export Packages

For each language (PT-BR, ES):

1. In Cognigy → Settings → Packages
2. Click "Export"
3. Name: `[demo-name]-[language]-v1.0.zip`
4. Save to: `verticals/[industry]/[demo-name]/packages/`

**Files:**

```
packages/
├── hotel-booking-pt-br-v1.0.zip
├── hotel-booking-es-v1.0.zip
└── hotel-booking-en-v1.0.zip
```

### Step 4: Create Documentation

**README.md** - Use [template](./templates/VERTICAL-README-TEMPLATE.md)

```bash
cp templates/VERTICAL-README-TEMPLATE.md verticals/hospitality/hotel-booking/README.md
# Edit with your vertical info
```

**CHANGELOG.md** - Track versions

```markdown
## [1.0.0] - 2025-05-04
### Added
- Initial release
- [List features]
```

### Step 5: Create Assets

**Screenshots** (in `assets/screenshots/`)

- 01-flow-diagram.png
- 02-welcome-message.png
- 03-main-interaction.png
- 04-form-xapp.png
- 05-confirmation.png
- README.md (describe each)

**Conversation flows** (in `assets/docs/`)

```markdown
# Conversation Flows - [Demo Name]

## Flow 1: Welcome & Intent

User: "..."
Agent: "..."
User: "..."
Agent: "..."

## Flow 2: Main Feature

[Similar structure]
```

**Demo script** (in `assets/demo-scripts/`)

```markdown
# Demo Script - [Demo Name]

Duration: 15 minutes
Audience: Pre-sales

## Opening (1 min)
[Script]

## Demo 1 (7 min)
[Script]

## Q&A (2 min)
[Q&A]
```

### Step 6: Create Industry Index

**verticals/[industry]/[industry]-README.md**

```markdown
# [Industry] Vertical

Collection of AI Agent demos for [industry].

## Available Demos

### 1. [Demo Name]
[Description]
- Languages: PT, ES, EN
- Status: Production Ready
- [→ View Demo](./[demo-name]/README.md)

## Getting Started

1. Choose a demo above
2. Read its README
3. Follow installation
4. Use demo script
```

### Step 7: Submit Pull Request

```bash
# Commit changes
git add verticals/[industry]/[demo-name]
git commit -m "feat: Add [Industry] vertical - [Demo Name]"

# Push to your fork
git push origin feature/[industry]-vertical

# Create PR on GitHub
# Use PULL_REQUEST_TEMPLATE.md
```

---

## Modifying an Existing Vertical

### For Bug Fixes

1. Test the bug locally
2. Fix in Cognigy
3. Export new package
4. Update version in CHANGELOG (PATCH)
5. Update README if needed
6. Submit PR

### For New Features

1. Build feature in Cognigy
2. Export new package
3. Update CHANGELOG (MINOR version)
4. Update documentation
5. Add conversation examples
6. Add/update screenshots
7. Submit PR

### For Language Addition

1. Create flows for new language
2. Export new package: `[name]-[language]-v1.0.zip`
3. Update README (languages supported)
4. Update CHANGELOG
5. Test everything
6. Submit PR

### Version Bumping

Follow [Semantic Versioning](https://semver.org/):

- **PATCH** (1.0.X) → Bug fixes, small improvements
- **MINOR** (1.X.0) → New features, backwards compatible
- **MAJOR** (X.0.0) → Breaking changes

Example:
```markdown
## [1.1.0] - 2025-06-04

### Added
- New feature X
- Language Y support

### Fixed
- Bug Z

### Changed
- Updated conversation flow
```

---

## Pull Request Process

### Before Submitting

- [ ] Tested in Cognigy sandbox
- [ ] All flows working correctly
- [ ] Mobile tested (if XApp)
- [ ] All languages tested
- [ ] Screenshots added
- [ ] Documentation complete
- [ ] CHANGELOG updated
- [ ] No breaking changes

### PR Checklist (in template)

```markdown
## 📝 Description
[Brief summary]

## 🎯 Type of Change
- [ ] New vertical
- [ ] Vertical improvement
- [ ] Bug fix
- [ ] Documentation

## ✅ Testing
- [ ] Tested in Cognigy
- [ ] All flows verified
- [ ] Mobile tested
- [ ] Languages tested

## 📋 Checklist
- [ ] README updated
- [ ] CHANGELOG updated
- [ ] Version bumped
- [ ] Assets included
- [ ] Links working
```

### Review Process

1. **Automated checks** - Format, structure
2. **Manual review** - Functionality, quality
3. **Testing** - Cognigy import, conversation flows
4. **Approval** - Maintainer review
5. **Merge** - Into main branch

### Expected Timeline

- Simple bug fix: 2-3 days
- New feature: 3-5 days
- New vertical: 1-2 weeks

---

## Standards & Best Practices

### Naming Conventions

**Verticals:**
```
verticals/[industry]/[demo-name]/
Examples:
verticals/insurance/one-seguro/
verticals/hospitality/hotel-booking/
```

**Packages:**
```
[demo-name]-[language]-v[version].zip
Examples:
one-seguro-pt-br-v1.0.zip
hotel-booking-es-v1.1.zip
```

**Branches:**
```
feature/[feature-name]
fix/[bug-description]
docs/[documentation-update]
Examples:
feature/hospitality-vertical
fix/voice-recognition-bug
docs/installation-guide
```

### Documentation Standards

- **Clear language** - Avoid jargon
- **Examples included** - Show real scenarios
- **Screenshots** - Visual reference
- **Conversation flows** - Real examples
- **Demo scripts** - Ready to present
- **Up-to-date** - Current version info

### Code Quality (Cognigy Flows)

- ✅ No unused nodes
- ✅ Clear node naming
- ✅ Proper error handling
- ✅ Sensible conversation flow
- ✅ Mobile responsive (XApp)
- ✅ All languages tested

### Testing Checklist

Before submitting:

```
Voice Channel:
- [ ] Intent detection works
- [ ] Asks contextual follow-ups
- [ ] Handles natural language
- [ ] Escalates appropriately
- [ ] Confirms information

Web Channel:
- [ ] Form loads quickly
- [ ] Mobile responsive
- [ ] Validation works
- [ ] File upload functions
- [ ] Confirmation displays

All Channels:
- [ ] Portuguese works
- [ ] Spanish works
- [ ] English works
- [ ] No console errors
- [ ] No timeout issues
```

---

## File Size Guidelines

- **Vertical package (.zip):** Max 50 MB
- **Screenshot (image):** Max 2 MB each
- **Documentation (markdown):** No limit

---

## Commit Message Format

```
type(scope): brief description

[optional body]

[optional footer]
```

Examples:

```
feat(insurance): add claims processor vertical
fix(one-seguro): resolve voice recognition issue
docs(installation): improve step-by-step guide
```

**Types:** feat, fix, docs, style, refactor, test, chore

---

## Questions & Support

### Before Contributing

- Review [README.md](./README.md)
- Check [existing issues](https://github.com/your-repo/issues)
- Read [FAQ](./docs/FAQ.md)
- See [Best Practices](./docs/BEST-PRACTICES.md)

### Need Help?

1. **Creating vertical?** → See [VERTICAL-README-TEMPLATE.md](./templates/VERTICAL-README-TEMPLATE.md)
2. **Cognigy questions?** → Check [INSTALLATION-GUIDE.md](./docs/INSTALLATION-GUIDE.md)
3. **Demo tips?** → See [DEMO-SCRIPT-TEMPLATE.md](./docs/DEMO-SCRIPT-TEMPLATE.md)
4. **Still stuck?** → Create GitHub discussion

### Contact

- **Email:** support@your-company.com
- **Issues:** [GitHub Issues](https://github.com/your-repo/issues)
- **Discussions:** [GitHub Discussions](https://github.com/your-repo/discussions)

---

## 📄 Code of Conduct

### Our Pledge

We're committed to providing a welcoming, inclusive environment.

### Expected Behavior

- ✅ Be respectful and inclusive
- ✅ Welcome diverse perspectives
- ✅ Give credit where due
- ✅ Provide constructive feedback
- ✅ Focus on collaboration

### Unacceptable Behavior

- ❌ Harassment or discrimination
- ❌ Offensive comments
- ❌ Personal attacks
- ❌ Unwelcome advances
- ❌ Any form of bullying

---

## Recognition

### Contributors

Contributors will be recognized:
- In CHANGELOG
- In vertical README (if requested)
- Monthly contributor highlights

### Licensing

By contributing, you agree your work is licensed under our [LICENSE](./LICENSE).

---

## Common Questions

**Q: Can I contribute without Cognigy experience?**
A: Yes! You can help with documentation, screenshots, or ideas.

**Q: How long does review take?**
A: Simple fixes: 2-3 days. New verticals: 1-2 weeks.

**Q: Can I update multiple languages at once?**
A: Yes. Include all 3 language packages in one PR.

**Q: Do I need to be an employee?**
A: No! Open source contributions welcome.

---

## Thank You! 🙏

Your contributions help make this project better for everyone. We appreciate your effort!

---

**Last Updated:** May 4, 2025  
**Maintained by:** [Your Team]