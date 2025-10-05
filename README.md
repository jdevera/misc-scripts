# Jacobo de Vera's miscellaneous scripts

These are some homemade scripts that I like having in all my Linux boxes.

## Installation

Simply clone this repository and add the directory to your path or copy all
scripts to a directory that is already in your path.

## Contents

<!-- [[[cog
import subprocess
from pathlib import Path
files = [str(f) for f in Path('.').glob('*') if f.is_file()]
res = subprocess.run([
    "./script-docs", "dump", "--format", "readme"
    ] + files, capture_output=True, text=True)
cog.out(res.stdout)
]]] -->

- **ssl-getpem** - Get PEM certificate chain for an SSL connection

- **json-to-yaml** - Convert JSON files to YAML format

- **chezmoi-pick-file** - Interactively select a chezmoi-managed file with fzf

- **git-branches** - Display git branches organized by category with color coding

- **relpath** - Print a path relative to another directory

- **abspath** - Print the absolute path for a given file or directory

- **json-validator** - Validate JSON/YAML files against a schema

- **longlines** - Show lines exceeding a given character length

- **git-remote-hoster** - Detect and display the git remote hosting service

- **pid** - Show processes for the current user with optional filtering

- **new** - Create new files from templates

- **op-edit** - Interactively select and edit a 1Password document

- **git-identity** - Show current git committer and author identity

- **script-docs** - Extract and display documentation from scripts

- **uv-script-docker-debian** - Test standalone UV scripts in a Debian Docker container

- **showaliases** - Display shell aliases in a formatted two-column list

<!-- [[[end]]] -->


## License

These scripts, unless stated otherwise in a particular file, are licensed
under the MIT License.

See LICENSE file for details.
