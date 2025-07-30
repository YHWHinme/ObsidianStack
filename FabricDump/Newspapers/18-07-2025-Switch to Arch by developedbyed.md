This video details the process and motivation behind switching a main Windows PC to **Arch Linux** with **Hyprland** for an optimized developer environment. The creator highlights the frustrations with Windows Subsystem for Linux (WSL) and Windows' native limitations, aiming for a more efficient and customizable setup.

---

### Introduction & Motivation
*   **[00:00:00] New Year, New Channel Focus:** The creator announces a shift in content for 2025, focusing more on Neovim and algorithms.
*   **[00:00:15] Dissatisfaction with Windows/WSL:** The primary reason for the switch is the poor experience coding on Windows using WSL.
    *   **Issues highlighted:** Slow performance, high CPU/RAM usage, poor window management, and encountering "weird edge cases" where code would work natively on Ubuntu but fail in WSL.
*   **[00:00:58] Transitioning Software:** The creator has moved away from Adobe tools to DaVinci Resolve for video editing and Affinity for photo editing, removing the main dependency on Windows.
*   **[00:01:18] The Big Switch:** Decision to convert the main PC (RTX 3070 Ti, AMD CPU) from Windows to Arch Linux with Hyprland.

### Pre-Installation Preparations
*   **[00:01:35] Ubuntu Live Wallpaper Alternative:** For those who like Windows' Wallpaper Engine, the creator briefly shows **Hidimari** on Ubuntu as a tool to display MP4 videos as live wallpapers.
    *   Installation: `flatpak install flathub io.github.jeffg.hidamari`
    *   Usage: Drag and drop MP4 or use a streaming URL.
*   **[00:02:49] Creating the Arch Linux USB Stick:**
    *   **Requirements:** A 32GB+ USB stick.
    *   **Steps:**
        1.  Download the latest Arch Linux ISO from the official website (e.g., `archlinux-2025.01.01-x86_64.iso`).
        2.  Use **Rufus** (on Windows) to flash the ISO onto the USB stick.
        *   *Caution:* This will wipe all data on the USB.
*   **[00:03:57] Windows Partitioning Challenges (BitLocker):** The creator faced issues shrinking the Windows C drive due to **BitLocker encryption**.
    *   **Solution:** Disable BitLocker and decrypt files to free up space for a new partition.

### Arch Linux Installation Process
*   **[00:04:47] BIOS Configuration:**
    *   Plug in the USB stick.
    *   Restart the computer and enter BIOS (typically F12 or F2).
    *   Enable **USB Boot**.
    *   Disable **Secure Boot**.
    *   Boot from the USB stick (UEFI option).
*   **[00:05:40] SSH for Easier Installation:** To facilitate recording and viewing, the creator SSHed into the Arch Linux installer from a MacBook.
    *   Requires the installation machine to be connected to the network (Ethernet or Wi-Fi).
    *   Command: `ssh root@archiso` (or similar, depending on network setup).
*   **[00:06:20] Running `archinstall`:** The `archinstall` script simplifies the process.
    *   **[00:06:30] Language & Keymaps:** Kept as English and default.
    *   **[00:06:40] Mirrors:** Changed to a closer region (e.g., United Kingdom) for faster package downloads.
    *   **[00:07:05] Disk Configuration:**
        *   Chosen: **Manual Partitioning**.
        *   Selected the pre-allocated 250GB SSD partition (ext4 filesystem).
        *   Marked to be *wiped* and assigned as the **root (`/`) mount point**.
    *   **[00:08:00] User Setup:** Set a root password and added a new user with *sudo* privileges.
    *   **[00:08:30] Profile (Desktop Environment):** Initially selected *Gnome*, but later realized the mistake and switched to *Hyprland* manually.
    *   **[00:08:50] Graphics Drivers:** Selected *Nvidia* with the *open kernel module*.
    *   **[00:09:20] Audio:** Chosen *Pipewire*.
    *   **[00:09:25] Kernel:** Selected *Linux* (with an optional LTS kernel for redundancy).
    *   **[00:09:40] Begin Installation.**

### Troubleshooting the Installation
*   **[00:09:55] Installation Failure (Grub Issue):** The initial installation failed, getting stuck in Grub because the boot loader wasn't pointing to the correct kernel.
*   **[00:10:20] Solution:** The creator realized a crucial step was missed: manually mounting a **500MB UEFI partition**. After correcting this and re-installing, the boot process worked.

### The New Arch Linux + Hyprland Setup
*   **[00:10:45] Post-Installation Adjustments:** The creator manually switched from Gnome to **Hyprland** after the initial installation error.
*   **[00:11:00] Renewed Excitement for Linux:** The journey, sparked by an interest in Neovim and Lua, led to a deep appreciation for Linux and tiling window managers.
*   **[00:11:40] Hyprland Workflow Demo:**
    *   Demonstrates **tiling window management** (windows automatically arrange).
    *   Shows quick app launching (e.g., Super+E for Chrome) and seamless window switching/closing.
    *   Praises Hyprland's efficiency over Windows and Mac's window systems.
*   **[00:12:25] Customization & Future Plans:** Shows different themes (e.g., Tokyo Nights, Rose Pine) and notes that further configuration, like scaling adjustments and Neovim setup, is still needed.

---

### Conclusion
*   **[00:12:50] Main Message:** The video concludes with the creator's excitement for the new Arch Linux + Hyprland setup, emphasizing the improved workflow and the journey of learning and customization. The transition has significantly boosted his enthusiasm for development and content creation.