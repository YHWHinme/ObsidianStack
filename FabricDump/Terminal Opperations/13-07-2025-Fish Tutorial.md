# Goal 1: Installing the Fish Shell on Arch Linux (Timestamp: 00:01:37)

**Step 1: Opening the Terminal**

The video starts by opening a terminal window, presumably using the default Bash shell.

**Step 2: Installing Necessary Packages using Pacman**

The speaker uses the Arch Linux package manager, `pacman`, to install the required packages.  The command used is:

```bash
sudo pacman -S fish pkgfile ttf-dejavu powerline-fonts inetutils
```

This command installs:
* `fish`: The Fish shell itself.
* `pkgfile`: A package to handle command-not-found errors, automatically searching repositories for missing commands.
* `ttf-dejavu`:  A font.
* `powerline-fonts`: Fonts for enhanced terminal appearance.
* `inetutils`:  Contains the `hostname` command, necessary for some Fish themes.

**Step 3:  Entering the sudo password and confirming installation.**

After entering the sudo password, the installation proceeds automatically.


# Goal 2: Setting Fish as the Interactive Shell (Timestamp: 00:03:06)

**Step 1: Editing the Bash RC file**

The speaker edits the Bash configuration file (`~/.bashrc`) using `vim`:

```bash
vim ~/.bashrc
```

**Step 2: Adding the exec command**

At the end of the `.bashrc` file, the following line is added:

```bash
exec fish
```
This command ensures that Fish is launched whenever a new terminal is opened.

**Step 3: Saving and Exiting the editor**

The changes to the `.bashrc` file are saved and the editor is exited.  The speaker mentions the alternative of sourcing the file (`source ~/.bashrc`) instead of closing and reopening the terminal.

**Step 4: Reopening the terminal (or sourcing the file)**

Reopening the terminal (or sourcing the `.bashrc` file) loads the changes, and the terminal now launches with the Fish shell.


# Goal 3: Configuring the Fish Shell using `fish_config` (Timestamp: 00:06:56)

**Step 1: Launching the Configuration Tool**

The built-in Fish configuration tool is launched using the command:

```bash
fish_config
```

This opens a web browser with a graphical interface for customizing the shell's appearance and behavior.

**Step 2: Customizing Colors and Theme**

The user interface allows for customization of various aspects, including:
* **Colors:**  The video demonstrates changing the colors of commands, quotes, comments, and other elements.
* **Theme:**  The user selects the "Tomorrow Night" theme.

**Step 3: Customizing Prompt**

The user interface offers a selection of pre-defined prompts. The video chooses the "Terlar" prompt.

**Step 4: Exploring Functions, Variables, Bindings, and Abbreviations**

The configuration tool also allows exploring and modifying existing functions, aliases, variables, key bindings, and abbreviations.

**Step 5: Saving Configuration Changes**

The changes are saved through the web interface.  The video then demonstrates the updated appearance of the prompt and colors.


# Goal 4: Creating and Removing a Custom Fish Alias (Timestamp: 00:09:57)

**Step 1: Creating an Alias**

An alias named `cfh` (change to fish home directory) is created using the following command:

```bash
alias -s cfh "cd /home/hermano/.config/fish"
```

This creates a shortcut to navigate to the user's Fish configuration directory.

**Step 2: Closing and Reopening the Terminal**

The terminal is closed and reopened for the alias to take effect.

**Step 3: Verifying the Alias**

The `cfh` alias is tested to ensure it works correctly.

**Step 4: Removing the Alias**

The alias is removed by navigating to the `functions` directory within the Fish configuration directory and deleting the corresponding file:

```bash
cd ~/.config/fish/functions
rm cfh.fish
```

The terminal is then closed and reopened to reflect the removal of the alias.


# Goal 5: Generating Autocompletions for Man Pages (Timestamp: 00:12:14)

**Step 1: Updating Completions**

The command to update the Fish shell's autocompletion database, including man pages, is executed:

```bash
fish_update_completions
```

This command takes a short time to run.  After completion, the Fish shell now provides autocompletion suggestions for man page commands.


The video concludes by summarizing the basic Fish installation and hinting at future tutorials covering more advanced customization with the Oh My Fish framework.
