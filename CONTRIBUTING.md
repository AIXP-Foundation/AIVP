# Contributing to AIVP

Thank you for your interest in contributing to the AI Value Protocol! This document provides guidelines for contributing to the project.

## How to Contribute

### Reporting Issues

- Use [GitHub Issues](https://github.com/AIXP-Foundation/AIVP/issues) to report bugs, suggest features, or propose specification changes
- For specification changes, use the `spec-change` issue template
- Provide clear descriptions with examples where possible

### Submitting Changes

1. **Fork** the repository
2. **Create a branch** from `main` for your changes
3. **Make your changes** following the guidelines below
4. **Commit** using [Conventional Commits](https://www.conventionalcommits.org/) format
5. **Submit a Pull Request** to `main`
6. **Wait for review** from maintainers

### Specification Changes

Changes to normative content (anything in `specification/`) require:

1. An issue with the `spec-change` label describing the proposed change
2. A minimum 14-day discussion period for non-trivial changes
3. An Architecture Decision Record (ADR) in `adrs/` for significant decisions
4. Axiom 0 compliance review by maintainers
5. Updated documentation reflecting the change
6. **Both EN and CN versions must be updated simultaneously**

### Documentation Changes

Changes to non-normative content (guides, topics, examples) follow a lighter process:

1. Submit a pull request with your changes
2. Ensure content aligns with Axiom 0 and the Dignity Standard
3. One maintainer approval required for merge

## Guidelines

### Writing Style

- Use clear, concise language
- Follow the existing document structure and formatting
- All content values must be in human language (no opaque codes or machine-only tokens)
- Default language is English; Chinese translations should follow promptly

### Axiom 0 Compliance

Every contribution must comply with Axiom 0: Human Sovereignty and Wellbeing. Specifically:

- Changes must not weaken human oversight of AI commercial interactions
- Changes must not enable AI agents to circumvent transparency requirements
- Changes must not compromise the Dignity Standard

### Commit Message Format

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

Types: `feat`, `fix`, `docs`, `spec`, `refactor`, `test`, `chore`

Examples:
- `spec(trust): add V4 Premier trust level stake requirements`
- `docs(guide): add getting started guide for contract creation`
- `fix(spec): correct CONTRACT_PROPOSE message format example`

### Bilingual Requirements

For specification changes:
- English version (`specification/AIVP_Protocol.md`) and Chinese version (`specification/AIVP_Protocol_cn.md`) must be updated in the same PR
- Axiom 0 in Chinese: "人类主权与福祉" (never abbreviated)
- Maintain consistent terminology — refer to `docs/reference/glossary.md`

## Development Setup

### Prerequisites

- Git
- Python 3.8+ (for MkDocs documentation site)
- MkDocs Material theme (`pip install mkdocs-material`)

### Building Documentation

```bash
# Install dependencies
pip install mkdocs-material

# Serve locally
mkdocs serve

# Build static site
mkdocs build
```

## Questions?

- Open a [GitHub Discussion](https://github.com/AIXP-Foundation/AIVP/discussions) for general questions
- For private inquiries, open a [Security Advisory](https://github.com/AIXP-Foundation/AIVP/security/advisories/new)

---

Align Axiom 0: Human Sovereignty and Wellbeing. Version: AIVP V1.0.0. www.aivp.dev
