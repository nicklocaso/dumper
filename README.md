# Dumper

**Dumper** is a simple yet effective command-line tool designed to capture the context of a project and prepare it for interaction with AI agents like ChatGPT.

It extracts the project structure, relevant files and contextual information into a clean Markdown file that can be manually pasted into an AI conversation. This is especially useful during development, debugging, code review, or documentation processes.

---

## Features

- Generates a complete Markdown file (`.dumper.dump.md`) containing:
  - Project context and request message
  - Dynamic TODO list for the AI
  - Project directory structure (up to configurable depth)
  - Selected important files (syntax-highlighted)
  - Optional `package.json` content (for nodejs developments)
- Opens the generated file automatically in Visual Studio Code (optional)
- Copies the content to clipboard automatically (optional)
- Estimates the number of tokens used (approximate)
- Highly configurable via command-line options
- Lightweight, with minimal external dependencies (`tree`, `pbcopy`, `xclip`, or `xsel`)

---

## Installation

Clone the repository and install Dumper globally:

```bash
git clone https://github.com/yourusername/dumper.git
cd dumper
chmod +x install.sh 
./install.sh
```

Make sure the `tree` command is installed:

```bash
# Debian/Ubuntu
sudo apt install tree

# macOS (Homebrew)
brew install tree
```

---

## Usage

Basic usage:

```bash
dumper "Write unit tests for the following files" src/index.js src/utils/helpers.js
```

Example:

```bash
dumper "Refactor and optimize the provided codebase for better performance" server/app.js server/routes/api.js  --no-package-json --no-open
```

This will create a `.dumper.dump.md` file with the project snapshot, ready to be pasted into a ChatGPT conversation.

---

## Options

| Option              | Description                                            |
|---------------------|--------------------------------------------------------|
| `--no-tree`          | Skip project directory tree generation                |
| `--no-package-json`  | Do not include `package.json` even if it exists        |
| `--no-open`          | Do not automatically open the generated file in VS Code |
| `--no-clipboard`     | Do not automatically copy content to clipboard        |
| `--help`             | Show help message and exit                            |

---

## Estimated Token Count

After generating the `.dumper.dump.md` file, Dumper provides an **approximate token count** based on file size.  
This helps ensure the context fits within AI model token limits.

**Approximation rule**:  
- 1 token ≈ 4 characters

---

## Requirements

- Bash (tested on macOS and Linux)
- `tree` command installed
- Optionally:
  - `pbcopy` (macOS)
  - `xclip` or `xsel` (Linux) for clipboard copy
  - Visual Studio Code (`code` CLI) for automatic opening (optional)

---

## License

This project is licensed under the MIT License.

