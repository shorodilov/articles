# Junie Guidelines

## Scope

Junie handles **coding tasks only** in this repository:

- Makefile development and maintenance
- Build scripts
- Automation scripts
- Configuration files
- GitHub Actions workflows

**Out of scope:**
Content authoring, publication structure, documentation prose.

## Core Principle

**Simplicity over complexity.**

- Prefer straightforward implementations
- No elaborate error handling — clear logging and messages suffice
- Avoid over-engineering
- Minimize dependencies

## Build System Context

The repository uses:

- **Make** (GNU Make 4.0+) — build automation
- **Pandoc** (3.x) — format transformation
- **LaTeX** (TeX Live) — PDF generation (optional)

### Makefile Conventions

```makefile
# Use tabs for indentation (per .editorconfig)
# Keep targets simple and focused
# Prefer built-in Make features over shell complexity

.PHONY: all clean

all: $(PUBLICATIONS)

clean:
	rm -rf $(OUTPUT_DIR)
```

### Error Handling

- Clear error messages with context
- Color-coded output if terminal supports it
- Pre-build checks for dependencies
- Proper exit codes (0 success, non-zero failure)
- **No** retry mechanisms
- **No** automatic recovery
- **No** complex fallback strategies

## Formatting Standards

Follow `.editorconfig`:

- Makefiles: tabs for indentation
- Shell scripts: 4-space indentation
- YAML/JSON: 2-space indentation
- Line length: 119 characters max
- UTF-8 encoding, LF line endings
- Final newline required

## Shell Scripts

If creating shell scripts:

```bash
#!/usr/bin/env bash
set -euo pipefail

# Clear, descriptive variable names
# Comment non-obvious logic
# Exit with meaningful codes
```

## GitHub Actions

For workflow files in `.github/workflows/`:

- Keep workflows focused (one purpose per workflow)
- Use specific action versions (not `@latest`)
- Minimize secrets and permissions
- Include clear job names

## Testing Approach

- Manual testing is acceptable
- No requirement for automated tests
- Document test procedures in comments if complex

## Dependencies

Before adding dependencies:

1. Is it necessary?
2. Is it commonly available in package managers?
3. Does it follow the simplicity principle?

Prefer standard Unix tools over specialized packages.

## Documentation

For code changes:

- Update inline comments
- Update README if user-facing behavior changes
- Keep documentation minimal but sufficient
