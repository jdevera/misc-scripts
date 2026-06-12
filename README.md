# Jacobo de Vera's miscellaneous scripts

These are some homemade scripts that I like having in all my Linux boxes.

## Installation

Simply clone this repository and add the directory to your path or copy all
scripts to a directory that is already in your path.

## Contents

<!-- [[[cog
import subprocess
from pathlib import Path
files = [str(f) for f in Path('src').glob('*') if f.is_file()]
res = subprocess.run([
    "./src/script-docs", "dump", "--format", "readme"
    ] + files, capture_output=True, text=True)
cog.out(res.stdout)
]]] -->

- **set-union** - Set union of two line files: all lines from either input, deduplicated

- **eloc** - Locate a file with locate + fzf and open it in the editor

- **ssl-getpem** - Get PEM certificate chain for an SSL connection

- **ranking** - Frequency table of input lines, most common first

- **json-to-yaml** - Convert JSON files to YAML format

- **edot** - Fuzzy-find and edit a file in a config tree (defaults to chezmoi source)

- **lastdown** - Show the most recently downloaded files with colors

- **hl** - Syntax-highlight files or stdin in the terminal with pygmentize

- **chezmoi-pick-file** - Interactively select a chezmoi-managed file with fzf

- **git-branches** - Display git branches organized by category with color coding

- **set-is-subset** - Exit 0 if all lines of the first input file are also in the second

- **relpath** - Print a path relative to another directory

- **set-symdiff** - Symmetric difference of two line files: lines in either input but not both

- **set-intersection** - Set intersection of two line files: only lines present in both inputs

- **abspath** - Print the absolute path of each given path

- **set-difference** - Set difference of two line files: lines in the first input but not the second

- **stripcolor** - Remove ANSI color/escape codes from files or stdin

- **git-foldiff** - Browse a git diff in vim with one fold per file

- **xf** - Extract any compressed file based on its extension

- **hless** - Syntax-highlight files or stdin and page through less

- **field** - Print the Nth whitespace-separated field of each input line

- **json-validator** - Validate JSON/YAML files against a schema

- **longlines** - Show lines exceeding a given character length

- **git-remote-hoster** - Detect and display the git remote hosting service

- **pid** - Show processes for the current user with optional filtering

- **rfv** - Search file contents live with ripgrep and fzf, open matches in Vim

- **http_server** - Serve the current directory over HTTP

- **download** - Download files into the downloads directory with wget

- **rtouch** - Touch a file, creating all parent directories first

- **new** - Create new files from templates

- **claude-spend** - Show a sparkline of daily Claude AI spend

- **op-edit** - Interactively select and edit a 1Password document

- **git-identity** - Show current git committer and author identity

- **script-docs** - Extract and display documentation from scripts

- **average** - Print the average of numeric input lines

- **uv-script-docker-debian** - Test standalone UV scripts in a Debian Docker container

- **showaliases** - Display shell aliases in a formatted two-column list

- **showenv** - Show a pretty-printed list of environment variables

- **stripe** - Color alternate lines of input blue for visual striping

<!-- [[[end]]] -->


## License

These scripts, unless stated otherwise in a particular file, are licensed
under the MIT License.

See LICENSE file for details.
