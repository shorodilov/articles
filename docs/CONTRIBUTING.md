# Contributing

Thank you for your interest in contributing to this repository!
This guide will help you understand how to contribute effectively.

## Welcome and Overview

This repository is a personal collection of technical articles and publications
maintained on a best-effort basis. We welcome various types of contributions,
including content suggestions, error corrections, external content proposals,
and improvements to the repository infrastructure.

Before participating, please read and follow our
[Code of Conduct][code-of-conduct].

**Important:** This is a single-author repository maintained in spare time.
While all contributions are appreciated, there are no commitments or
guarantees regarding response times or request fulfillment. Please set
realistic expectations and understand that not all requests can be addressed.

## Before You Contribute

Before submitting a contribution, please:

1. **Check Existing Issues** — Search for similar issues or requests that may
   already exist to avoid duplicates.

2. **Understand the Repository Structure** — Familiarize yourself with how
   content is organized. Publications are stored under `src/` with supporting
   build infrastructure.

3. **Read the README** — Review [README.md][readme] to understand the
   repository's purpose and scope.

4. **Set Realistic Expectations** — Remember that this is a best-effort
   project. Response times may vary, and not all requests can be fulfilled.

## Contribution Pathways

Choose the appropriate pathway for your contribution. Each pathway has a
corresponding issue template to guide you through the process.

### 3.1. Content Request

**Use this pathway when:** You want to suggest a new publication topic or
request coverage of a specific technical subject.

**How to contribute:**

1. Open a new issue using the "🎯 Content Request" template
2. Provide a clear topic title and detailed description
3. Explain why this content would be valuable
4. Include any relevant references or resources

**What to include:**

- Specific aspects of the topic that interest you
- Desired level of detail and scope
- Use cases or examples you'd like to see
- Rationale for why this publication would be valuable

**Note:** Content requests are evaluated based on relevance, feasibility, and
author expertise. There are no commitments to create requested content.

### 3.2. Content Fix

**Use this pathway when:** You've found errors, inaccuracies, or
misinformation in existing publications.

**How to contribute:**

For **simple corrections** (typos, formatting, minor clarity improvements):

- Submit a Pull Request directly with your fix
- Follow the PR guidelines in Section 4

For **significant issues** (factual errors, technical inaccuracies, outdated
information):

1. Open a new issue using the "✏️ Fix Content" template first
2. Identify the publication and specific location of the error
3. Provide the current content and your proposed correction
4. Include evidence or authoritative sources supporting your correction
5. Indicate severity (Minor, Moderate, or Major)

**What to include:**

- Publication name and location (section, paragraph, or line number)
- Quote of the incorrect content
- Proposed correction with supporting evidence
- Links to authoritative sources or documentation

### 3.3. External Content

**Use this pathway when:** You want to propose inclusion or reference to
external technical content from Git repositories.

**Requirements:**

- Content must exist in a Git repository
- License must be compatible with CC0 (see [LICENSE][license])
- Content must be relevant to this repository's scope
- Signed commits are preferred but optional

**How to contribute:**

1. Open a new issue using the "📚 External Content" template
2. Provide the content name and Git repository URL
3. Specify the content's license
4. Explain the content and its relevance to this repository

**What to include:**

- Name or title of the external content
- Git repository URL
- License information
- Description of topics covered and author information
- Explanation of why it's relevant and valuable

### 3.4. Build System Issue

**Use this pathway when:** You encounter problems building publications
locally.

**Note:** While the README indicates this repository is not primarily a
software project with a build system, some publications may use build tools
like make, pandoc, and LaTeX for document generation. Refer to
[README.md][readme] for detailed setup instructions if available.

**How to contribute:**

1. Open a new issue using the "🔧 Build System Issue" template
2. Describe the issue type (build fails, incorrect output, configuration issue,
   missing dependency, etc.)
3. Provide the command you ran and the complete error message
4. Include your environment information

**What to include:**

- Issue type and specific publication (if applicable)
- Command used and complete error output
- Environment details:
  - Operating system and version
  - Make version (if applicable)
  - Pandoc version (if applicable)
  - LaTeX distribution (if applicable)
- Steps you've already tried to resolve the issue

### 3.5. Build System Enhancement

**Use this pathway when:** You want to suggest improvements to the build
process, Makefile, templates, scripts, or configuration files.

**How to contribute:**

1. Open a new issue using the "⚙️ Build System Enhancement" template
2. Identify the component (Makefile, templates, scripts, configuration, etc.)
3. Describe the current behavior and proposed enhancement
4. Explain the benefits of your suggestion

**What to include:**

