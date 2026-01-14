> [!IMPORTANT]
>
> This document describes the Proof of Concepts for the repository structure.
> It does not contain requirements or any rules to follow.

## 1. Purpose and Scope

### 1.1 Primary Purpose

- Primary storage for publications authored by the repository owner
- Maintain an archive of articles and associated code snippets
- Facilitate easy reference and sharing of published work

### 1.2 Content Types

- Mixed publication types with no dedicated format:
    - Technical articles
    - Research papers
    - Blog posts
    - Tutorials
    - Code snippets and examples
    - Any other written content

### 1.3 Out of Scope

- Publishing platform (no automated web publishing)
- Co-authoring workflow (single author model)
- Complex metadata tracking systems

## 2. Repository Structure

### 2.1 Organization

#### 2.1.1 Directory Structure

```
repo-root/
  .github/              # GitHub configuration (workflows, templates)
  src/                  # Source publications and shared resources
    refs.bib            # Shared references database
    metafile.yaml       # Shared metadata and configurations
    <publication-name>/ # Individual publication
      index             # Main entry point (required, any plain text format)
      refs.bib          # Publication-specific references (optional)
      metafile.yaml     # Publication-specific metadata (optional)
      README            # Publication description and notes (optional)
      <section-name>/   # Content sections (optional)
        ...             # Section files
      assets/           # Images, code, data files (optional)
  templates/            # Shared pandoc templates
    default.latex
    default.openxml
    ...
  csl/                  # Citation Style Language files (shared)
  docs/                 # Supporting documentation
    PROOF_OF_CONCEPT.md # This document
    CODE_OF_CONDUCT.md  # Community code of conduct
    CONTRIBUTING.md     # Contribution guidelines
    SECURITY.md         # Security policy
    SUPPORT.md          # Support information
  Makefile              # Root build system
  Taskfile.yml          # Alternative build system
  dist/                 # Build outputs (default, gitignored)
  README.md
  LICENSE
  .editorconfig
  .gitignore            # Excludes: dist/, public/, build/, out/
  .gitmodules
```

**Note**:

- Square brackets in examples denote optional items
- The output directory (`dist/` by default) and its common alternatives are
  excluded from version control
- Each publication must have an `index` file as its main entry point
- Community health files are stored in `docs/` for better organization

#### 2.1.2 Publication Structure

Each publication in `src/` follows this pattern:

```
src/<publication-name>/
  index                 # Main entry point (required, any plain text format)
  refs.bib              # Publication-specific references (optional)
  metafile.yaml         # Publication-specific metadata (optional)
  README                # Publication description and notes (optional)
  <section-name>/       # Content sections (optional)
    ...                 # Section files
  assets/               # Images, code, data files (optional)
```

**Key points**:

- `index` file at publication root is the main entry point (required)
- `README` file can document publication-specific information (optional)
- `<section-name>/` directories organize multi-part content (optional)
- Sections can have their own `index` entry points (optional)
- `assets/` contains all publication-specific resources (optional)
- Simple publications may have only an `index` file

#### 2.1.3 Resource Sharing

**Shared resources** (in `src/` root):

- `src/refs.bib` - Shared references database
- `src/metafile.yaml` - Shared metadata and configurations
- `templates/` - Pandoc templates (repository root)
- `csl/` - Citation Style Language files (repository root)

**Per-publication resources** (in `src/<publication-name>/`):

- `index` - Main entry point (required)
- `README` - Publication description and notes (optional)
- `refs.bib` - Publication-specific references (optional, merged with shared)
- `metafile.yaml` - Publication-specific metadata (optional, overrides shared)
- `<section-name>/` - Content sections (optional)
- `assets/` - All publication-specific resources (optional)

**Resolution order**:

1. Build system reads `src/<publication-name>/index` as entry point
2. Loads shared resources from `src/refs.bib` and `src/metafile.yaml`
3. If publication has its own `refs.bib`, both are merged
4. If publication has its own `metafile.yaml`, it overrides/extends shared
   metadata
