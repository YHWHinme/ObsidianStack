
https://www.youtube.com/watch?v=4FkTNQwPZ58&t=46s

# Goal 1: Installing Fast Fetch (Timestamp: 00:00:41)

**Step 1: Executing the Installation Command**

For Arch Linux or Arch-based distributions, the speaker provides the following command:

```bash
sudo pacman -S fastfetch
```

This command uses the `pacman` package manager (specific to Arch Linux) to install the `fastfetch` package.  `sudo` ensures the command is run with administrator privileges.

**Step 2: Providing the System Password**

The command prompts for the user's password to confirm administrative authorization for the installation.

**Step 3: Confirming Installation**

The user is prompted to press 'y' to confirm the installation of the dependencies.

**Step 4: Verifying Installation**

After installation, run `fastfetch` in your terminal to check if the installation was successful.


# Goal 2: Setting Fast Fetch to Run Automatically on Terminal Launch (Timestamp: 00:01:23)

**Step 1: Accessing the Shell Configuration File**

Open your shell configuration file using a text editor. The speaker uses `vim`, a powerful command-line text editor:

```bash
vim ~/.bashrc
```

(Note:  The exact configuration file may vary depending on your shell; it could be `.zshrc` for Zsh, etc.)

**Step 2: Adding the Fast Fetch Command**

Add the following line to the end of your configuration file:

```bash
fastfetch
```

This command will execute `fastfetch` each time your terminal starts.

**Step 3: Saving the Configuration File**

In `vim`, press `Esc`, then type `:wq` and press Enter to save and quit the editor. This writes the changes to the configuration file.

**Step 4: Restarting the Terminal**

Restart your terminal for the changes to take effect.  This ensures the new configuration is loaded.


# Goal 3: Customizing Fast Fetch's Appearance (Timestamp: 00:01:55)

**Step 1: Locating or Generating the Configuration File**

If the configuration file doesn't exist, generate it using:

```bash
fastfetch --gen-config
```

Otherwise, locate the configuration file (typically located at `~/.config/fastfetch/config.jsonc`). The speaker uses `vim` to edit it:

```bash
vim ~/.config/fastfetch/config.jsonc
```

**Step 2: Editing the Configuration File**

The speaker recommends using a template (link provided in the video description).  The file uses `jsonc` format (JSON with comments).  The speaker uses the following steps in vim:

*   `: %d` (select all and delete)
*   Paste the content from the template.

**Step 3:  Modifying Configuration Options**

The `config.jsonc` file allows customization of various aspects, including:

*   **Logo:**  Specifies the image to display.
*   **Modules:**  Selects which system information to show (can be enabled/disabled by commenting out lines).
*   **Formatting:** Controls the visual presentation.

Make changes as desired within the file.

**Step 4: Saving Changes**

In `vim`, press `Esc`, then type `:wq` and press Enter to save and quit the editor.

**Step 5: Restarting the Terminal**

Restart your terminal to see the changes reflected in the `fastfetch` output.


# Goal 4: Changing the Fast Fetch Logo (Timestamp: 00:03:57)

**Step 1: Accessing the Configuration File**

Open the `~/.config/fastfetch/config.jsonc` file using a text editor (e.g., `vim`).

**Step 2: Modifying the Logo Path**

Locate the `logo` setting within the configuration file and change the path to your desired logo image.  For example:

```jsonc
"logo": "/path/to/your/logo.png"
```

**Step 3: Saving Changes**

In `vim`, press `Esc`, then type `:wq` and press Enter to save and quit the editor.

**Step 4: Restarting the Terminal**

Restart your terminal to see the new logo displayed by `fastfetch`.
