# BibTeX Validation

## File Locations

- `src/refs.bib` — shared references (repository-wide)
- `src/<publication>/refs.bib` — publication-specific references

Both are merged during build; publication-specific entries take precedence.

## Duplicate Detection

**Primary validation task:** Detect duplicate citation keys.

### Within Single File

```bibtex
% DUPLICATE - same key twice
@article{smith:2024,
    ...
}
@book{smith:2024,
    ...
}
```

### Across Files

Check for conflicts between:

- Publication-specific `refs.bib` and shared `src/refs.bib`
- Different publications (if cross-referenced)

### Resolution

When duplicates found:

1. Flag the duplicate entries
2. Suggest unique key names
3. Prefer descriptive keys: `author:year`, `source:topic-year`

## Entry Structure

### Required Fields by Type

| Type           | Required Fields                          |
|----------------|------------------------------------------|
| @article       | author, title, journal, year             |
| @book          | author OR editor, title, publisher, year |
| @online        | author OR title, url, urldate            |
| @inproceedings | author, title, booktitle, year           |
| @misc          | author OR title, year                    |

### Optional but Recommended

- `doi` — for articles and papers
- `url` — for online resources
- `urldate` — access date for online resources

## Formatting Guidelines

Follow existing style in repository:

```bibtex
@article{de:41.1,
    author = {First Last and Second Author},
    title = {Article Title},
    journal = {Journal Name},
    volume = {41},
    number = {1},
    pages = {6--25},
    year = {2020},
    doi = {10.1080/...},
    url = {https://...}
}
```

### Style Notes

- Use `{...}` for field values (not `"..."`)
- Separate multiple authors with ` and `
- Use `--` for page ranges
- Keep consistent indentation (4 spaces)
- End entries with closing `}`

## Common Issues

1. **Missing commas** between fields
2. **Unbalanced braces** in values
3. **Invalid characters** in keys (avoid spaces, special chars)
4. **Inconsistent key format** within same file
