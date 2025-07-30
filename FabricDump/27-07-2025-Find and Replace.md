https://thevaluable.dev/vim-search-find-replace/

# Vim Search and Replace With Examples: A Concise Summary

This article details Vim's search and replace capabilities, covering basic commands, advanced techniques, and helpful plugins.  The author aims to empower developers to efficiently navigate and manipulate code using Vim's powerful search features.


## Vim Search in the Current File

[00:04:18] **Basics:** The `/` command initiates a forward search, while `?` searches backward. `n` and `N` cycle through results.  `//` repeats the last search.

[00:05:08] **Highlighting Search Results:** `:set hlsearch` enables search highlighting (default in Neovim). `:noh` clears the highlighting.  The author suggests mapping a key (e.g., `<esc>`) to `:noh<cr>` in your `vimrc` for easy clearing.

[00:06:03] **Searching the Word Under the Cursor:** `*` searches forward for the word under the cursor, `g*` searches for partial words. `#` and `g#` perform backward searches.

[00:06:48] **Case Sensitivity:** `/search\C` for case-sensitive, `/search\c` for case-insensitive.  `set ignorecase` and `set smartcase` offer global options in your `vimrc`.


## Vim Search in Multiple Files

[00:07:38] **`vimgrep`:** This command populates the quickfix list with search results.  Examples include `:vimgrep pattern *`, `:vimgrep pattern *.php`, and `:vimgrep pattern **/*.php`. `:cnext`/:cn and `:cprev`/:cp navigate results; `:copen` opens the quickfix window.

[00:09:08] **`grep`:** A faster alternative to `vimgrep` using an external program (usually `grep`).  Configured via `grepprg`.  Similar usage to `vimgrep`.


## Find and Replace

[00:09:58] **Substitution in the Current File:** `:s/pattern/replace/g` substitutes on the current line; `:%s/pattern/replace/g` substitutes in the entire file.  `g` flag for global replacement.  Escaping `/` with `\/` or using a different separator (e.g., `#`) is shown.

[00:11:09] **Find and Replace One Occurrence at a Time:**  `/` to search, `cgn` to change the next occurrence, `n` or `N` to navigate, and `.` to repeat the replacement.

[00:12:01] **Find and Replace in Multiple Files:** Using the arglist (`arg *pattern*`, `argadd *pattern*`, `:argdo`). `:argdo %s/pattern/replace/ge | update` performs the replacement across all files in the arglist; `e` flag prevents errors for non-matches.  The author also demonstrates how to use `bufdo` to perform find and replace on all open buffers.

[00:14:00]  **Combining arglist with `grep` or `vimgrep` and `:cdo`**: Demonstrates searching and then applying a command (`cdo`) to each result in the quickfix list.


## Beyond Vanilla Vim: Search with External Plugins

[00:14:50] **`fzf.vim` and `fzf`:** A fast search tool for files, buffers, history, etc.  `:Files`, `:Buffers`, `:History` are examples of its usage.

[00:15:52] **`ripgrep`:** A fast CLI search tool, often paired with `fzf`. `:Rg pattern` searches using ripgrep.  Configuration details are referenced.  Can be used with `:grep` by setting `grepprg=rg\ --vimgrep`.

[00:16:53] **`ferret`:**  A plugin for searching and replacing across multiple files, using `ripgrep` by default.  `:Ack pattern` initiates the search.

[00:17:30] **`coc.nvim` and `:CocSearch`:**  Leverages `ripgrep` for powerful searches.  Supports options like `-A` to display lines after the match.


## Conclusion

[00:18:05] The article concludes by summarizing the author's preferred workflow (built-in Vim for single files, `fzf`, `ripgrep`, and `coc.nvim` for projects) and encourages readers to share their own search techniques.  The overall message is to harness Vim's search capabilities, supplemented by powerful plugins, for efficient development.
