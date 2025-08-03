https://www.youtube.com/watch?v=rW3JKs1_oVI&t=15s

# NixOS Multi-System Configuration: A Setup Guide (Video Summary)

This video demonstrates setting up a multi-system configuration using NixOS, a declarative Linux distribution. The creator aims to rebuild their configuration from scratch, focusing on clarity and efficiency.

## Setting the Stage [00:00:00]

* **Introduction to NixOS:** [00:00:00] The video introduces NixOS as a declarative Linux distribution, contrasting it with package managers like those in Ubuntu.  It emphasizes NixOS's ability to build the entire system from a configuration file and its use of generations to prevent system breakage.
* **Advantages of NixOS:** [00:00:30]  The creator highlights NixOS's advantages: complete control, ease of setting up new systems, and the ability to handle multiple package versions without dependency conflicts.

## Initial NixOS Installation [00:01:18]

* **Virtual Machine Setup:** [00:01:18] A standard installation of NixOS on a virtual machine is shown, with minimal modification during the installation process.  The creator opts for a standard installation and focuses on configuring the system afterward using the configuration file.

## Initial Configuration and SSH Access [00:02:05]

* **Enabling SSH:** [00:02:05]  The creator enables the SSH server by uncommenting `services.openssh.enable = true` in the system configuration.
* **Adding Nix Settings:** [00:02:15]  They add lines for experimental features (enabling `nix` command and flakes) and trusted users (root and the main user) to the configuration. This allows for easy configuration changes from their local machine.
* **SSH Key Setup:** [00:02:40]  An SSH key is copied to the virtual machine to avoid password prompts on subsequent connections.

## Setting up the NixOS Configuration [00:03:05]

* **Creating the Configuration:** [00:03:05] A new project folder is created, and a configuration template is downloaded (link provided in the video).  The creator mentions using `nix flake init -T <git-repo>#<template>` to initialize the configuration.
* **Flake.nix Explanation:** [00:03:45] The `flake.nix` file is explained, highlighting its inputs (home-manager, Nix packages URL – using unstable and stable branches). The importance of the `nixosConfiguratio%ns` section is emphasized, showcasing how configurations are structured per host.
* **Structuring the Configuration:** [00:04:30] The creator explains their preferred configuration structure for managing multiple systems, emphasizing the ability to share resources between machines.
* **Replacing Placeholders:** [00:04:55] Placeholders like "your-host" and "your-name" are replaced with the actual hostname and username.
* **Copying Configuration Files:** [00:05:20] The configuration files are copied from the virtual machine to the local machine using `scp`.

## Building and Deploying the Configuration [00:05:40]

* **Adding Packages:** [00:05:40]  `neovim` and `git` are added as system packages.
* **Pushing Configuration to VM:** [00:05:50] The command `nixos-rebuild switch --flake .#<hostname> --use-remote-sudo` is used to push the local configuration to the virtual machine.
* **Troubleshooting Errors:** [00:06:05]  Errors encountered during the rebuild process are addressed, highlighting the importance of checking for double definitions and ensuring the correct hostname is used.

## Final Configuration and Hyperland Setup [00:07:00]

* **Disabling Root Login and Enabling SFTP:** [00:07:00]  The creator modifies the openSSH service to disable root login and enable SFTP.
* **Enabling Hyperland:** [00:07:15]  Hyperland is enabled as a window manager.
* **Troubleshooting Hyperland Crash:** [00:07:35] A crash in Hyperland is resolved by setting the `WLR_RENDERER_ALLOW_SOFTWARE` environment variable in the Hyperland configuration.

## Conclusion [00:08:10]

The video concludes with a successful setup, demonstrating the ability to manage a NixOS configuration locally and deploy it to a remote machine.  The creator promises more detailed tutorials in future videos.
