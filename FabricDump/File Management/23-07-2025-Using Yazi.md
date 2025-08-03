# Yazi: A Terminal-Based File Manager Tutorial

This video provides a comprehensive tutorial on using Yazi, a terminal-based file manager written in Rust.  The creator aims to demonstrate Yazi's features and how to configure it for optimal workflow.  A blog post with accompanying code is linked in the description.

## Installation and Setup [00:00:28]

*   The video begins by showing how to install Yazi using Homebrew on macOS.  [00:00:38]
*   Several optional dependencies are highlighted for a smoother experience. [00:00:50]
*   After installation, typing `yazi` and pressing Enter opens the file manager. [00:01:15]
*   The video demonstrates how to add code to your `.zshrc` file (or equivalent for other shells) to automatically return to the previous directory after exiting Yazi. [00:01:36]  This ensures a seamless transition between Yazi and the terminal.


## Configuration [00:02:55]

*   The tutorial explains how to configure Yazi by creating three TOML files in `~/.config/yazi`: `yazi.toml` (general settings), `keymap.toml` (keybindings), and `theme.toml` (appearance). [00:02:55]
*   The creator copies the default configuration files from the Yazi documentation to customize the settings. [00:03:55]
*   Key configuration options are explained, including pane sizing, sorting (case-sensitive/insensitive), and showing hidden files. [00:04:50]


## Keybindings and Navigation [00:08:10]

*   Basic navigation: `j` and `k` move up and down, `h` and `l` move left and right (similar to Vim). [00:08:10]
*   `gg` goes to the top, `Shift+g` goes to the bottom. [00:08:48]
*   `z` (with optional addons) allows jumping to recently visited directories. [00:08:57]
*   `Z` (with fzf) provides fuzzy-finding capabilities for directories. [00:09:25]
*   `Shift+h` goes back to the previous directory, `Shift+l` goes forward. [00:09:55]
*   `o` or Enter opens the selected file in the default editor (configurable via environment variable). [00:10:00]
*   Space bar selects multiple files, `y` yanks (copies), `p` pastes, `X` cuts, `D` deletes (moves to trash), `Shift+x` undoes delete. [00:10:55]
*   `Tab` shows file information. [00:11:35]
*   `Esc` cancels selection, `Ctrl+a` (or configurable) selects all files. [00:11:45]
*   `.` toggles hidden file visibility. [00:12:05]
*   `;` runs a shell command in the background, `:` runs a blocking command. [00:12:10]
*   `c` copies file paths, names, or names without extensions. [00:12:20]
*   `/` searches forward, `?` searches backward, `n` and `Shift+n` cycle through search results. [00:12:30]
*   `S` searches for files containing specific text. [00:12:55]
*   `,` sorts files (by size, name, etc.), `m` shows modification time, `o` shows owner. [00:13:15]


## Themes and Customization [00:05:10], [00:14:20]

*   The video shows how to install and enable custom themes using `yapack` (Yazi's plugin manager). [00:14:20]
*   The process of installing the `nightfly` and `catppuccin` themes is demonstrated. [00:14:20]


## Tab Management [00:16:00]

*   `T` creates a new tab, `[` and `]` switch between tabs, `{` and `}` swap tabs. [00:16:00]
*   `Ctrl+c` closes a tab (repeated presses close multiple tabs). [00:16:50]
*   Numbers 1-9 can also be used to switch tabs. [00:16:50]


## Conclusion [00:17:00]

The video concludes with a summary of Yazi's features and a call to action to like, comment, and subscribe.  A mention of the creator's split keyboard shop is also included.

**Key Takeaway:** This video provides a practical, step-by-step guide to installing, configuring, and mastering the Yazi terminal file manager, highlighting its many features and customization options.
