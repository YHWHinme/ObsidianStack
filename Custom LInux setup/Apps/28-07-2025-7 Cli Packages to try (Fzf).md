# 7 Amazing Command Line Tools for Your Terminal

This video demonstrates seven powerful command-line tools, primarily showcasing their use on macOS but applicable to Linux as well.  The presenter utilizes Homebrew for installation, with instructions provided in the video description.

## 1. fzf: Fuzzy Finder for the Command Line

[00:01:08] Introduction to fzf, a fast fuzzy finder. Installation via `brew install fzf`.

[00:01:38] Configuring fzf in the `.zshrc` file (using `neovim` as the editor, but any text editor works). Key bindings are added for fuzzy completion.

[00:02:50] Primary use case: searching for files.  Running `fzf` opens the fuzzy finder; typing filters results.

[00:03:20] Shortcuts:  `Ctrl+T` with a command (e.g., `nvim Ctrl+T`) searches files and directories.

[00:04:00] Using `fzf` with various commands (e.g., `code Ctrl+T` for VS Code).

[00:04:26] `CD ** Tab` automatically opens fzf, showing only directories.

[00:04:45] Navigation within fzf: `Ctrl+J`/`Ctrl+K`, `Ctrl+N`/`Ctrl+P`, or up/down arrows.

[00:05:05] Using `fzf` with other commands and the `**` pattern for directory searches.

[00:05:40] Using `fzf` with `kill` to find and kill processes (using `-9` for forceful termination).

[00:06:12] Multi-selection in fzf: `Tab` to select, `Shift+Tab` to deselect.

[00:06:35] Using `fzf` with environment variables (`unset`, `export`, and aliases).

[00:06:58] Using `Ctrl+R` to search command history.

## 2. FD: Replacing the `find` Command

[00:07:30] Installing `fd` (`brew install fd`).  It replaces the default `find` command used by fzf.

[00:07:55] Configuring `.zshrc` to use `fd`: showing hidden files, stripping the current working directory, and excluding `.git` directories.

[00:08:50]  Customizing `fzf`'s key bindings to use `fd` for file and directory searches.

## 3. Git Integration with fzf

[00:09:16] Cloning `fzf-cache` repository for improved Git integration.

[00:09:42]  Using `Ctrl+G` and `GH` to show Git hashes, enabling easy `git diff` selection.

[00:10:08] Using `Ctrl+G` and `GB` to list branches for `git checkout`.

## 4. bat: A Better `cat`

[00:10:35] Installing `bat` (`brew install bat`).  It provides syntax highlighting for file display.

[00:10:58] Using `bat` with `fzf` to view files.

[00:11:18]  Comparing `bat` and `cat` output, highlighting `bat`'s improved readability.

[00:11:35]  Viewing available themes with `bat --list-themes`.

[00:12:15] Installing custom themes: creating the themes directory, downloading a theme (e.g., `Tokyo Night`), and building with `bat --config-dir ~/.config/bat build`.

[00:13:30] Setting the default theme in `.zshrc`.

## 5. Delta: Enhanced `git diff`

[00:13:50] Installing `Delta` (`brew install delta`). It produces visually appealing diffs.

[00:14:10] Configuring Delta in `.gitconfig` to integrate with Git.

[00:14:40] Using Delta with `git diff` and `Ctrl+G`.

[00:15:00] Enabling side-by-side diffs in `.gitconfig`.

## 6. eza: Enhanced `ls`

[00:15:35] Installing `eza` (`brew install eza`).  A superior alternative to `ls`.

[00:15:50]  Demonstrating `eza`'s options: `-C`, `--color=always`, `--long`, `--git`, `--icon`, and others.

[00:16:45] Creating an alias for `ls` to use `eza` with preferred options.

## 7. fzf Previews with bat and eza

[00:17:22] Configuring fzf previews in `.zshrc` to use `bat` for files and `eza` in tree format for directories.

[00:18:55] Demonstrating previews with `Ctrl+T` and `** Tab`.

## 8. tldr: Concise Command-Line Help

[00:19:25] Installing `tldr` (`brew install tldr`).  Provides user-friendly summaries of commands.

[00:19:50] Example: using `tldr eza`.

## 9. the: Command Autocorrection

[00:20:08] Installing `the` (`brew install the`).  Autocorrects mistyped commands.

[00:20:35] Configuring `the` in `.zshrc`.

## 10. zide: Improved `cd`

[00:21:10] Installing `z` (`brew install z`).  A smarter way to navigate directories.

[00:21:30]  Setting up `z` in `.zshrc`.

[00:22:00] Demonstrating `z`'s functionality for directory navigation.  It remembers recently visited directories.

[00:22:50] Using `z` with partial directory names.

[00:23:35] Using `z` with `cd`-like commands (e.g., `cd ..`).

[00:23:55] Using `z` with fzf for directory selection.

[00:24:15] Setting up a `cd` alias for `z` in `.zshrc`.

[00:24:35] Modifying the fzf theme in `.zshrc`.

[00:25:40]  Conclusion:  links to alacrity setup video and neovim configuration guide.  Call to action: subscribe for future videos.
