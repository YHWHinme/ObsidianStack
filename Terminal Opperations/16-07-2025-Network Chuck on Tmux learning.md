
https://www.youtube.com/watch?v=nTqu6w2wc68

This video serves as a comprehensive introduction to `tmux`, a powerful terminal multiplexer designed to significantly enhance productivity for Linux users, developers, and system administrators. It demonstrates how `tmux` allows users to manage multiple terminal sessions, windows, and panes within a single terminal window, enabling processes to run continuously in the background even after disconnecting.

### Getting Started with `tmux`

*   **[00:00:00] Introduction to `tmux`**: `tmux` is a terminal multiplexer that allows running multiple terminal programs inside one terminal, enabling users to detach from sessions and reattach later from anywhere.
*   **[00:01:25] Setting Up Your Environment**: The video uses a Linode cloud virtual machine (Ubuntu) for demonstration.
*   **[00:02:40] Installing `tmux`**: `tmux` is often pre-installed on many Linux distributions. If not, use `sudo apt install tmux`.
*   **[00:03:00] Starting a `tmux` Session**: Simply type `tmux` in your terminal to start a new session. This creates a terminal running inside your terminal.

### `tmux` Core Concepts: Sessions, Windows, and Panes

`tmux` operates on three layers: **Sessions**, **Windows**, and **Panes**. All `tmux` commands begin with a **prefix key**, which is `Ctrl+b` by default. After pressing the prefix key, you then press the command key.

#### Sessions

*   **[00:05:00] Detaching from a Session**:
    *   To detach from the current session while keeping processes running, press `Ctrl+b` then `d`.
*   **[00:05:40] Reattaching to the Last Session**:
    *   To reattach to your most recent `tmux` session, use `tmux a`.
*   **[00:06:50] Creating a Named Session**:
    *   To create a new `tmux` session with a specific name: `tmux new -s [session_name]` (e.g., `tmux new -s Bob`).
*   **[00:07:40] Listing Sessions**:
    *   To see all active `tmux` sessions: `tmux ls`.
*   **[00:08:00] Attaching to a Specific Session**:
    *   To attach to a specific session by its index or name: `tmux a -t [index_or_name]` (e.g., `tmux a -t 0` or `tmux a -t Bob`).
*   **[00:10:00] Killing a Specific Session**:
    *   To terminate a specific session: `tmux kill-session -t [index_or_name]` (e.g., `tmux kill-session -t Bob`).
*   **[00:23:40] Killing All Sessions**:
    *   To terminate all running `tmux` sessions: `tmux kill-server`.

#### Windows

*   **[00:11:40] Creating a New Window**:
    *   To create a new window within your current session: `Ctrl+b` then `c`.
*   **[00:12:30] Navigating Between Windows**:
    *   To move to the next window: `Ctrl+b` then `n`.
    *   To move to the previous window (not explicitly shown but common): `Ctrl+b` then `p`.
*   **[00:13:30] Renaming a Window**:
    *   To rename the current window: `Ctrl+b` then `,` (comma).
*   **[00:14:10] Listing and Selecting Windows/Sessions**:
    *   To view a list of all windows across all sessions and jump to them: `Ctrl+b` then `w`.
*   **[00:22:20] Killing a Window**:
    *   To close the current window: `Ctrl+b` then `&` (ampersand). Confirm with `y` or `yes`.

#### Panes

*   **[00:16:00] Splitting Panes (Horizontal and Vertical)**:
    *   To split the current pane horizontally (hot dog style): `Ctrl+b` then `%` (percent sign).
    *   To split the current pane vertically (hamburger style): `Ctrl+b` then `"` (double quote).
*   **[00:18:00] Navigating Between Panes**:
    *   To move to an adjacent pane: `Ctrl+b` then `[arrow key]` (up, down, left, or right).
    *   To jump to a pane by its index (displayed when entering command): `Ctrl+b` then `q`, then press the index number.
*   **[00:19:50] Resizing Panes**:
    *   To resize the active pane: `Ctrl+b` then `Ctrl+[arrow key]` (for smaller steps) or `Ctrl+b` then `Alt+[arrow key]` (for larger steps).
*   **[00:20:50] Pre-selected Pane Layouts**:
    *   To apply pre-defined pane layouts: `Ctrl+b` then `Alt+[1-5]` (e.g., `Alt+1` for vertical splits).
*   **[00:21:40] Killing a Pane**:
    *   To close the current pane: `Ctrl+b` then `x`. Confirm with `y` or `yes`.

### Advanced Feature: Copy Mode

*   **[00:24:50] Configuring `tmux` for Copy Mode**:
    *   Edit your `~/.tmux.conf` file (or create it if it doesn't exist) using a text editor like `nano`: `nano ~/.tmux.conf`.
    *   Add these lines to enable mouse support and Vim-style keys for copy mode:
        ```
        set -g mouse on
        set-window-option -g mode-keys vi
        ```
    *   Save and exit (`Ctrl+X`, `Y`, `Enter`). Then kill all `tmux` sessions (`tmux kill-server`) and restart for changes to take effect.
*   **[00:26:00] Mouse-based Copy Mode**:
    *   With `set -g mouse on`, you can simply select text with your mouse to copy it (it automatically enters and exits copy mode).
*   **[00:27:00] Keyboard-based Copy Mode**:
    *   **Enter Copy Mode**: `Ctrl+b` then `[` (opening bracket).
    *   **Start Selection**: Move your cursor to the desired starting point using arrow keys (or Vim keys HJKL) and press `space`.
    *   **Select Text**: Move your cursor to the end of the desired selection.
    *   **Copy to Buffer**: Press `enter`.
    *   **Paste from Buffer**: `Ctrl+b` then `]` (closing bracket).

### Conclusion

*   **[00:30:20] Final Thoughts**: `tmux` significantly boosts productivity by allowing users to manage multiple terminal environments, detach from long-running processes, and reattach as needed. While the initial learning curve for hotkeys might seem daunting, consistent practice quickly makes these commands second nature, transforming users into terminal "wizards." The ability to manage sessions, windows, and panes effectively is invaluable for anyone working extensively in the Linux command line, from programmers and hackers to system administrators.