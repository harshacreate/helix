## Keymap

[Normal mode](#normal-mode)

[Movement](#movement)

[Changes](#changes)

    - [Shell](#shell)
[Selection manipulation](#selection-manipulation)

[Search](#search)

[Minor modes](#minor-modes)

    - [View mode](#view-mode)
    - [Goto mode](#goto-mode)
    - [Match mode](#match-mode)
    - [Window mode](#window-mode)
    - [Space mode](#space-mode)
      - [Popup](#popup)
      - [Completion Menu](#completion-menu)
      - [Signature-help Popup](#signature-help-popup)
    - [Unimpaired](#unimpaired)
[Insert mode](#insert-mode)

[Select / extend mode](#select--extend-mode)

[Picker](#picker)

[Prompt](#prompt)

💡 Mappings marked (LSP) require an active language server for the file.

💡 Mappings marked (TS) require a tree-sitter grammar for the file type.

⚠️ Some terminals' default key mappings conflict with Helix's. If any of the mappings described on this page do not work as expected, check your terminal's mappings to ensure they do not conflict. See the [wiki](https://github.com/helix-editor/helix/wiki/Terminal-Support) for known conflicts.

## Normal mode

Normal mode is the default mode when you launch helix. You can return to it from other modes by pressing the `Escape` key.

### Movement

NOTE: Unlike Vim, `f`, `F`, `t` and `T` are not confined to the current line.

Hereafter, `<n>` represents an integer by typing a sequence of digits.

Key: `h`, `Left`; Description: Move left; Command: `move_char_left`

Key: `j`, `Down`; Description: Move down; Command: `move_visual_line_down`

Key: `k`, `Up`; Description: Move up; Command: `move_visual_line_up`

Key: `l`, `Right`; Description: Move right; Command: `move_char_right`

Key: `w`; Description: Move next word start; Command: `move_next_word_start`

Key: `b`; Description: Move previous word start; Command: `move_prev_word_start`

Key: `e`; Description: Move next word end; Command: `move_next_word_end`

Key: `W`; Description: Move next WORD start; Command: `move_next_long_word_start`

Key: `B`; Description: Move previous WORD start; Command: `move_prev_long_word_start`

Key: `E`; Description: Move next WORD end; Command: `move_next_long_word_end`

Key: `t`; Description: Find till next char; Command: `find_till_char`

Key: `f`; Description: Find next char; Command: `find_next_char`

Key: `T`; Description: Find till previous char; Command: `till_prev_char`

Key: `F`; Description: Find previous char; Command: `find_prev_char`

Key: `<n>G`, `<n>gg`; Description: Go to line number `<n>`; Command: `goto_line`

Key: `Alt-.`; Description: Repeat last motion (`f`, `t`, `m`, `[` or `]`); Command: `repeat_last_motion`

Key: `Home`; Description: Move to the start of the line; Command: `goto_line_start`

Key: `End`; Description: Move to the end of the line; Command: `goto_line_end`

Key: `Ctrl-b`, `PageUp`; Description: Move page up; Command: `page_up`

Key: `Ctrl-f`, `PageDown`; Description: Move page down; Command: `page_down`

Key: `Ctrl-u`; Description: Move cursor and page half page up; Command: `page_cursor_half_up`

Key: `Ctrl-d`; Description: Move cursor and page half page down; Command: `page_cursor_half_down`

Key: `Ctrl-i`; Description: Jump forward on the jumplist; Command: `jump_forward`

Key: `Ctrl-o`; Description: Jump backward on the jumplist; Command: `jump_backward`

Key: `Ctrl-s`; Description: Save the current selection to the jumplist; Command: `save_selection`


### Changes

| Key         | Description                                                          | Command                   |
| -----       | -----------                                                          | -------                   |
| `r`         | Replace with a character                                             | `replace`                 |
| `R`         | Replace with yanked text                                             | `replace_with_yanked`     |
| `~`         | Switch case of the selected text                                     | `switch_case`             |
| `` ` ``     | Set the selected text to lower case                                  | `switch_to_lowercase`     |
| `` Alt-` `` | Set the selected text to upper case                                  | `switch_to_uppercase`     |
| `i`         | Insert before selection                                              | `insert_mode`             |
| `a`         | Insert after selection (append)                                      | `append_mode`             |
| `I`         | Insert at the start of the line                                      | `insert_at_line_start`    |
| `A`         | Insert at the end of the line                                        | `insert_at_line_end`      |
| `o`         | Open new line below selection                                        | `open_below`              |
| `O`         | Open new line above selection                                        | `open_above`              |
| `.`         | Repeat last insert                                                   | N/A                       |
| `u`         | Undo change                                                          | `undo`                    |
| `U`         | Redo change                                                          | `redo`                    |
| `Alt-u`     | Move backward in history                                             | `earlier`                 |
| `Alt-U`     | Move forward in history                                              | `later`                   |
| `y`         | Yank selection                                                       | `yank`                    |
| `p`         | Paste after selection                                                | `paste_after`             |
| `P`         | Paste before selection                                               | `paste_before`            |
| `"` `<reg>` | Select a register to yank to or paste from                           | `select_register`         |
| `>`         | Indent selection                                                     | `indent`                  |
| `<`         | Unindent selection                                                   | `unindent`                |
| `=`         | Format selection (LSP)                                           | `format_selections`       |
| `d`         | Delete selection                                                     | `delete_selection`        |
| `Alt-d`     | Delete selection, without yanking                                    | `delete_selection_noyank` |
| `c`         | Change selection (delete and enter insert mode)                      | `change_selection`        |
| `Alt-c`     | Change selection (delete and enter insert mode, without yanking)     | `change_selection_noyank` |
| `Ctrl-a`    | Increment object (number) under cursor                               | `increment`               |
| `Ctrl-x`    | Decrement object (number) under cursor                               | `decrement`               |
| `Q`         | Start/stop macro recording to the selected register (experimental)   | `record_macro`            |
| `q`         | Play back a recorded macro from the selected register (experimental) | `replay_macro`            |
| `Ctrl-z`    | Suspend Helix and return to the shell (resume with `fg`)             | `suspend`                 |

#### Shell

Key: <code>&#124;</code>; Description: Pipe each selection through shell command, replacing with output; Command: `shell_pipe`

Key: <code>Alt-&#124;</code>; Description: Pipe each selection into shell command, ignoring output; Command: `shell_pipe_to`

Key: `!`; Description: Run shell command, inserting output before each selection; Command: `shell_insert_output`

Key: `Alt-!`; Description: Run shell command, appending output after each selection; Command: `shell_append_output`

Key: `$`; Description: Pipe each selection into shell command, keep selections where command returned 0; Command: `shell_keep_pipe`


### Selection manipulation

Key: `s`; Description: Select all regex matches inside selections; Command: `select_regex`

Key: `S`; Description: Split selection into sub selections on regex matches; Command: `split_selection`

Key: `Alt-s`; Description: Split selection on newlines; Command: `split_selection_on_newline`

Key: `Alt-minus`; Description: Merge selections; Command: `merge_selections`

Key: `Alt-_`; Description: Merge consecutive selections; Command: `merge_consecutive_selections`

Key: `&`; Description: Align selection in columns; Command: `align_selections`

Key: `_`; Description: Trim whitespace from the selection; Command: `trim_selections`

Key: `;`; Description: Collapse selection onto a single cursor; Command: `collapse_selection`

Key: `Alt-;`; Description: Flip selection cursor and anchor; Command: `flip_selections`

Key: `Alt-:`; Description: Ensures the selection is in forward direction; Command: `ensure_selections_forward`

Key: `,`; Description: Keep only the primary selection; Command: `keep_primary_selection`

Key: `Alt-,`; Description: Remove the primary selection; Command: `remove_primary_selection`

Key: `C`; Description: Copy selection onto the next line (Add cursor below); Command: `copy_selection_on_next_line`

Key: `Alt-C`; Description: Copy selection onto the previous line (Add cursor above); Command: `copy_selection_on_prev_line`

Key: `(`; Description: Rotate main selection backward; Command: `rotate_selections_backward`

Key: `)`; Description: Rotate main selection forward; Command: `rotate_selections_forward`

Key: `Alt-(`; Description: Rotate selection contents backward; Command: `rotate_selection_contents_backward`

Key: `Alt-)`; Description: Rotate selection contents forward; Command: `rotate_selection_contents_forward`

Key: `%`; Description: Select entire file; Command: `select_all`

Key: `x`; Description: Select current line, if already selected, extend to next line; Command: `extend_line_below`

Key: `X`; Description: Extend selection to line bounds (line-wise selection); Command: `extend_to_line_bounds`

Key: `Alt-x`; Description: Shrink selection to line bounds (line-wise selection); Command: `shrink_to_line_bounds`

Key: `J`; Description: Join lines inside selection; Command: `join_selections`

Key: `Alt-J`; Description: Join lines inside selection and select the inserted space; Command: `join_selections_space`

Key: `K`; Description: Keep selections matching the regex; Command: `keep_selections`

Key: `Alt-K`; Description: Remove selections matching the regex; Command: `remove_selections`

Key: `Ctrl-c`; Description: Comment/uncomment the selections; Command: `toggle_comments`

Key: `Alt-o`, `Alt-up`; Description: Expand selection to parent syntax node (TS); Command: `expand_selection`

Key: `Alt-i`, `Alt-down`; Description: Shrink syntax tree object selection (TS); Command: `shrink_selection`

Key: `Alt-p`, `Alt-left`; Description: Select previous sibling node in syntax tree (TS); Command: `select_prev_sibling`

Key: `Alt-n`, `Alt-right`; Description: Select next sibling node in syntax tree (TS); Command: `select_next_sibling`

Key: `Alt-a`; Description: Select all sibling nodes in syntax tree (TS); Command: `select_all_siblings`

Key: `Alt-I`, `Alt-Shift-down`; Description: Select all children nodes in syntax tree (TS); Command: `select_all_children`

Key: `Alt-e`; Description: Move to end of parent node in syntax tree (TS); Command: `move_parent_node_end`

Key: `Alt-b`; Description: Move to start of parent node in syntax tree (TS); Command: `move_parent_node_start`


### Search

Search commands all operate on the `/` register by default. To use a different register, use `"<char>`.

Key: `/`; Description: Search for regex pattern; Command: `search`

Key: `?`; Description: Search for previous pattern; Command: `rsearch`

Key: `n`; Description: Select next search match; Command: `search_next`

Key: `N`; Description: Select previous search match; Command: `search_prev`

Key: `*`; Description: Use current selection as the search pattern, automatically wrapping with `\b` on word boundaries; Command: `search_selection_detect_word_boundaries`

Key: `Alt-*`; Description: Use current selection as the search pattern; Command: `search_selection`


### Minor modes

These sub-modes are accessible from normal mode and typically switch back to normal mode after a command.

Key: `v`; Description: Enter [select (extend) mode](#select--extend-mode); Command: `select_mode`

Key: `g`; Description: Enter [goto mode](#goto-mode); Command: N/A

Key: `m`; Description: Enter [match mode](#match-mode); Command: N/A

Key: `:`; Description: Enter command mode; Command: `command_mode`

Key: `z`; Description: Enter [view mode](#view-mode); Command: N/A

Key: `Z`; Description: Enter sticky [view mode](#view-mode); Command: N/A

Key: `Ctrl-w`; Description: Enter [window mode](#window-mode); Command: N/A

Key: `Space`; Description: Enter [space mode](#space-mode); Command: N/A


These modes (except command mode) can be configured by
[remapping keys](https://docs.helix-editor.com/remapping.html#minor-modes).

#### View mode

Accessed by typing `z` in [normal mode](#normal-mode).

View mode is intended for scrolling and manipulating the view without changing
the selection. The "sticky" variant of this mode (accessed by typing `Z` in
normal mode) is persistent and can be exited using the escape key. This is
useful when you're simply looking over text and not actively editing it.

Key: `z`, `c`; Description: Vertically center the line; Command: `align_view_center`

Key: `t`; Description: Align the line to the top of the screen; Command: `align_view_top`

Key: `b`; Description: Align the line to the bottom of the screen; Command: `align_view_bottom`

Key: `m`; Description: Align the line to the middle of the screen (horizontally); Command: `align_view_middle`

Key: `j`, `down`; Description: Scroll the view downwards; Command: `scroll_down`

Key: `k`, `up`; Description: Scroll the view upwards; Command: `scroll_up`

Key: `Ctrl-f`, `PageDown`; Description: Move page down; Command: `page_down`

Key: `Ctrl-b`, `PageUp`; Description: Move page up; Command: `page_up`

Key: `Ctrl-u`; Description: Move cursor and page half page up; Command: `page_cursor_half_up`

Key: `Ctrl-d`; Description: Move cursor and page half page down; Command: `page_cursor_half_down`


#### Goto mode

Accessed by typing `g` in [normal mode](#normal-mode).

Jumps to various locations.

Key: `<n>g`; Description: Go to line number `<n>`; Command: `goto_file_start`

Key: `g`; Description: Go to the start of the file; Command: `goto_file_start`

Key: <code>&lt;n&gt;&#124;</code>; Description: Go to column number `<n>`; Command: `goto_column`

Key: <code>&#124;</code>; Description: Go to the start of line; Command: `goto_column`

Key: `e`; Description: Go to the end of the file; Command: `goto_last_line`

Key: `f`; Description: Go to files/URLs in selections; Command: `goto_file`

Key: `h`; Description: Go to the start of the line; Command: `goto_line_start`

Key: `l`; Description: Go to the end of the line; Command: `goto_line_end`

Key: `s`; Description: Go to first non-whitespace character of the line; Command: `goto_first_nonwhitespace`

Key: `t`; Description: Go to the top of the screen; Command: `goto_window_top`

Key: `c`; Description: Go to the middle of the screen; Command: `goto_window_center`

Key: `b`; Description: Go to the bottom of the screen; Command: `goto_window_bottom`

Key: `d`; Description: Go to definition (LSP); Command: `goto_definition`

Key: `D`; Description: Go to declaration (LSP); Command: `goto_declaration`

Key: `y`; Description: Go to type definition (LSP); Command: `goto_type_definition`

Key: `r`; Description: Go to references (LSP); Command: `goto_reference`

Key: `i`; Description: Go to implementation (LSP); Command: `goto_implementation`

Key: `a`; Description: Go to the last accessed/alternate file; Command: `goto_last_accessed_file`

Key: `m`; Description: Go to the last modified/alternate file; Command: `goto_last_modified_file`

Key: `n`; Description: Go to next buffer; Command: `goto_next_buffer`

Key: `p`; Description: Go to previous buffer; Command: `goto_previous_buffer`

Key: `.`; Description: Go to last modification in current file; Command: `goto_last_modification`

Key: `j`; Description: Move down textual (instead of visual) line; Command: `move_line_down`

Key: `k`; Description: Move up textual (instead of visual) line; Command: `move_line_up`

Key: `w`; Description: Show labels at each word and select the word that belongs to the entered labels; Command: `goto_word`


#### Match mode

Accessed by typing `m` in [normal mode](#normal-mode).

Please refer to the relevant sections for detailed explanations about [surround](./surround.md) and [textobjects](./textobjects.md).

Key: `m`; Description: Goto matching bracket (TS); Command: `match_brackets`

Key: `s` `<char>`; Description: Surround current selection with `<char>`; Command: `surround_add`

Key: `r` `<from><to>`; Description: Replace surround character `<from>` with `<to>`; Command: `surround_replace`

Key: `d` `<char>`; Description: Delete surround character `<char>`; Command: `surround_delete`

Key: `a` `<object>`; Description: Select around textobject; Command: `select_textobject_around`

Key: `i` `<object>`; Description: Select inside textobject; Command: `select_textobject_inner`


TODO: Mappings for selecting syntax nodes (a superset of `[`).

#### Window mode

Accessed by typing `Ctrl-w` in [normal mode](#normal-mode).

This layer is similar to Vim keybindings as Kakoune does not support windows.

Key: `w`, `Ctrl-w`; Description: Switch to next window; Command: `rotate_view`

Key: `v`, `Ctrl-v`; Description: Vertical right split; Command: `vsplit`

Key: `s`, `Ctrl-s`; Description: Horizontal bottom split; Command: `hsplit`

Key: `t`, `Ctrl-t`; Description: Transpose the two adjacent splits; Command: `transpose_view`

Key: `f`; Description: Go to files/URLs in selections in horizontal splits; Command: `goto_file_hsplit`

Key: `F`; Description: Go to files/URLs in selections in vertical splits; Command: `goto_file_vsplit`

Key: `h`, `Ctrl-h`, `Left`; Description: Move to left split; Command: `jump_view_left`

Key: `j`, `Ctrl-j`, `Down`; Description: Move to split below; Command: `jump_view_down`

Key: `k`, `Ctrl-k`, `Up`; Description: Move to split above; Command: `jump_view_up`

Key: `l`, `Ctrl-l`, `Right`; Description: Move to right split; Command: `jump_view_right`

Key: `q`, `Ctrl-q`; Description: Close current window; Command: `wclose`

Key: `o`, `Ctrl-o`; Description: Only keep the current window, closing all the others; Command: `wonly`

Key: `H`; Description: Swap window to the left; Command: `swap_view_left`

Key: `J`; Description: Swap window downwards; Command: `swap_view_down`

Key: `K`; Description: Swap window upwards; Command: `swap_view_up`

Key: `L`; Description: Swap window to the right; Command: `swap_view_right`

Key: `ns`, `nCtrl-s`; Description: New horizontal split with a scratch buffer; Command: `hsplit_new`

Key: `nv`, `nCtrl-v`; Description: New vertical split with a scratch buffer; Command: `vsplit_new`


#### Space mode

Accessed by typing `Space` in [normal mode](#normal-mode).

This layer is a kludge of mappings, mostly pickers.

Key: `f`; Description: Open file picker at LSP workspace root; Command: `file_picker`

Key: `F`; Description: Open file picker at current working directory; Command: `file_picker_in_current_directory`

Key: `e`; Description: Open file explorer at workspace root; Command: `file_explorer`

Key: `.`; Description: Open file explorer at current buffer's directory; Command: `file_explorer_in_current_buffer_directory`

Key: `b`; Description: Open buffer picker; Command: `buffer_picker`

Key: `j`; Description: Open jumplist picker; Command: `jumplist_picker`

Key: `g`; Description: Open changed file picker; Command: `changed_file_picker`

Key: `G`; Description: Debug (experimental); Command: N/A

Key: `k`; Description: Show documentation for item under cursor in a [popup](#popup) (LSP); Command: `hover`

Key: `s`; Description: Open document symbol picker (LSP or TS); Command: `lsp_or_syntax_symbol_picker`

Key: `S`; Description: Open workspace symbol picker (LSP or TS); Command: `lsp_or_syntax_workspace_symbol_picker`

Key: `d`; Description: Open document diagnostics picker (LSP); Command: `diagnostics_picker`

Key: `D`; Description: Open workspace diagnostics picker (LSP); Command: `workspace_diagnostics_picker`

Key: `r`; Description: Rename symbol (LSP); Command: `rename_symbol`

Key: `a`; Description: Apply code action (LSP); Command: `code_action`

Key: `h`; Description: Select symbol references (LSP); Command: `select_references_to_symbol_under_cursor`

Key: `'`; Description: Open last fuzzy picker; Command: `last_picker`

Key: `w`; Description: Enter [window mode](#window-mode); Command: N/A

Key: `c`; Description: Comment/uncomment selections; Command: `toggle_comments`

Key: `C`; Description: Block comment/uncomment selections; Command: `toggle_block_comments`

Key: `Alt-c`; Description: Line comment/uncomment selections; Command: `toggle_line_comments`

Key: `p`; Description: Paste system clipboard after selections; Command: `paste_clipboard_after`

Key: `P`; Description: Paste system clipboard before selections; Command: `paste_clipboard_before`

Key: `y`; Description: Yank selections to clipboard; Command: `yank_to_clipboard`

Key: `Y`; Description: Yank main selection to clipboard; Command: `yank_main_selection_to_clipboard`

Key: `R`; Description: Replace selections by clipboard contents; Command: `replace_selections_with_clipboard`

Key: `/`; Description: Global search in workspace folder; Command: `global_search`

Key: `?`; Description: Open command palette; Command: `command_palette`


💡 Global search displays results in a fuzzy picker, use `Space + '` to bring it back up after opening a file.

##### Popup

Displays documentation for item under cursor. Remapping currently not supported.

`Ctrl-u`: Scroll up

`Ctrl-d`: Scroll down


##### Completion Menu

Displays documentation for the selected completion item. Remapping currently not supported.

`Shift-Tab`, `Ctrl-p`, `Up`: Previous entry

`Tab`, `Ctrl-n`, `Down`: Next entry

`Enter`: Close menu and accept completion

`Ctrl-c`: Close menu and reject completion


Any other keypresses result in the completion being accepted.

##### Signature-help Popup

Displays the signature of the selected completion item. Remapping currently not supported.

`Alt-p`: Previous signature

`Alt-n`: Next signature


#### Unimpaired

These mappings are in the style of [vim-unimpaired](https://github.com/tpope/vim-unimpaired).

Key: `]d`; Description: Go to next diagnostic (LSP); Command: `goto_next_diag`

Key: `[d`; Description: Go to previous diagnostic (LSP); Command: `goto_prev_diag`

Key: `]D`; Description: Go to last diagnostic in document (LSP); Command: `goto_last_diag`

Key: `[D`; Description: Go to first diagnostic in document (LSP); Command: `goto_first_diag`

Key: `]f`; Description: Go to next function (TS); Command: `goto_next_function`

Key: `[f`; Description: Go to previous function (TS); Command: `goto_prev_function`

Key: `]t`; Description: Go to next type definition (TS); Command: `goto_next_class`

Key: `[t`; Description: Go to previous type definition (TS); Command: `goto_prev_class`

Key: `]a`; Description: Go to next argument/parameter (TS); Command: `goto_next_parameter`

Key: `[a`; Description: Go to previous argument/parameter (TS); Command: `goto_prev_parameter`

Key: `]c`; Description: Go to next comment (TS); Command: `goto_next_comment`

Key: `[c`; Description: Go to previous comment (TS); Command: `goto_prev_comment`

Key: `]e`; Description: Go to next entry (TS); Command: `goto_next_entry`

Key: `[e`; Description: Go to previous entry (TS); Command: `goto_prev_entry`

Key: `]T`; Description: Go to next test (TS); Command: `goto_next_test`

Key: `[T`; Description: Go to previous test (TS); Command: `goto_prev_test`

Key: `]p`; Description: Go to next paragraph; Command: `goto_next_paragraph`

Key: `[p`; Description: Go to previous paragraph; Command: `goto_prev_paragraph`

Key: `]g`; Description: Go to next change; Command: `goto_next_change`

Key: `[g`; Description: Go to previous change; Command: `goto_prev_change`

Key: `]G`; Description: Go to last change; Command: `goto_last_change`

Key: `[G`; Description: Go to first change; Command: `goto_first_change`

Key: `[x`; Description: Go to next (X)HTML element; Command: `goto_next_xml_element`

Key: `]x`; Description: Go to previous (X)HTML element; Command: `goto_prev_xml_element`

Key: `]Space`; Description: Add newline below; Command: `add_newline_below`

Key: `[Space`; Description: Add newline above; Command: `add_newline_above`


## Insert mode

Accessed by typing `i` in [normal mode](#normal-mode).

Insert mode bindings are minimal by default. Helix is designed to
be a modal editor, and this is reflected in the user experience and internal
mechanics. Changes to the text are only saved for undos when
escaping from insert mode to normal mode.

💡 New users are strongly encouraged to learn the modal editing paradigm
to get the smoothest experience.

Key: `Escape`; Description: Switch to normal mode; Command: `normal_mode`

Key: `Ctrl-s`; Description: Commit undo checkpoint; Command: `commit_undo_checkpoint`

Key: `Ctrl-x`; Description: Autocomplete; Command: `completion`

Key: `Ctrl-r`; Description: Insert a register content; Command: `insert_register`

Key: `Ctrl-w`, `Alt-Backspace`; Description: Delete previous word; Command: `delete_word_backward`

Key: `Alt-d`, `Alt-Delete`; Description: Delete next word; Command: `delete_word_forward`

Key: `Ctrl-u`; Description: Delete to start of line; Command: `kill_to_line_start`

Key: `Ctrl-k`; Description: Delete to end of line; Command: `kill_to_line_end`

Key: `Ctrl-h`, `Backspace`, `Shift-Backspace`; Description: Delete previous char; Command: `delete_char_backward`

Key: `Ctrl-d`, `Delete`; Description: Delete next char; Command: `delete_char_forward`

Key: `Ctrl-j`, `Enter`; Description: Insert new line; Command: `insert_newline`

Key: `Tab`; Description: [Smart tab] (configurable); Command: `smart_tab`

Key: `Shift-Tab`; Description: Insert tab; Command: `insert_tab`


[Smart tab]: ./editor.md#editorsmart-tab-section

These keys are not recommended, but are included for new users less familiar
with modal editors.

Key: `Up`; Description: Move to previous line; Command: `move_line_up`

Key: `Down`; Description: Move to next line; Command: `move_line_down`

Key: `Left`; Description: Backward a char; Command: `move_char_left`

Key: `Right`; Description: Forward a char; Command: `move_char_right`

Key: `PageUp`; Description: Move one page up; Command: `page_up`

Key: `PageDown`; Description: Move one page down; Command: `page_down`

Key: `Home`; Description: Move to line start; Command: `goto_line_start`

Key: `End`; Description: Move to line end; Command: `goto_line_end_newline`


As you become more comfortable with modal editing, you may want to disable some
insert mode bindings. You can do this by editing your `config.toml` file.

```toml
[keys.insert]
up = "no_op"
down = "no_op"
left = "no_op"
right = "no_op"
pageup = "no_op"
pagedown = "no_op"
home = "no_op"
end = "no_op"
```

## Select / extend mode

Accessed by typing `v` in [normal mode](#normal-mode).

Select mode echoes Normal mode, but changes any movements to extend
selections rather than replace them. Goto motions are also changed to
extend, so that `vgl`, for example, extends the selection to the end of
the line.

Search is also affected. By default, `n` and `N` will remove the current
selection and select the next instance of the search term. Toggling this
mode before pressing `n` or `N` makes it possible to keep the current
selection. Toggling it on and off during your iterative searching allows
you to selectively add search terms to your selections.

## Picker

Keys to use within picker. Remapping currently not supported.
See the documentation page on [pickers](./pickers.md) for more info.
[Prompt](#prompt) keybinds also work in pickers, except where they conflict with picker keybinds.

`Shift-Tab`, `Up`, `Ctrl-p`: Previous entry

`Tab`, `Down`, `Ctrl-n`: Next entry

`PageUp`, `Ctrl-u`: Page up

`PageDown`, `Ctrl-d`: Page down

`Home`: Go to first entry

`End`: Go to last entry

`Enter`: Open selected

`Alt-Enter`: Open selected in the background without closing the picker

`Ctrl-s`: Open horizontally

`Ctrl-v`: Open vertically

`Ctrl-t`: Toggle preview

`Escape`, `Ctrl-c`: Close picker


## Prompt

Keys to use within prompt, Remapping currently not supported.

`Escape`, `Ctrl-c`: Close prompt

`Alt-b`, `Ctrl-Left`: Backward a word

`Ctrl-b`, `Left`: Backward a char

`Alt-f`, `Ctrl-Right`: Forward a word

`Ctrl-f`, `Right`: Forward a char

`Ctrl-e`, `End`: Move prompt end

`Ctrl-a`, `Home`: Move prompt start

`Ctrl-w`, `Alt-Backspace`, `Ctrl-Backspace`: Delete previous word

`Alt-d`, `Alt-Delete`, `Ctrl-Delete`: Delete next word

`Ctrl-u`: Delete to start of line

`Ctrl-k`: Delete to end of line

`Backspace`, `Ctrl-h`, `Shift-Backspace`: Delete previous char

`Delete`, `Ctrl-d`: Delete next char

`Ctrl-s`: Insert a word under doc cursor, may be changed to Ctrl-r Ctrl-w later

`Ctrl-p`, `Up`: Select previous history

`Ctrl-n`, `Down`: Select next history

`Ctrl-r`: Insert the content of the register selected by following input char

`Tab`: Select next completion item

`BackTab`: Select previous completion item

`Enter`: Open selected
