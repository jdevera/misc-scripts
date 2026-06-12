# AGENTS.md

This file provides guidance to AI coding agents when working with code in this repository.

## Repository Overview

This is a collection of standalone utility scripts (Python and Bash) for common development and system administration tasks. Scripts are designed to be self-contained and executable directly from the repository directory or from the PATH.

## Script Documentation Convention

All scripts in this repository follow a tag-based documentation format at the top of each file:

```bash
# BRIEF: <one-line-summary>
# DESC: <optional-longer-explanation>
# DESC: <continuation-lines-repeat-the-tag>
# USAGE: <optional-usage-examples>
# DEPS: <optional-external-dependencies>
```

**Key Rules:**
- **BRIEF** is required (< 80 chars)
- **DESC**, **USAGE**, **DEPS** are optional
- Multi-line tags repeat the prefix on each line
- Placement: Within first ~10 lines, after shebang and any embedded metadata
- Use imperative mood: "Print paths" not "Prints paths"

See `docs/documentation.md` for complete guidelines.

## Python Scripts with UV

Many Python scripts use `uv` as a script runner with embedded dependencies:

```python
#!/usr/bin/env -S uv run --quiet --script
# /// script
# requires-python = ">=3.11"
# dependencies = [
#    "click",
#    "rich",
# ]
# ///
# BRIEF: Script description here
```

This allows scripts to be standalone with their dependencies specified inline. The `uv` tool handles creating isolated environments and installing packages automatically.

**Python Click Scripts:**
- When using Click, enable `-h` as a help option alias by adding `context_settings={"help_option_names": ["-h", "--help"]}` to the command/group decorator

## Bash scripts

Bash scripts do not state the path to bash directly:

```bash
#!/usr/bin/env bash
# BRIEF: Script description here
```


## Architecture

**Structure:**
- Root directory contains all executable scripts
- `ARCHIVE/` contains old/deprecated scripts (excluded from normal operations)
- `docs/` contains documentation
- No build system - scripts are run directly

## Running Scripts

Scripts are executed directly:

```sh
./script-name [args]
```

For Python scripts using `uv`, the first run will install dependencies. Subsequent runs use cached environments.

## Adding New Scripts

When creating a new script:

1. Make it executable: `chmod +x script-name`
2. Add appropriate shebang:
   - Bash: `#!/usr/bin/env bash`
   - Python with uv: `#!/usr/bin/env -S uv run --quiet --script`
3. Add documentation tags (BRIEF at minimum)
4. For Python scripts with dependencies, use uv PEP 723 inline metadata
5. Place in repository root (not in subdirectories)

## Validating and Extracting Documentation

The `script-docs` tool extracts and validates documentation from scripts:

**Validate documentation:**
```bash
./script-docs dump --strict script-name
```

**Extract documentation in various formats:**
```bash
# JSON (array format)
./script-docs dump script-name [script-name2 ...]

# Markdown (raw)
./script-docs dump --format markdown script-name

# Rich (rendered in terminal)
./script-docs dump --format rich script-name

# README format (brief list)
./script-docs dump --format readme *
```

**Common validation issues:**
- Missing BRIEF tag (required)
- Missing shebang (files without `#!` are skipped)
- Non-script files are automatically filtered out

Use `--strict` mode when adding or modifying scripts to ensure documentation is complete.

## Code Preservation when documenting with comments

**Critical:** When modifying scripts, preserve all existing code including:
- `__description__` variables in Python scripts
- Docstrings and inline comments
- Function implementations
- Any existing functionality

Only update documentation headers, never remove working code during documentation updates.
