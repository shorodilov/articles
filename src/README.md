# Source Content

This directory contains the main article content and supporting materials.
The structure is designed for a single-article workflow with modular
components.

## Initial Repository Structure

- `index.txt` - Master file for article build and distribution
- `README.md` - This documentation file

## Article Organization Approaches

This template supports two main approaches to organizing your article content:

### Single-File Approach

The simplest approach is to write your entire article in a single file:
- Use `index.txt` directly for your content
- Rename it to match your preferred format, or leave it "as is"
- Suitable for shorter articles or when maintaining a single narrative flow

### Modular Approach

For more complex articles, consider splitting content into multiple files:
- Use `index.txt` as a master file that references and assembles other
  components
- Create a `section/` directory with individual files for each article section
- Suitable for collaborative writing, longer articles, or content with distinct
  sections

## Content Format

This template supports various documentation formats:
- Markdown (.md)
- reStructuredText (.rst)
- LaTeX (.tex)
- Other formats as needed

Choose the format that best suits your workflow, toolchain, and publishing
requirements.

## Version Management

This repository uses Git for version control and document metadata for content
status.
Instead of maintaining separate draft directories, use frontmatter or document
metadata to indicate content status.

For Markdown:
```yaml
---
version: draft
---
```

For RST:
```rst
:version: draft
```

For LaTeX:
```latex
% !TEX version=draft
```

Possible version values:
- `draft` - Work in progress
- `review` - Ready for editorial review
- `final` - Approved for publication

## Content Organization

### Main Article

The `index.md` file serves as the primary article file or as an entry point
that assembles modular content. For shorter articles, all content may reside
in this file.

### Article Sections

The `section/` directory contains modular components of the article.
This approach is useful for:

- Breaking large articles into manageable pieces
- Allowing focused editing on specific sections
- Enabling collaborative work on different sections

### Research Materials

The article may include a `research/` directory to house supporting materials
such as:
- Preliminary notes
- Outlines and drafts
- Research findings
- Interview transcripts
- Background materials

This is optional and depends on your workflow and organizational preferences.

## Writing Guidelines

### File Naming

- Use descriptive, kebab-case filenames (e.g., `literature-review.md`)
- Avoid spaces and special characters in filenames
- Keep filenames concise but meaningful

### Markdown Usage

- Use standard Markdown syntax for consistency
- Apply proper heading hierarchy (H1 for title, H2 for major sections, etc.)
- Include frontmatter for metadata when appropriate
- Use relative links for references to other content and assets

### Content Standards

- Follow the established style guide for tone and formatting
- Include proper citations for all referenced sources
- Maintain consistent terminology throughout the article
- Consider accessibility in the content structure (proper headings,
  alt text for images etc.)
