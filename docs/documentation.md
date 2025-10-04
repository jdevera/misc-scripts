# Script Documentation Convention

## Overview

This repository contains utility scripts written in Python and Bash. To maintain consistency and enable automated documentation generation, all scripts should follow a concise, tag-based documentation format.

## Documentation Format

### Basic Format

Add a brief summary near the top of the file:

```bash
# BRIEF: <one-line-summary>
```

**Placement:** Within the first ~10 lines
- **Python scripts**: After shebang and any embedded metadata (like `# /// script` blocks)
- **Bash scripts**: After shebang, typically before `set` commands

### Extended Format (Optional)

Add more context as needed. Tags can span multiple lines by repeating the prefix:

```bash
# BRIEF: <one-line-summary>
# DESC: <longer-explanation>
# DESC: <continuation-of-explanation>
# USAGE: <command-example>
# USAGE: <more-usage-details>
# DEPS: <dependencies>
```

Use what makes sense for each script.

## Tag Definitions

- **BRIEF**: One-line (< 80 char) summary of what the script does
- **DESC**: Longer, multi-line description providing more context (optional)
- **USAGE**: Example invocation and usage details (optional, multi-line)
- **DEPS**: External dependencies - packages, commands, env vars (optional)

**Multi-line Support**: Any tag can span multiple lines by repeating the prefix on each line.

## Examples

### Python Script with uv metadata

```python
#!/usr/bin/env -S uv run --quiet --script
# /// script
# requires-python = ">=3.11"
# dependencies = ["jsonschema", "pyyaml"]
# ///
# BRIEF: Validate JSON/YAML files against a schema
# USAGE: json-validator --schema <schema> <file>...

import jsonschema
...
```

### Simple Python Script

```python
#!/usr/bin/env python3
# BRIEF: Print the absolute path for a file or directory

import os.path
...
```

### Bash Script with Multi-line Documentation

```bash
#!/usr/bin/env bash
# BRIEF: Get PEM certificate chain for SSL connection
# DESC: Connects to the specified host and port, retrieves the SSL
# DESC: certificate chain, and outputs it in PEM format. Useful for
# DESC: inspecting certificates or adding them to trust stores.
# USAGE: ssl-getpem <host> [<port>] [<output-file>]
# USAGE:   host        - Hostname to connect to
# USAGE:   port        - Port number (default: 443)
# USAGE:   output-file - Output file (default: stdout)
# DEPS: openssl

set -euo pipefail
```

### Minimal Bash Script

```bash
#!/usr/bin/env bash
# BRIEF: Show current git committer and author identity

function get_identity() { ... }
```


## Guidelines

1. **BRIEF is required** - keep it under 80 characters
2. **DESC is optional** - use when you need to explain more context
3. **Multi-line by repeating prefix** - `# DESC:` on each line for continuation
4. **Focus on what, not how** - describe the purpose, not implementation
5. **Add USAGE/DEPS when helpful** - completely optional
6. **Place near the top** - somewhere in first ~10 lines is fine
7. **Use imperative mood** - "Print paths" not "Prints paths"
8. **Keep it simple** - if it feels like too much ceremony, it probably is

This is meant to be lightweight and practical, not a strict requirement.
