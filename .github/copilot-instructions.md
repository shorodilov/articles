# GitHub Copilot Instructions

This is a publications repository containing articles, essays, reviews,
and other written content in plain text formats (primarily reStructuredText).

## Core Principles

**Simplicity over complexity.** Prefer straightforward solutions. Avoid
elaborate error handling, over-engineered abstractions, or unnecessary
automation. Clear logging and helpful error messages are sufficient.

**Best-effort maintenance.** This is a single-author repository. Do not
suggest complex workflows, CI/CD pipelines, or automation beyond what
already exists.

**Format flexibility.** The repository accepts any plain text format.
reStructuredText is primary, but Markdown and plain text are equally valid.

## Repository Structure

```
src/<publication>/          Publication source files
  index.*                   Main entry point (required)
  refs.bib                  Publication-specific bibliography (optional)
  metafile.yaml             Publication-specific metadata (optional)
  section/                  Content sections (optional)
  assets/                   Images, code, data (optional)
docs/                       Repository documentation
templates/                  Pandoc templates
csl/                        Citation Style Language files
```

## Guidelines

Follow these documents (located in `docs/`):

- **CONTRIBUTING.md** — contribution workflows and standards
- **CODE_OF_CONDUCT.md** — community standards and values
- **SUPPORT.md** — support expectations
- **SECURITY.md** — security policy

Follow formatting rules in `.editorconfig`:

- UTF-8 encoding
- LF line endings
- 4-space indentation (2 for YAML/JSON)
- 119-character line limit (79 for Markdown documentation)
- Final newline required

## Publication Source Validation

When reviewing or modifying publications, verify:

### Structure

- Each publication in `src/` has an `index` file (any plain text extension)
- Section files use descriptive names
- Assets are in the `assets/` subdirectory

### Cross-References

- Internal `.. include::` directives point to existing files
- Links and references resolve correctly
- Citation keys in text match entries in `refs.bib`

### Metadata

- If `metafile.yaml` exists, it contains valid YAML
- Required fields are present (title, author, date where applicable)

## BibTeX Validation

When working with `refs.bib` files:

- Check for duplicate citation keys (within file and across shared refs)
- Verify required fields per entry type:
  - `@article`: author, title, journal, year
  - `@book`: author/editor, title, publisher, year
  - `@online`: author/title, url, urldate
- Use consistent key naming (e.g., `author:year` or `source:topic`)

## Pull Request Review

When reviewing PRs, check:

1. **Formatting** — compliance with `.editorconfig`
2. **File placement** — correct directory structure
3. **Documentation** — README updates if needed
4. **Bibliography** — new citations properly formatted
5. **Cross-references** — no broken links or includes

## Content Standards

This repository maintains a clear stance against disinformation supporting
military aggression against Ukraine. When reviewing content:

- Flag any pro-war rhetoric or justification of aggression
- Ensure content respects the dignity of the Ukrainian people
- Report concerns per CODE_OF_CONDUCT.md

This applies to all content, including external contributions and references.

## License

All content is released under CC0 (public domain). Do not suggest adding
copyright notices or restrictive licenses.