5. Frontmatter in source files takes final precedence

### 2.2 Naming Conventions

- **Publication directories**: lowercase with hyphens (e.g., `article-01`,
  `my-topic-name`)
    - Use descriptive names that reflect content
    - Numeric prefixes optional (e.g., `01-intro`, `02-advanced`)
- **Source files**: descriptive names matching content
    - `index` - main entry point (required for each publication)
    - Other files: descriptive names (e.g., `introduction`, `chapter1`,
      `conclusion`)
    - Use the most appropriate plain text format extension (`.rst`, `.md`,
      `.txt`, etc.)
    - File extensions identify the format but are not prescribed
    - No strict convention - author's discretion
- **Directories**:
    - `<section-name>/` - for organizing multi-part content (optional)
        - Use descriptive names (e.g., `introduction/`, `methodology/`,
          `results/`)
    - `assets/` - for images, code, data files (optional)
- **Output directory**: Configurable via Makefile variable
    - Default: `dist/`
    - Can be overridden (e.g., `make OUTPUT_DIR=public all`)
    - Common alternatives: `public/`, `build/`, `out/`

**Note**: Naming conventions are intentionally flexible to accommodate diverse
publication types and source formats.

### 2.2 File Formats

#### 2.2.1 Format Philosophy

- **Format-agnostic**: The repository must support any plain text format
- Input formats are always plain text (rst, md, txt, etc.)
- No binary formats for source content

#### 2.2.2 Supported Input Formats

- **Primary format**: reStructuredText (`.rst`)
    - Recommended for new publications
    - Most feature-rich for technical documentation
- **Also supported**: Markdown (`.md`), plain text (`.txt`), and other plain
  text formats
    - Each publication uses the format most suitable for its content
    - Many external publications will be in Markdown
    - No format conversion required – use source formats directly

**Philosophy**: The repository is truly format-agnostic. While reStructuredText
is preferred for new content, any plain text format is acceptable. Pandoc
handles all conversions transparently.

#### 2.2.3 Format Transformation

- Use `pandoc` for format conversions
- Build system must handle multiple input formats

## 3. Metadata and Documentation

### 3.1 Article Metadata

- Not applicable: No special metadata tracking required
- Standard git metadata (commit history, dates) is enough for versioning

### 3.2 Index/Catalog

- Optional: Auto-generated publication index (long-term feature)
- Git directory structure provides a basic catalog

### 3.3 README.md Guidelines

#### 3.3.1 Repository README (root level)

The main README.md should include:

**Required sections**:

- **Title and description**: Brief overview of repository purpose
    - "A collection of publications primarily authored by [author]"
    - Explain the single-repository approach
- **Quick start**: How to build publications
    - Prerequisites (pandoc, make, etc.)
    - Basic build commands (`make all`, `make <publication>`)
    - Example: `make article-01`
- **Repository structure**: Brief overview of directories
    - Explain `src/`, `templates/`, `csl/`, `docs/`, etc.
    - Note that `dist/` is gitignored
- **Contributing**: Link to `docs/CONTRIBUTING.md` or brief guidelines
    - How to report errors
    - How to request publications
- **License**: Reference to CC0 license

**Optional sections**:

- **Publication list**: Manual or auto-generated list (until index feature)
- **Build options**: Advanced Makefile usage (`OUTPUT_DIR` override, etc.)
- **Troubleshooting**: Common build issues and solutions
- **Workflow**: Branch strategy overview for contributors

**Style**:

- Keep concise and scannable
- Use clear headers and code examples
- Update when major changes occur

#### 3.3.2 Publication README (optional)

Individual publications may include a `README` file at
`src/<publication-name>/README` with:

- Publication title and description
- Build instructions if non-standard
- Special dependencies or requirements
- Publication-specific notes
- Links to related resources

> [!NOTE]
> Publication READMEs are optional and at the author's discretion.
> They can be in any plain text format (Markdown recommended for
> readability on GitHub).

## 4. Version Control

### 4.1 Versioning Strategy

