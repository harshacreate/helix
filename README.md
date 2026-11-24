Helix

This is my copy of [Helix](https://github.com/helix-editor/helix), a text editor made by the Helix team and its contributors. The original project is written in Rust and takes ideas from Kakoune and Neovim.

What it does

Helix runs in a terminal. It uses different modes for typing and editing. You can select and edit several parts of a file at once. It works with language servers for features such as code completion, and uses tree-sitter to read the structure of code.

Some languages have rules for automatic indentation. Check `runtime/queries/<lang>/indents.scm` for those rules.

Install and use it

Follow the [installation guide](https://docs.helix-editor.com/install.html). The [manual](https://docs.helix-editor.com/) explains how to use it and lists the [keyboard shortcuts](https://docs.helix-editor.com/keymap.html).

For help, read the [common questions](https://github.com/helix-editor/helix/wiki/FAQ) and [problem solving guide](https://github.com/helix-editor/helix/wiki/Troubleshooting). You can also visit the [Helix community](https://matrix.to/#/#helix-community:matrix.org).

Contribute and credits

Read the [contributor guide](docs/CONTRIBUTING.md) before changing the code. The original project and its contributors keep credit for their work. The logo was designed by [jakenvac](https://github.com/jakenvac). See [LICENSE](LICENSE) for the license terms.
