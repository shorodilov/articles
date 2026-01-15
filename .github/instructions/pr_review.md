# Publication Source Consistency

## Directory Structure

Each publication lives in `src/<publication-name>/` and must follow:

```
src/<publication-name>/
  index.*           Main entry point (REQUIRED, any plain text format)
  refs.bib          Publication-specific references (optional)
  metafile.yaml     Publication-specific metadata (optional)
  README.*          Publication notes (optional)
  section/          Content sections (optional)
  assets/           Images, code, data files (optional)
```

## Structure Validation

When validating publication structure:

### Required Elements

- Every publication MUST have an `index` file at its root
- File extension can be `.rst`, `.md`, `.txt`, or other plain text

### Naming Conventions

- Publication directories: lowercase with hyphens (`my-article-name`)
- Section files: descriptive names matching content
- No strict convention — author's discretion applies

### Common Issues

- Missing index file
- Assets placed outside `assets/` directory
- Inconsistent naming within a publication

## Cross-Reference Validation

### Include Directives (reStructuredText)

Check `.. include::` directives:

```rst
.. include:: section/10-intro.txt
```

- Target file must exist at the specified path
- Path is relative to the including file
- File extension must match actual file

### Internal Links

- Verify link targets exist
- Check for broken anchor references
- Ensure relative paths are correct

### Citation References

- Citation keys in text must exist in `refs.bib`
- Check both publication-specific and shared (`src/refs.bib`) references
- Format: `:cite:'key'` or `[@key]` depending on format

## Metadata Validation

### metafile.yaml

If present, verify:

- Valid YAML syntax
- Common fields: title, author, date, abstract
- No duplicate keys

### Frontmatter

Source files may contain frontmatter:

- YAML frontmatter in Markdown (between `---` markers)
- Field definitions in reStructuredText (`:field: value`)

Frontmatter takes precedence over metafile.yaml.

## Shared Resources

Located in repository root:

- `src/refs.bib` — shared bibliography
- `src/metafile.yaml` — shared metadata defaults
- `templates/` — Pandoc templates
- `csl/` — citation styles

Publication-specific files override shared resources.