- Git provides all versioning functionality
- Repository hosted on GitHub
- Standard git workflow for tracking changes and revisions
- Commit history serves as a changelog for publications

### 4.2 Branch Strategy

- **Main branch**: `main` (default branch)
    - Contains stable, completed publications
    - Production-ready content only

- **Article branches**: Individual branches per article in progress
    - Pattern: `article/<article-name>` (e.g., `article/article-01`)
    - Created for new publications or major revisions
    - Merged to `main` when complete

- **GitFlow adaptation**:
    - No `develop` branch (simplified workflow)
    - No `stage` or testing branches
    - Direct feature branches to `main`

### 4.3 Workflow

1. Create article branch from `main`
2. Work on publication in a branch
3. Merge to `main` when ready
4. Delete article branch after merge (optional)

## 5. Quality Standards

### 5.1 Content Standards

- Single author model – author maintains quality control
- No formal review process is required
- Optional: Self-review checklist before merging to `main`

### 5.2 Code Standards

- Code snippets should be tested and functional
- Follow language-specific formatting conventions
- Include comments where helpful
- No strict linting requirements (author's discretion)

### 5.3 Source File Validation

#### 5.3.1 Validation Goals

- Catch common formatting errors before build
- Ensure source files are well-formed
- Validate frontmatter syntax
- Check for broken internal references

#### 5.3.2 Validation Tools

- **reStructuredText**: Use `rst-lint` or `rstcheck`
    - Check syntax validity
    - Validate directive usage
    - Detect broken references

- **Markdown**: Use `markdownlint` (optional)
    - Check formatting consistency
    - Validate links

- **Custom validation**: Make target for validation
    - `make validate` or `make lint`
    - Run before building
    - Non-blocking warnings, blocking errors

#### 5.3.3 Validation Policy

- Validation is optional but recommended
- Author's discretion on strictness level
- No automated enforcement (no pre-commit hooks required)
- Validation tools documented in README

## 6. Licensing

### 6.1 Content License

- CC0 1.0 Universal (public domain)
- Applies to all publications in the repository

### 6.2 Code License

- Same as content: CC0 1.0 Universal
- All code snippets are released to the public domain

## 7. Contribution Guidelines

### 7.1 External Contributions

- **Accepted contribution types**:
    - Requests for new publications
    - Corrections of misinformation in existing documents
    - Bug reports and issue submissions

- **Not accepted**:
    - Co-authoring or direct content contributions
    - Pull requests modifying publication content (without prior discussion)

### 7.2 Contribution Process

- Use GitHub Issues to request publications or report errors
- Discussion required before any content changes
- See `docs/CONTRIBUTING.md` for detailed guidelines

## 8. Build and Deployment

### 8.1 Build System Overview

#### 8.1.1 General Concepts

The repository uses a build system to transform source publications into
various output formats:

- **Automatic discovery**: A build system discovers publications from `src/`
  directory
- **Configurable output**: Output directory is configurable (default: `dist/`)
- **Multiple formats**: Generate PDF, HTML, and other formats via pandoc
- **Single file or parallel**: Build all publications or specific ones

Two build system implementations are available: Make and Task.

#### 8.1.2 Feature Comparison

| Feature                    | Make                                                | Task                                   |
|----------------------------|-----------------------------------------------------|----------------------------------------|
| **Configuration format**   | Makefile (special syntax)                           | YAML (human-readable)                  |
| **Installation**           | Pre-installed on most Unix systems                  | Requires separate installation         |
| **Cross-platform**         | Limited (native on Unix, requires ports on Windows) | Native support (Windows, Linux, macOS) |
| **Variable interpolation** | Basic (shell-based)                                 | Advanced (built-in templating)         |
| **Dependency management**  | File timestamp-based                                | Built-in dependency resolution         |
| **Syntax complexity**      | Requires tabs, special escaping                     | Straightforward YAML                   |
| **Maturity**               | Industry standard for decades                       | Modern (2017+)                         |
| **Learning curve**         | Steeper (special syntax)                            | Gentler (familiar YAML)                |
| **Ecosystem**              | Ubiquitous                                          | Growing                                |

Both implementations provide the same functionality and can coexist in the
repository.

### 8.2 Make Implementation

#### 8.2.1 Makefile Structure

- Single root `Makefile` at repository root
- No per-publication Makefiles needed
- No Makefile generation required

#### 8.2.2 Build Targets

- `make all`: Build all publications in `src/`
- `make <publication-name>`: Build specific publication
    - Example: `make article-01` builds only `src/article-01/`
    - Publication name matches directory name in `src/`
- `make clean`: Remove build outputs
- `make validate`: Run source file validation

#### 8.2.3 Usage Examples

```bash
# Build all publications
make all

# Build specific publication
make article-01

# Build with custom output directory
make OUTPUT_DIR=public all

# Clean build outputs
make clean

# Validate source files
make validate
```

### 8.3 Task Implementation

#### 8.3.1 Taskfile Structure

Create a `Taskfile.yml` at repository root:

```yaml
version: '3'

vars:
    OUTPUT_DIR: '{{.OUTPUT_DIR | default "dist"}}'
    SRC_DIR: src

tasks:
    default:
        desc: List available tasks
        cmds:
            - task --list

    all:
        desc: Build all publications
        cmds:
            -   task: build-publication
                for:
                    var: PUBLICATIONS
                vars:
                    PUBLICATION: '{{.ITEM}}'
        vars:
            PUBLICATIONS:
                sh: ls -1 {{.SRC_DIR}}

    build-publication:
        desc: Build a specific publication
        summary: |
            Build a single publication by name.
            Usage: task build-publication PUBLICATION=article-01
        cmds:
            - mkdir -p {{.OUTPUT_DIR}}/{{.PUBLICATION}}
            - pandoc {{.SRC_DIR}}/{{.PUBLICATION}}/index.* -o {{.OUTPUT_DIR}}/{{.PUBLICATION}}/output.pdf
        requires:
            vars: [ PUBLICATION ]

    clean:
        desc: Remove build outputs
        cmds:
            - rm -rf {{.OUTPUT_DIR}}

    validate:
        desc: Validate source files
        cmds:
            - echo "Running validation..."
            # Add validation commands here
```

#### 8.3.2 Build Tasks

- `task all`: Build all publications in `src/`
- `task build-publication PUBLICATION=<name>`: Build specific publication
    - Example: `task build-publication PUBLICATION=article-01`
- `task clean`: Remove build outputs
- `task validate`: Run source file validation

#### 8.3.3 Usage Examples

```bash
# List available tasks
task

# Build all publications
task all

# Build specific publication
task build-publication PUBLICATION=article-01

# Build with custom output directory
OUTPUT_DIR=public task all

# Clean build outputs
task clean

# Validate source files
task validate
```

### 8.4 Build Process

Regardless of the build system used, the build process follows these steps:

1. Discover publications automatically from `src/` directory
2. Use `pandoc` for format transformations
3. Apply shared templates and metadata from `src/metafile.yaml`
4. Merge publication-specific metadata from `src/<publication>/metafile.yaml`
5. Combine references from `src/refs.bib` and `src/<publication>/refs.bib`
6. Apply frontmatter overrides as final step
7. Generate output in configured directory structure

### 8.5 Output Generation

- **Transformation tool**: pandoc
- **Output location**: Configurable output directory
    - Default: `dist/`
    - Override via environment variable or build system parameter
    - Examples:
        - Make: `make OUTPUT_DIR=public all`
        - Task: `OUTPUT_DIR=public task all`
- **Output structure**: `<output-dir>/<publication-name>/<format>/`
    - Example: `dist/article-01/pdf/`, `dist/article-01/html/`
- **Supported formats**:
    - PDF (primary)
    - HTML
    - Other formats as needed

### 8.6 Build Artifacts

- **Not tracked in git**: Build outputs are excluded from version control
- **`.gitignore` entries**: Common output directory names
    - `dist/`
    - `public/`
    - `build/`
    - `out/`
    - Any other configured output directories

### 8.7 Error Handling

#### 8.7.1 Error Reporting

- **Clear error messages**: When builds fail, display informative messages
    - Example: "Failed to build article-01: pandoc returned error code 1"
    - Include context about what step failed
    - Show which file/line caused the error when possible

- **Pretty logging**:
    - Color-coded output (if the terminal supports it)
        - Red for errors
        - Yellow for warnings
        - Green for success messages
    - Clear visual separation between build steps
    - Progress indicators for multi-publication builds

- **Pre-build checks**:
    - Verify source files exist before building
    - Check for required dependencies (pandoc, build system tool)
    - Display helpful "command not found" messages with installation hints
    - Warn about missing optional dependencies

- **Exit codes**:
    - 0 for successful builds
    - Non-zero for failed builds
    - Allows CI/CD and build tools to detect failures

#### 8.7.2 Error Handling Scope

- **Simple error reporting only** (no complex logic)
- No retry mechanisms
- No automatic error recovery
- No fallback strategies
- No partial build states
- Focus on clear diagnostics and helpful messages

### 8.8 Publishing Workflow

- No automated publishing to external platforms
- Generated outputs stored in a configured output directory
- Users must build locally to generate outputs

## 9. Technical Requirements

### 9.1 Dependencies

#### 9.1.1 Required Tools

- **make**: GNU Make 4.0 or higher
    - Build system and task automation
- **Task**: Version 3.x or higher
    - Modern task runner and build system
- **pandoc**: Version 2.x or higher (3.x recommended)
    - Format transformation engine
    - Universal document converter
- **git**: Version 2.x or higher
    - Version control system
    - Repository hosted on GitHub

#### 9.1.2 Optional Dependencies

- **LaTeX distribution** (for PDF generation):
    - TeX Live 2020 or higher (recommended)
    - MiKTeX (Windows alternative)

- **Python 3.x** (for potential scripting/validation):
    - Version 3.8 or higher

- **Other format-specific tools**:
    - Depends on chosen output formats

#### 9.1.3 Version Policy

- Specify minimum versions, not exact versions
- Aim for tools available in common package managers
- Document any breaking changes with major version updates

### 9.2 Compatibility

- Unix-like systems preferred (Linux, macOS)
- Plain text sources viewable on any platform
- Generated outputs depend on chosen formats

## 10. Future Considerations

### 10.1 Long-term Features

- **Publication index**: Auto-generated index of all publications
    - Could be `INDEX.md` at repository root
    - Lists all publications with metadata (title, date, description)
    - Updated automatically by the build system
    - Not an immediate requirement

- **CI/CD integration**: Automated builds on push
    - GitHub Actions workflow
    - Automatic build validation
    - Optional: Deploy outputs to GitHub Pages or similar

- **Enhanced templates**: Publication type-specific templates
    - Article template
    - Tutorial template
    - Research paper template

- **Search functionality**: Cross-publication search capability
    - Full-text search across all publications
    - Tag-based navigation

- **Output format standardization**:
  Define preferred formats per publication type

### 10.2 Potential Enhancements

- Bibliography management improvements
- Citation style customization per publication
- Multi-language publication support
- Interactive HTML outputs with navigation

---

## Summary

This document defines a format-agnostic publication repository with the
following key characteristics:

**Core Philosophy**:

- Single-author repository for mixed publication types
- Format-agnostic: supports any plain text format (rst, md, txt, etc.)
- Simple, flat structure with shared resources
- Build system for output generation, not publishing

**Key Features**:

- ✓ Flat publication structure in `src/` directory
- ✓ Shared templates, metadata, and bibliography
- ✓ Make-based build system with `make all` and `make <publication>` targets
- ✓ Configurable output directory (default: `dist/`)
- ✓ Git-based versioning with a simplified branching strategy
- ✓ Optional validation/linting with clear error messages
- ✓ CC0 license for all content
