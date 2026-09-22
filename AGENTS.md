# Agent Instructions

## Core Rules

- Ask clarifying questions.
- Avoid excessive token burn.
- Never commit secrets or local config (e.g. `config.secret.yml`, `.env`).
- Prefer adding to existing files before creating new ones.

## Communication

- Use direct and concise language and common terminology.
- Easy to digest by a human, technical enough for an agent.

## Name Conventions

- **Isometric / aligned naming**
  - improves scannability (column alignment)
- **Semantic symmetry / parallel pairs**
  - If you know the opposite verb, you can guess the pair
- **Rhythmic variation**
  - Words in a phrase differ in length to avoid monotony and improve rhythm

## Development Process

- Break feature work into ~3 phases
  - Phases: "Minimum Scope", "Complete Scope", "Extended Scope"
  - Write phase list to documents for tracking
  - Update documentation after each step.
- Break feature phases into tasks:
  - Write task list to documents for tracking
  - Update documentation after each step.
- Use test driven development
  - Unit tests MUST be fast (<= few seconds) and should be ran frequently
  - Other tests may be slow (>= few minutes) and should be ran infrequently
- Log diagnostics often for debugging and optimization
- Update documentation with every change
- Treat compiler warnings, test failures, leaks, out-of-bounds access and
  unchecked allocation or I/O as defects; handle failure paths explicitly.

## System Design

- Minimal dependencies
- Modular for ease of composition and testing
- Core modules decoupled from infrastructure
- Avoid overfitting to a use case to preserve versitility
- Keep behavior deterministic for identical seeds, inputs and time steps
- Avoid hidden global state

## User Interface Design

- Use WebSockets often for async messaging
- Modulate hero icon in a variety of ways to indicate status

## User Interface Style

- Sleak and minimal with balance of empty space.
- High quality and legible typography.
- Prefer icons over text labels.
- Responsive to change in size and orientation.
- Mobile first

## Documentation Style

- Dense and detailed.
- Use lists over tables
- Use mermaid charts over ASCII charts
- Try to avoid line breaks mid sentence
- Use check list boxes (open: `- [ ]`, closed: `- [x]`)

## Environment Tools

- Use `uv` (for Python, `.venv`, and other applications)
- Use `clang` (for C11)
- Use `gh` (read-only unless explicitly told otherwise)
- Use `aws` (read-only unless explicitly told otherwise)

## Workspace Content

### File Descriptions

#### Documentation files

- _AGENTS.md_ Agent instructions
- _CHANGES.md_ Closed tasks list sorted by version
- _DESIGN.md_ Complete overview and reference
- _EXAMPLE.ipynb_ Minimal demonstration
- _INITIAL.md_ Initial description
- _LICENSE.md_ Content license
- _OPTIONS.md_ Configuration properties
- _README.md_ Summary and quickstart
- _TODO.md_ Open tasks list sorted by impact

#### Project CI/CD files

- _settings.yml_
  - Default configuration
- _init.ps1_
  - dev environment setup (Windows)
- _init.sh_
  - dev environment setup (Mac/Linux)
- _make.py_
  - CI/CD: install, build, test, run, eval, deploy

#### Native project files

- _app/core.c_
  - C11 API library (no header)
- _app/vulk.c_
  - C11 Vulkan backend (no header)
- _app/main.py_
  - C11 CLI/TUI
- _test/test.c_
  - C11 unit tests (no header)
- _test/e2e.c_
  - C11 e2e tests and UI captures (images in `assets/`)
- _test/eval.c_:
  - Python benchmark tests

#### Python project files

- _app/core.py_
  - Python API library
- _app/main.py_
  - Python CLI/TUI
- _test/test.py_:
  - Python unit tests
- _test/e2e.py_:
  - Python e2e tests and UI captures (images in `assets/`)
- _test/eval.py_:
  - Python benchmark tests
- _pyproject.toml_
  - package metadata and dependencies

#### Web UI project files

- _app/ui.html_
  - Web UI markup
- _app/ui.css_
  - Web UI styles
- _app/ui.js_:
  - Web UI logic

## VS Code Settings

```json
"chat.useAgentSkills": true,
"chat.useAgentsMdFile": true,
"chat.useNestedAgentsMdFiles": false,
"chat.useClaudeMdFile": false,
"chat.useClaudeHooks": false,
"chat.useHooks": false,
"chat.agentHost.byokModels.enabled": true,
"git.confirmSync": false,
"git.enableSmartCommit": true,
"[python]": {
"editor.tabSize": 4,
"editor.defaultFormatter": "ms-python.black-formatter"
},
"black-formatter.args": [
"--line-length",
"200"
],
"python.testing.unittestEnabled": false,
"python.testing.pytestEnabled": true,
"python.testing.pytestArgs": [
"tests"
],
  "[yaml]": {
    "editor.defaultFormatter": "redhat.vscode-yaml",
    "editor.autoIndent": "keep",
    "diffEditor.ignoreTrimWhitespace": false,
    "editor.defaultColorDecorators": "auto",
    "editor.quickSuggestions": {
      "strings": true,
      "other": true,
      "comments": false
    }
  },
  "yaml.validate": true,
  "yaml.customTags": [
    "!And",
    "!Base64",
    "!Cidr",
    "!Condition",
    "!Equals",
    "!FindInMap",
    "!GetAtt",
    "!If",
    "!ImportValue",
    "!Include",
    "!Join",
    "!Not",
    "!Or",
    "!Ref",
    "!Select",
    "!Split",
    "!Sub",
    "!Transform"
  ],
```
