## Editor

[`[editor]` Section](#editor-section)

[`[editor.clipboard-provider]` Section](#editorclipboard-provider-section)

[`[editor.statusline]` Section](#editorstatusline-section)

[`[editor.lsp]` Section](#editorlsp-section)

[`[editor.cursor-shape]` Section](#editorcursor-shape-section)

[`[editor.file-picker]` Section](#editorfile-picker-section)

[`[editor.file-explorer]` Section](#editorfile-explorer-section)

[`[editor.buffer-picker]` Section](#editorbuffer-picker-section)

[`[editor.auto-pairs]` Section](#editorauto-pairs-section)

[`[editor.auto-save]` Section](#editorauto-save-section)

[`[editor.search]` Section](#editorsearch-section)

[`[editor.whitespace]` Section](#editorwhitespace-section)

[`[editor.indent-guides]` Section](#editorindent-guides-section)

[`[editor.gutters]` Section](#editorgutters-section)

[`[editor.gutters.line-numbers]` Section](#editorguttersline-numbers-section)

[`[editor.gutters.diagnostics]` Section](#editorguttersdiagnostics-section)

[`[editor.gutters.diff]` Section](#editorguttersdiff-section)

[`[editor.gutters.spacer]` Section](#editorguttersspacer-section)

[`[editor.gutters.code-action-hint]` Section](#editorgutterscode-action-hint-section)

[`[editor.soft-wrap]` Section](#editorsoft-wrap-section)

[`[editor.smart-tab]` Section](#editorsmart-tab-section)

[`[editor.inline-diagnostics]` Section](#editorinline-diagnostics-section)

[`[editor.word-completion]` Section](#editorword-completion-section)

[`[editor.workspace-trust]` Section](#editorworkspace-trust-section)

### `[editor]` Section

Key: `scrolloff`; Description: Number of lines of padding around the edge of the screen when scrolling; Default: `5`

Key: `mouse`; Description: Enable mouse mode; Default: `true`

Key: `mouse-yank-register`; Description: Which register to use for mouse yanks.; Default: `*`

Key: `middle-click-paste`; Description: Middle click paste support; Default: `true`

Key: `default-yank-register`; Description: Default register used for yank/paste; Default: `'"'`

Key: `scroll-lines`; Description: Number of lines to scroll per scroll wheel step; Default: `3`

Key: `shell`; Description: Shell to use when running external commands; Default: Unix: `["sh", "-c"]`<br/>Windows: `["cmd", "/C"]`

Key: `line-number`; Description: Line number display: `absolute` simply shows each line's number, while `relative` shows the distance from the current line. When unfocused or in insert mode, `relative` will still show absolute line numbers; Default: `"absolute"`

Key: `cursorline`; Description: Highlight all lines with a cursor; Default: `false`

Key: `cursorcolumn`; Description: Highlight all columns with a cursor; Default: `false`

Key: `continue-comments`; Description: if helix should automatically add a line comment token if you create a new line inside a comment.; Default: `true`

Key: `gutters`; Description: Gutters to display: Available are `diagnostics` and `diff` and `line-numbers` and `spacer` and `code-action-hint`, note that `diagnostics` also includes other features like breakpoints, 1-width padding will be inserted if gutters is non-empty; Default: `["diagnostics", "spacer", "line-numbers", "spacer", "diff"]`

Key: `auto-completion`; Description: Enable automatic pop up of auto-completion; Default: `true`

Key: `path-completion`; Description: Enable filepath completion. Show files and directories if an existing path at the cursor was recognized, either absolute or relative to the current opened document or current working directory (if the buffer is not yet saved). Defaults to true.; Default: `true`

Key: `auto-format`; Description: Enable automatic formatting on save[^3]; Default: `true`

Key: `idle-timeout`; Description: Time in milliseconds since last keypress before idle timers trigger.; Default: `250`

Key: `completion-timeout`; Description: Time in milliseconds after typing a word character before completions are shown, set to 5 for instant.; Default: `250`

Key: `preview-completion-insert`; Description: Whether to apply completion item instantly when selected; Default: `true`

Key: `completion-trigger-len`; Description: The min-length of word under cursor to trigger autocompletion; Default: `2`

Key: `completion-replace`; Description: Whether to make completions always replace the entire word and not just the part before the cursor; Default: `false`

Key: `auto-info`; Description: Whether to display info boxes; Default: `true`

Key: `true-color`; Description: Whether to override automatic detection of terminal truecolor support in the event of a false negative; Default: `false`

Key: `undercurl`; Description: Whether to override automatic detection of terminal undercurl support in the event of a false negative; Default: `false`

Key: `rulers`; Description: List of column positions at which to display the rulers. Can be overridden by language specific `rulers` in `languages.toml` file; Default: `[]`

Key: `bufferline`; Description: Renders a line at the top of the editor displaying open buffers. Can be `always`, `never` or `multiple` (only shown if more than one buffer is in use); Default: `"never"`

Key: `color-modes`; Description: Whether to color the mode indicator with different colors depending on the mode itself; Default: `false`

Key: `text-width`; Description: Maximum line length. Used for the `:reflow` command and soft-wrapping if `soft-wrap.wrap-at-text-width` is set; Default: `80`

Key: `workspace-lsp-roots`; Description: Directories relative to the workspace root that are treated as LSP roots. Should only be set in `.helix/config.toml`; Default: `[]`

Key: `default-line-ending`; Description: The line ending to use for new documents. Can be `native`, `lf`, `crlf`, `ff`, `cr` or `nel`. `native` uses the platform's native line ending (`crlf` on Windows, otherwise `lf`).; Default: `"native"`

Key: `insert-final-newline`; Description: Whether to automatically insert a trailing line-ending on write if missing; Default: `true`

Key: `atomic-save`; Description: Whether to use atomic operations to write documents to disk. This prevents data loss if the editor is interrupted while writing the file, but may confuse some file watching/hot reloading programs.; Default: `true`

Key: `trim-final-newlines`; Description: Whether to automatically remove line-endings after the final one on write; Default: `false`

Key: `trim-trailing-whitespace`; Description: Whether to automatically remove whitespace preceding line endings on write; Default: `false`

Key: `popup-border`; Description: Draw border around `popup`, `menu`, `all`, or `none`; Default: `"none"`

Key: `indent-heuristic`; Description: How the indentation for a newly inserted line is computed: `simple` just copies the indentation level from the previous line, `tree-sitter` computes the indentation based on the syntax tree and `hybrid` combines both approaches. If the chosen heuristic is not available, a different one will be used as a fallback (the fallback order being `hybrid` -> `tree-sitter` -> `simple`).; Default: `"hybrid"`

Key: `jump-label-alphabet`; Description: The characters that are used to generate two character jump labels. Characters at the start of the alphabet are used first.; Default: `"abcdefghijklmnopqrstuvwxyz"`

Key: `end-of-line-diagnostics`; Description: Minimum severity of diagnostics to render at the end of the line. Set to `disable` to disable entirely. Refer to the setting about `inline-diagnostics` for more details; Default: `"hint"`

Key: `clipboard-provider`; Description: Which API to use for clipboard interaction. One of `pasteboard` (MacOS), `wayland`, `x-clip`, `x-sel`, `win32-yank`, `termux`, `tmux`, `windows`, `termcode`, `none`, or a custom command set.; Default: Platform and environment specific.

Key: `editor-config`; Description: Whether to read settings from [EditorConfig](https://editorconfig.org) files; Default: `true`

Key: `rainbow-brackets`; Description: Whether to render rainbow colors for matching brackets. Requires tree-sitter `rainbows.scm` queries for the language.; Default: `false`

Key: `kitty-keyboard-protocol`; Description: Whether to enable Kitty Keyboard Protocol. Can be `enabled`, `disabled` or `auto`; Default: `"auto"`


[^3]: In most cases, you also need to enable the `auto-format` setting under `languages.toml`. You can find the reasoning [here](https://github.com/helix-editor/helix/discussions/9043#discussioncomment-7811497).

### `[editor.clipboard-provider]` Section

Helix can be configured either to use a builtin clipboard configuration or to use
a provided command.

For instance, setting it to use OSC 52 termcodes, the configuration would be:
```toml
[editor]
clipboard-provider = "termcode"
```

Alternatively, Helix can be configured to use arbitrary commands for clipboard integration:

```toml
[editor.clipboard-provider.custom]
yank = { command = "cat",  args = ["test.txt"] }
paste = { command = "tee",  args = ["test.txt"] }
primary-yank = { command = "cat",  args = ["test-primary.txt"] } # optional
primary-paste = { command = "tee",  args = ["test-primary.txt"] } # optional
```

For custom commands the contents of the yank/paste is communicated over stdin/stdout.

### `[editor.statusline]` Section

Allows configuring the statusline at the bottom of the editor.

The configuration distinguishes between three areas of the status line:

`[ ... ... LEFT ... ... | ... ... ... CENTER ... ... ... | ... ... RIGHT ... ... ]`

Statusline elements can be defined as follows:

```toml
[editor.statusline]
left = ["mode", "spinner"]
center = ["file-name"]
right = ["diagnostics", "selections", "position", "file-encoding", "file-line-ending", "file-type"]
separator = "│"
mode.normal = "NORMAL"
mode.insert = "INSERT"
mode.select = "SELECT"
diagnostics = ["warning", "error"]
workspace-diagnostics = ["warning", "error"]
```
The `[editor.statusline]` key takes the following sub-keys:

Key: `left`; Description: A list of elements aligned to the left of the statusline; Default: `["mode", "spinner", "file-name", "read-only-indicator", "file-modification-indicator"]`

Key: `center`; Description: A list of elements aligned to the middle of the statusline; Default: `[]`

Key: `right`; Description: A list of elements aligned to the right of the statusline; Default: `["diagnostics", "selections", "register", "position", "file-encoding"]`

Key: `separator`; Description: The character used to separate elements in the statusline; Default: `"│"`

Key: `mode.normal`; Description: The text shown in the `mode` element for normal mode; Default: `"NOR"`

Key: `mode.insert`; Description: The text shown in the `mode` element for insert mode; Default: `"INS"`

Key: `mode.select`; Description: The text shown in the `mode` element for select mode; Default: `"SEL"`

Key: `diagnostics`; Description: A list of severities which are displayed for the current buffer; Default: `["warning", "error"]`

Key: `workspace-diagnostics`; Description: A list of severities which are displayed for the workspace; Default: `["warning", "error"]`


The following statusline elements can be configured:

`mode`: The current editor mode (`mode.normal`/`mode.insert`/`mode.select`)

`spinner`: A progress spinner indicating LSP activity

`file-name`: The path/name of the opened file

`file-absolute-path`: The absolute path/name of the opened file

`file-base-name`: The basename of the opened file

`current-working-directory`: The current working directory

`file-modification-indicator`: The indicator to show whether the file is modified (a `[+]` appears when there are unsaved changes)

`file-encoding`: The encoding of the opened file if it differs from UTF-8

`file-line-ending`: The file line endings (CRLF or LF)

`file-indent-style`: The file indentation style

`read-only-indicator`: An indicator that shows `[readonly]` when a file cannot be written

`total-line-numbers`: The total line numbers of the opened file

`file-type`: The type of the opened file

`diagnostics`: The number of warnings and/or errors

`workspace-diagnostics`: The number of warnings and/or errors on workspace

`selections`: The primary selection index out of the number of active selections

`primary-selection-length`: The number of characters currently in primary selection

`position`: The cursor position

`position-percentage`: The cursor position as a percentage of the total number of lines

`separator`: The string defined in `editor.statusline.separator` (defaults to `"│"`)

`spacer`: Inserts a space between elements (multiple/contiguous spacers may be specified)

`version-control`: The current branch name or detached commit hash of the opened workspace

`register`: The current selected register

`code-action-hint`: Indicator for when code actions are available


### `[editor.lsp]` Section

Key: `enable`; Description: Enables LSP integration. Setting to false will completely disable language servers regardless of language settings.; Default: `true`

Key: `display-messages`; Description: Display LSP `window/showMessage` messages below statusline[^1]; Default: `true`

Key: `display-progress-messages`; Description: Display LSP progress messages below statusline[^1]; Default: `false`

Key: `auto-signature-help`; Description: Enable automatic popup of signature help (parameter hints); Default: `true`

Key: `auto-document-highlight`; Description: Automatically highlight symbol references at the cursor; Default: `false`

Key: `display-inlay-hints`; Description: Display inlay hints[^2]; Default: `false`

Key: `inlay-hints-length-limit`; Description: Maximum displayed length (non-zero number) of inlay hints; Default: Unset by default

Key: `display-color-swatches`; Description: Show color swatches next to colors; Default: `true`

Key: `display-signature-help-docs`; Description: Display docs under signature help popup; Default: `true`

Key: `snippets`; Description: Enables snippet completions. Requires a server restart (`:lsp-restart`) to take effect after `:config-reload`/`:set`.; Default: `true`

Key: `goto-reference-include-declaration`; Description: Include declaration in the goto references popup.; Default: `true`


[^1]: By default, a progress spinner is shown in the statusline beside the file path.

[^2]: You may also have to activate them in the language server config for them to appear, not just in Helix. Inlay hints in Helix are still being improved on and may be a little bit laggy/janky under some circumstances. Please report any bugs you see so we can fix them!

### `[editor.cursor-shape]` Section

Defines the shape of cursor in each mode.
Valid values for these options are `block`, `bar`, `underline`, or `hidden`.

💡 Due to limitations of the terminal environment, only the primary cursor can
change shape.

Key: `normal`; Description: Cursor shape in [normal mode][normal mode]; Default: `"block"`

Key: `insert`; Description: Cursor shape in [insert mode][insert mode]; Default: `"block"`

Key: `select`; Description: Cursor shape in [select mode][select mode]; Default: `"block"`


[normal mode]: ./keymap.md#normal-mode
[insert mode]: ./keymap.md#insert-mode
[select mode]: ./keymap.md#select--extend-mode

### `[editor.file-picker]` Section

Set options for file picker and global search. Ignoring a file means it is
not visible in the Helix file picker and global search.

All git related options are only enabled in a git repository.

Key: `hidden`; Description: Enables ignoring hidden files; Default: `true`

Key: `follow-symlinks`; Description: Follow symlinks instead of ignoring them; Default: `true`

Key: `deduplicate-links`; Description: Ignore symlinks that point at files already shown in the picker; Default: `true`

Key: `parents`; Description: Enables reading ignore files from parent directories; Default: `true`

Key: `ignore`; Description: Enables reading `.ignore` files; Default: `true`

Key: `git-ignore`; Description: Enables reading `.gitignore` files; Default: `true`

Key: `git-global`; Description: Enables reading global `.gitignore`, whose path is specified in git's config: `core.excludesfile` option; Default: `true`

Key: `git-exclude`; Description: Enables reading `.git/info/exclude` files; Default: `true`

Key: `max-depth`; Description: Set with an integer value for maximum depth to recurse; Default: Unset by default


Ignore files can be placed locally as `.ignore` or put in your home directory as `~/.ignore`. They support the usual ignore and negative ignore (unignore) rules used in `.gitignore` files.

Additionally, you can use Helix-specific ignore files by creating a local `.helix/ignore` file in the current workspace or a global `ignore` file located in your Helix config directory:
Linux and Mac: `~/.config/helix/ignore`

Windows: `%AppData%\helix\ignore`

Example:

```ini
# unignore in file picker and global search
!.github/
!.gitignore
!.gitattributes
```

### `[editor.file-explorer]` Section

In addition to the options for the file picker and global search, a similar set of options is presented to configure the file explorer separately. However, unlike the file picker, the defaults are set to avoid ignoring most files.

Note that the ignore files consulted by the file explorer when `ignore` is set to true are the same ones used by the file picker, including the aforementioned Helix-specific ignore files.

Key: `hidden`; Description: Enables ignoring hidden files; Default: `false`

Key: `follow-symlinks`; Description: Follow symlinks instead of ignoring them; Default: `false`

Key: `parents`; Description: Enables reading ignore files from parent directories; Default: `false`

Key: `ignore`; Description: Enables reading `.ignore` files; Default: `false`

Key: `git-ignore`; Description: Enables reading `.gitignore` files; Default: `false`

Key: `git-global`; Description: Enables reading global `.gitignore`, whose path is specified in git's config: `core.excludesfile` option; Default: `false`

Key: `git-exclude`; Description: Enables reading `.git/info/exclude` files; Default: `false`

Key: `flatten-dirs`; Description: Enables flattening single child directories; Default: `true`


### `[editor.buffer-picker]` Section

Set options for buffer picker.

Key: `start-position`; Description: Controls behavior for which buffer is initially selected; Default: `current`


Example

```toml
[editor.buffer-picker]
start-position = "previous"
```

### `[editor.auto-pairs]` Section

Enables automatic insertion of pairs to parentheses, brackets, etc. Can be a
simple boolean value, or a specific mapping of pairs of single characters.

To disable auto-pairs altogether, set `auto-pairs` to `false`:

```toml
[editor]
auto-pairs = false # defaults to `true`
```

The default pairs are <code>(){}[]''""``</code>, but these can be customized by
setting `auto-pairs` to a TOML table:

```toml
[editor.auto-pairs]
'(' = ')'
'{' = '}'
'[' = ']'
'"' = '"'
'`' = '`'
'<' = '>'
```

Additionally, this setting can be used in a language config. Unless
the editor setting is `false`, this will override the editor config in
documents with this language.

Example `languages.toml` that adds `<>` and removes `''`

```toml
[[language]]
name = "rust"

[language.auto-pairs]
'(' = ')'
'{' = '}'
'[' = ']'
'"' = '"'
'`' = '`'
'<' = '>'
```

### `[editor.auto-save]` Section

Control auto save behavior.

Key: `focus-lost`; Description: Enable automatic saving on the focus moving away from Helix. Requires [focus event support](https://github.com/helix-editor/helix/wiki/Terminal-Support) from your terminal; Default: `false`

Key: `after-delay.enable`; Description: Enable automatic saving after `auto-save.after-delay.timeout` milliseconds have passed since last edit.; Default: `false`

Key: `after-delay.timeout`; Description: Time in milliseconds since last edit before auto save timer triggers.; Default: `3000`


### `[editor.search]` Section

Search specific options.

Key: `smart-case`; Description: Enable smart case regex searching (case-insensitive unless pattern contains upper case characters); Default: `true`

Key: `wrap-around`; Description: Whether the search should wrap after depleting the matches; Default: `true`


### `[editor.whitespace]` Section

Options for rendering whitespace with visible characters. Use `:set whitespace.render all` to temporarily enable visible whitespace.

Key: `render`; Description: Whether to render whitespace. May either be `all` or `none`, or a table with sub-keys `space`, `nbsp`, `nnbsp`, `tab`, and `newline`; Default: `"none"`

Key: `characters`; Description: Literal characters to use when rendering whitespace. Sub-keys may be any of `tab`, `space`, `nbsp`, `nnbsp`, `newline` or `tabpad`; Default: See example below


Example

```toml
[editor.whitespace]
render = "all"
# or control each character
[editor.whitespace.render]
space = "all"
tab = "all"
nbsp = "none"
nnbsp = "none"
newline = "none"

[editor.whitespace.characters]
space = "·"
nbsp = "⍽"
nnbsp = "␣"
tab = "→"
newline = "⏎"
tabpad = "·" # Tabs will look like "→···" (depending on tab width)
```

### `[editor.indent-guides]` Section

Options for rendering vertical indent guides.

Key: `render`; Description: Whether to render indent guides; Default: `false`

Key: `character`; Description: Literal character to use for rendering the indent guide; Default: `"│"`

Key: `skip-levels`; Description: Number of indent levels to skip; Default: `0`


Example:

```toml
[editor.indent-guides]
render = true
character = "╎" # Some characters that work well: "▏", "┆", "┊", "⸽"
skip-levels = 1
```

### `[editor.gutters]` Section

For simplicity, `editor.gutters` accepts an array of gutter types, which will
use default settings for all gutter components.

```toml
[editor]
gutters = ["diff", "diagnostics", "line-numbers", "spacer"]
```

To customize the behavior of gutters, the `[editor.gutters]` section must
be used. This section contains top level settings, as well as settings for
specific gutter components as subsections.

Key: `layout`; Description: A vector of gutters to display; Default: `["diagnostics", "spacer", "line-numbers", "spacer", "diff"]`


Example:

```toml
[editor.gutters]
layout = ["diff", "diagnostics", "line-numbers", "spacer"]
```

#### `[editor.gutters.line-numbers]` Section

Options for the line number gutter

Key: `min-width`; Description: The minimum number of characters to use; Default: `3`


Example:

```toml
[editor.gutters.line-numbers]
min-width = 1
```

#### `[editor.gutters.diagnostics]` Section

Currently unused

#### `[editor.gutters.diff]` Section

The `diff` gutter option displays colored bars indicating whether a `git` diff represents that a line was added, removed or changed.
These colors are controlled by the theme attributes `diff.plus`, `diff.minus` and `diff.delta`.

Other diff providers will eventually be supported by a future plugin system.

There are currently no options for this section.

#### `[editor.gutters.spacer]` Section

Currently unused

#### `[editor.gutters.code-action-hint]` Section

The `code-action-hint` gutter option displays an indicator for whether a code action is available at current selection.

There are currently no options for this section.

### `[editor.soft-wrap]` Section

Options for soft wrapping lines that exceed the view width:

Key: `enable`; Description: Whether soft wrapping is enabled.; Default: `false`

Key: `max-wrap`; Description: Maximum free space left at the end of the line.; Default: `20`

Key: `max-indent-retain`; Description: Maximum indentation to carry over when soft wrapping a line.; Default: `40`

Key: `wrap-indicator`; Description: Text inserted before soft wrapped lines, highlighted with `ui.virtual.wrap`; Default: `"↪ "`

Key: `wrap-at-text-width`; Description: Soft wrap at `text-width` instead of using the full viewport size.; Default: `false`


Example:

```toml
[editor.soft-wrap]
enable = true
max-wrap = 25 # increase value to reduce forced mid-word wrapping
max-indent-retain = 0
wrap-indicator = ""  # set wrap-indicator to "" to hide it
```

### `[editor.smart-tab]` Section

Options for navigating and editing using tab key.

Key: `enable`; Description: If set to true, then when the cursor is in a position with non-whitespace to its left, instead of inserting a tab, it will run `move_parent_node_end`. If there is only whitespace to the left, then it inserts a tab as normal. With the default bindings, to explicitly insert a tab character, press Shift-tab.; Default: `true`

Key: `supersede-menu`; Description: Normally, when a menu is on screen, such as when auto complete is triggered, the tab key is bound to cycling through the items. This means when menus are on screen, one cannot use the tab key to trigger the `smart-tab` command. If this option is set to true, the `smart-tab` command always takes precedence, which means one cannot use the tab key to cycle through menu items. One of the other bindings must be used instead, such as arrow keys or `C-n`/`C-p`.; Default: `false`


Due to lack of support for S-tab in some terminals, the default keybindings don't fully embrace smart-tab editing experience. If you enjoy smart-tab navigation and a terminal that supports the [Enhanced Keyboard protocol](https://github.com/helix-editor/helix/wiki/Terminal-Support#enhanced-keyboard-protocol), consider setting extra keybindings:

```toml
[keys.normal]
tab = "move_parent_node_end"
S-tab = "move_parent_node_start"

[keys.insert]
S-tab = "move_parent_node_start"

[keys.select]
tab = "extend_parent_node_end"
S-tab = "extend_parent_node_start"
```

### `[editor.inline-diagnostics]` Section

Options for rendering diagnostics inside the text like shown below

```text
fn main() {
  let foo = bar;
            └─ no such value in this scope
}
```

Key: `cursor-line`; Description: The minimum severity that a diagnostic must have to be shown inline on the line that contains the primary cursor. Set to `disable` to not show any diagnostics inline. This option does not have any effect when in insert-mode and will only take effect 350ms after moving the cursor to a different line.; Default: `"warning"`

Key: `other-lines`; Description: The minimum severity that a diagnostic must have to be shown inline on a line that does not contain the cursor-line. Set to `disable` to not show any diagnostics inline.; Default: `"disable"`

Key: `prefix-len`; Description: How many horizontal bars `─` are rendered before the diagnostic text.; Default: `1`

Key: `max-wrap`; Description: Equivalent of the `editor.soft-wrap.max-wrap` option for diagnostics.; Default: `20`

Key: `max-diagnostics`; Description: Maximum number of diagnostics to render inline for a given line; Default: `10`


The allowed values for `cursor-line` and `other-lines` are: `error`, `warning`, `info`, `hint`.

The (first) diagnostic with the highest severity that is not shown inline is rendered at the end of the line (as long as its severity is higher than the `end-of-line-diagnostics` config option):

```text
fn main() {
  let baz = 1;
  let foo = bar; a local variable with a similar name exists: baz
            └─ no such value in this scope
}
```

### `[editor.word-completion]` Section

Options for controlling completion of words from open buffers.

Key: `enable`; Description: Whether word completion is enabled; Default: `true`

Key: `trigger-length`; Description: Number of word characters to type before triggering completion; Default: `7`


Example:

```toml
[editor.word-completion]
enable = true
# Set the trigger length lower so that words are completed more often
trigger-length = 4
```

### `[editor.workspace-trust]` Section

Controls implicit workspace trust. See the [workspace
trust](./workspace-trust.md) chapter for the full feature.

Key: `level`; Description: The default level of trust for every workspace.; Default: `"servers"`

Key: `prompt`; Description: Whether to show a modal when opening a file in an untrusted workspace.; Default: `true`

Key: `trusted`; Description: Glob patterns whose matching workspaces are trusted without a grant.; Default: `[]`


Example:

```toml
[editor.workspace-trust]
# Even if `false`, the statusline `[⚠]` indicator is still shown.
prompt = false

# "none":     prompt for every workspace.
# "servers":  trust LSP and DAP launches but still gate local config and git;
#             .helix/config.toml, .helix/languages.toml, etc. need :workspace-trust.
# "insecure": trust everything (discouraged).
level = "servers"

# Discouraged: skips .helix/ change detection and trusts anything that lands
# under a matching path. `~` and environment variables are expanded.
trusted = ["~/src/github.com/me/*"]
```
