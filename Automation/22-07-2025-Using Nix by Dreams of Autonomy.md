
https://www.youtube.com/watch?v=Z8BL8mdzWHI&t=235s


# Setting up and Using the Nyx Package Manager on macOS

This video demonstrates how to use the Nyx package manager, specifically the Nyx Darwin module, to manage applications and system settings on macOS.  It highlights Nyx's declarative approach, offering a more powerful alternative to Homebrew.

## Getting Started with Nyx Darwin [00:01:18]

*   **Installation:** The video begins by showcasing the installation process of Nyx on a fresh macOS installation using a single command from the Nyx OS website's download page.  [00:01:50]  The installer is described as "rather involved," creating a separate Apple volume and user accounts. [00:02:20]
*   **Verification:** After installation, the presenter verifies Nyx's functionality by running `nyx shell neofetch`, which downloads and executes neofetch without system-wide installation. [00:02:45] This demonstrates Nyx's temporary environment feature for one-off commands.

## Configuring Nyx with Nyx Flakes [00:03:28]

*   **Creating the Configuration Directory:** A new directory (`~/nyx`) is created to store the Nyx configuration. [00:03:38]  The presenter notes that the Nyx documentation suggests using `/config/nx`. [00:03:55]
*   **`flake.nix` File:** The video proceeds to create and explain the `flake.nix` file, which utilizes the Nyx flakes approach for improved composability and reproducibility. [00:04:15]  The presenter explains the `inputs`, `outputs`, and the use of a functional language within the configuration. [00:05:00]  Key elements like defining system packages, enabling the Nyx daemon, and utilizing experimental feature flags are discussed. [00:06:15]
*   **Modifying `flake.nix`:**  The presenter changes the flake description and sets the system architecture to `aarch64` for Apple Silicon. [00:07:50] The configuration name is changed from `simple` to `mini`. [00:08:00]

## Installing Packages [00:08:50]

*   **Declarative Installation:** The video emphasizes Nyx's declarative nature, recommending against using the `nyx m` command for individual package installations. Instead, packages are added to the `environment.systemPackages` list within `flake.nix`. [00:09:35]
*   **`Darwin rebuild` Command:**  The `darwin rebuild` command is used to apply changes to the configuration and install/update packages. [00:09:58] Neovim is installed as an example. [00:10:00]
*   **Package Discovery:** The `nyx search` command is demonstrated to find packages within the Nyx repository. [00:10:35]


## Installing GUI Applications [00:10:50]

*   **Installing from Nyx Repository:** Alacrity (terminal emulator) is installed as an example from the Nyx repository. [00:10:55]  The video addresses the issue of Spotlight not indexing symlinks created by Nyx, offering a solution using aliases. [00:11:30]
*   **Font Installation:** The JetBrains Mono Nerd Font is installed using Nyx, highlighting the declarative approach for font management. [00:11:50]
*   **Spotlight Indexing:**  A code snippet (link provided in the description) is used to configure Nyx to generate macOS aliases for better Spotlight integration. [00:12:30]
*   **Non-Free Applications:** The video explains how to install non-open-source applications (like Obsidian) by adding a configuration value to allow unfree licenses. [00:12:55]


## Integrating with Homebrew [00:13:20]

*   **Homebrew Module:** The Nyx Homebrew module is added to the `flake.nix` to manage Homebrew packages declaratively. [00:13:30]  Instructions are provided for both new and existing Homebrew installations. [00:14:00]
*   **Installing Casks:** Hammerspoon, Firefox, and The Unarchiver are installed via Homebrew using casks. [00:14:30]
*   **Managing Homebrew Packages:**  The `activation.cleanup` option is set to `zap` to ensure only packages specified in the Nyx configuration are installed. [00:14:55]
*   **Mac App Store Applications:** Yoink is installed as an example of installing a Mac App Store application using the `mas` option and its app ID. [00:15:15] The video explains how to obtain the app ID using either the share link or the `mas` CLI tool (installed via Homebrew). [00:16:00]


## Updating Packages [00:17:00]

*   **Updating Nyx Flakes:**  The `nyx flake update` command updates the Nyx flakes, followed by `darwin rebuild` to update installed packages. [00:17:00]
*   **Homebrew Updates:**  The video suggests updating Homebrew packages during system upgrades using `darwin rebuild`, enabling `autoUpdate` and `autoUpgrade` options in the configuration. [00:17:30]

## Configuring System Settings [00:17:50]

*   **Declarative System Configuration:**  The video demonstrates configuring macOS settings declaratively within the Nyx configuration.  Auto-hiding the dock is used as an example. [00:17:50]
*   **Additional Settings:** The presenter shows how to configure other settings, such as specifying persistent dock apps, setting the finder view to column view, disabling the guest account, using 24-hour time, and setting the color and key repeat settings. [00:18:30]  The Nyx Darwin documentation is recommended for exploring additional options. [00:19:00]

## Conclusion [00:19:30]

The video concludes by mentioning future content on managing dotfiles using the Home Manager module and recommending Fim Joy's YouTube channel for further learning on Nyx and NixOS.