- Which component would be affected
- Description of current limitations
- Detailed explanation of the proposed improvement
- Benefits (performance, new capability, simplified workflow, etc.)
- Optional: Possible implementation approach or code snippets

### 3.6. Bug Report

**Use this pathway when:** You've found bugs in repository infrastructure,
build scripts, or other non-content components.

**Important:** This is for infrastructure bugs, not content errors. For
content errors in publications, use the "Content Fix" pathway instead.

**How to contribute:**

1. Open a new issue using the "🐛 Bug Report" template
2. Identify the component with the bug
3. Provide a clear description of the bug
4. Include steps to reproduce the issue

**What to include:**

- Component affected (Makefile, scripts, templates, configuration, etc.)
- Clear bug description
- Step-by-step reproduction instructions
- Expected vs. actual behavior
- Environment information (if relevant)
- Logs or error output

### 3.7. Question / Help

**Use this pathway when:** You have questions about repository content,
technical topics covered in publications, or need help understanding concepts.

**Note:** Support is provided on a best-effort basis. For detailed support
information, see [SUPPORT.md][support].

**How to contribute:**

1. Open a new issue using the "❓ Question / Help" template
2. Provide a clear description of your question
3. Include relevant context
4. Share what you've already tried (optional)

**What to include:**

- Clear and concise question
- Related publication (if applicable)
- Context about what you're trying to understand or accomplish
- What you've already researched or attempted

### 3.8. General / Other

**Use this pathway when:** You have feedback, suggestions, or want to discuss
something that doesn't fit into other categories.

**How to contribute:**

1. Check if your issue fits one of the specific templates first
2. If not, open a new issue using the "💬 General / Other" template
3. Describe what you'd like to share or discuss

**What to include:**

- Clear description of your feedback or suggestion
- Any relevant context or additional information

This template is for:

- General feedback about the repository
- Suggestions for improvement
- Discussions about direction or scope
- Anything else not covered by other templates

## Submitting Pull Requests

Pull requests are welcome for content fixes, documentation improvements, and
infrastructure enhancements. Follow these guidelines:

### Branch Naming Conventions

Use descriptive branch names that indicate the type and scope of your changes:

- `fix/content-<topic>` — For content corrections
- `docs/<description>` — For documentation changes
- `build/<description>` — For build system improvements
- `feature/<description>` — For new features or enhancements

Examples:

- `fix/content-rust-async-typo`
- `docs/update-installation-guide`
- `build/improve-makefile-targets`

### Commit Messages

Write clear, concise commit messages:

- Use present tense ("Add feature" not "Added feature")
- Use imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or fewer
- Reference issues and pull requests where appropriate

Examples:

- `Fix typo in introduction section`
- `Update bibliography with recent sources`
- `Improve error handling in build script`

### Signed Commits

Signed commits are **optional but appreciated**. They help verify the
authenticity of your contributions. If you're familiar with commit signing,
please use it. If not, unsigned commits are still accepted.

### PR Templates and Acknowledgment

When opening a pull request:

1. Use the appropriate PR template if one is available for your change type
2. Provide a clear description of what your PR does and why
3. Reference any related issues using keywords (e.g., "Fixes #42")
4. Acknowledge that you understand contributions are reviewed on a
   best-effort basis
5. Be patient — reviews may take time depending on maintainer availability

### Before Submitting

- Ensure your changes follow the formatting guidelines in
  [.editorconfig][editorconfig]
- Test your changes locally if applicable (especially for build-related
  changes)
- Keep changes focused and atomic — one PR per logical change
- Update documentation if your changes affect how things work

## Licensing

> [!IMPORTANT]
> All contributions to this repository are released under the project's
> [LICENSE][license].

By contributing, you agree to dedicate your contributions to the public domain
through CC0. This means:

- You **waive all copyright and related rights** to your contributions
- Your contributions can be freely used, modified, and distributed by anyone
- You provide no warranties for your contributions
- You give up any claim to attribution (though attribution is appreciated)

CC0 is the most permissive license possible, allowing anyone to use the
content for any purpose without restrictions. Please ensure you're comfortable
with this before contributing. If you're contributing external content, verify
that its license is compatible with CC0.

## Getting Help

If you need assistance or have questions about contributing, please see
[SUPPORT.md][support] for:

- Support expectations and response times
- Available support channels
- How to ask effective questions
- Additional resources

Thank you for contributing to this project! Your efforts help improve the
quality and accessibility of technical knowledge.

[readme]: /../main/README.md
[license]: /../main/LICENSE
[editorconfig]: /../main/.editorconfig
[code-of-conduct]: /../main/docs/CODE_OF_CONDUCT.md
[support]: /../main/docs/SUPPORT.md
