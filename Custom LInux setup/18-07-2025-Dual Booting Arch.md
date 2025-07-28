This video provides a comprehensive, step-by-step guide on how to safely dual-boot Arch Linux with Windows 11, minimizing the risk of data loss. It also includes instructions on how to safely remove Arch Linux from a dual-boot setup. The tutorial emphasizes caution due to the non-straightforward nature of Arch Linux installation and details every step from preparing disk space to configuring the bootloader and desktop environment.

---

### Video Summary: Dual-Booting Arch Linux with Windows 11

**[00:00:00] Introduction & Requirements**
The video introduces an updated and safe method for dual-booting Arch Linux with Windows 11, ensuring no data loss. It also covers the process of safely removing Arch Linux.
*   **Requirements:**
    *   Windows 11 installed on PC/laptop.
    *   8GB or higher USB drive for bootable media.
    *   At least **40GB of free space** reserved from an existing Windows drive.

**[00:01:15] Preparing Windows for Dual Boot**
*   Open Disk Management (`diskmgmt.msc`).
*   Identify your main Windows partition (e.g., C: drive).
*   Right-click the partition and select **"Shrink Volume."**
*   Allocate a minimum of **40GB** (40,000 MB) or more for Arch Linux. This creates unallocated free space.

**[00:02:10] Creating Arch Linux Bootable Media & System Restore Point**
*   Download the Arch Linux ISO from the official website.
*   Use a tool like **Rufus** or Ventoy to burn the ISO to your USB drive, creating a bootable disk.
*   **Highly Recommended:** Create a Windows System Restore Point before proceeding with Arch Linux installation to allow system recovery if issues arise.

**[00:03:05] BIOS/UEFI Configuration**
*   Reboot your computer and enter BIOS/UEFI settings (common keys: F2, F9, Esc).
*   **Enable USB Boot** and set the USB drive as the primary boot device.
*   **Disable Secure Boot** (critical for Arch Linux).
*   If available, enable "Microsoft's third-party UEFI."
*   Clear any existing boot keys or certificates after disabling Secure Boot.
*   Save changes and exit. The system should boot into Arch Linux from the USB.

**[00:04:10] Booting into Arch Linux Live Environment & Initial Setup**
*   Once booted, you'll be in a terminal environment (mouse disabled).
*   Increase console size for better readability.
*   **Check Internet Connection:**
    *   **Ethernet:** Use `ping google.com` to verify.
    *   **Wi-Fi:**
        *   Type `iwctl` to enter iwd shell mode.
        *   `device list` to find your Wi-Fi interface (e.g., `wlan0`).
        *   `station wlan0 get-networks` to list available networks.
        *   `station wlan0 connect <SSID>` and enter password.
        *   `exit` from iwd shell.
        *   Verify with `ping google.com`.

**[00:06:25] Partitioning for Arch Linux**
*   Synchronize package databases and install `archinstall` (though manual partitioning is shown).
*   Identify your main drive using `lsblk` (e.g., `nvme0n1` or `sda`).
*   Use `cfdisk /dev/<your_disk_identifier>` to partition the unallocated space.
*   **Create three main partitions:**
    *   **EFI Partition:** 800MB (Type: EFI System). *Note: This is a new EFI partition for Arch, separate from Windows' EFI.*
    *   **Root Partition:** 20GB or higher (Type: Linux filesystem).
    *   **Swap Partition:** Remaining free space (Type: Linux swap).
*   **Write** the changes and **Quit** `cfdisk`.

**[00:08:40] Formatting and Mounting Partitions**
*   Identify your newly created partitions using `lsblk` (e.g., `nvme0n1p5` for EFI, `nvme0n1p6` for root, `nvme0n1p7` for swap).
*   **Format partitions:**
    *   Arch EFI: `mkfs.fat -F 32 /dev/nvme0n1p5`
    *   Root: `mkfs.ext4 /dev/nvme0n1p6`
    *   Swap: `mkswap /dev/nvme0n1p7`
*   **Mount partitions:**
    *   Root: `mount /dev/nvme0n1p6 /mnt`
    *   Create boot directory: `mkdir /mnt/boot`
    *   Arch EFI: `mount /dev/nvme0n1p5 /mnt/boot`
    *   Enable Swap: `swapon /dev/nvme0n1p7`
*   Verify mounting with `lsblk`.

**[00:10:00] Installing Base Arch Linux System**
*   Install the base system and essential packages:
    `pacstrap /mnt base base-devel linux linux-firmware amd-ucode` (for AMD) or `intel-ucode` (for Intel) `sudo nano git vim neofetch networkmanager bluetooth`
*   Accept defaults and wait for the installation to complete.

**[00:11:30] Initial Arch Linux Configuration (Chroot)**
*   Generate `fstab`: `genfstab -U /mnt >> /mnt/etc/fstab`
*   Enter the installed Arch Linux environment: `arch-chroot /mnt`
*   Set **root password**: `passwd`

**[00:12:30] Setting up Users and Sudo**
*   Create a standard user: `useradd -m -g users -G wheel,storage,power -s /bin/bash <your_username>`
*   Set password for the new user: `passwd <your_username>`
*   **Enable sudo privileges:**
    *   Edit `sudoers` file: `EDITOR=nano visudo`
    *   Uncomment the line: `%wheel ALL=(ALL:ALL) ALL`
    *   Save (`Ctrl+O`) and exit (`Ctrl+X`).
*   Verify sudo access by switching to the new user (`su - <username>`) and running a sudo command.

**[00:14:20] System Localization and Hostname**
*   **Set Time Zone:**
    *   List time zones: `timedatectl list-timezones`
    *   Set zone: `ln -sf /usr/share/zoneinfo/Asia/Kolkata /etc/localtime` (replace with your zone)
    *   Sync time: `timedatectl set-ntp true`
*   **Set System Language:**
    *   Edit `locale.gen`: `nano /etc/locale.gen`
    *   Uncomment `en_US.UTF-8 UTF-8` (or your preferred locale).
    *   Generate locales: `locale-gen`
    *   Create `locale.conf`: `echo "LANG=en_US.UTF-8" > /etc/locale.conf`
*   **Set Hostname:**
    *   Set hostname: `echo "ArchLinux" > /etc/hostname` (replace "ArchLinux" with your desired name)
    *   Edit `hosts` file: `nano /etc/hosts` and add entries for `127.0.0.1` and `::1` with your hostname.

**[00:16:30] Installing and Configuring GRUB Bootloader**
*   Install GRUB and `efibootmgr`: `pacman -S grub efibootmgr`
*   Install GRUB to the Arch EFI partition: `grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=ArchLinux --recheck`
*   Generate GRUB configuration file: `grub-mkconfig -o /boot/grub/grub.cfg`
*   **Enable Services:**
    *   Bluetooth: `systemctl enable bluetooth.service`
    *   Network Manager: `systemctl enable NetworkManager.service`
*   Exit chroot: `exit`
*   Unmount partitions: `umount -R /mnt`
*   Shutdown: `poweroff` and eject USB.

**[00:18:20] Post-Installation: Setting up Desktop Environment**
*   Boot into Arch Linux.
*   Log in with your new user account.
*   **Connect to Wi-Fi (if needed):**
    *   `nmcli dev status`
    *   `nmcli radio wifi on`
    *   `nmcli dev wifi list`
    *   `nmcli dev wifi connect <SSID> password "<PASSWORD>"`
*   Update Pacman database: `sudo pacman -Syyu`
*   **Install KDE Plasma Desktop (example):**
    *   `sudo pacman -S xorg sddm plasma-meta` (or `plasma` for a minimal install)
    *   Install recommended fonts.
*   Enable display manager: `sudo systemctl enable sddm.service`
*   Reboot: `reboot` (Arch Linux should now boot with KDE Plasma).

**[00:21:00] Adding Windows Boot Entry to GRUB**
*   **Fix Discover App Backend:** `sudo pacman -S flatpak`
*   (Optional) Install NVIDIA drivers: `sudo pacman -S nvidia` (reboot after install).
*   Install `os-prober`: `sudo pacman -S os-prober`
*   Edit GRUB configuration: `sudo nano /etc/default/grub`
    *   Change `GRUB_TIMEOUT` to `20`.
    *   Uncomment (or add) `GRUB_DISABLE_OS_PROBER=false`.
*   Save (`Ctrl+O`) and exit (`Ctrl+X`).
*   Update GRUB: `sudo grub-mkconfig -o /boot/grub/grub.cfg` (you should see it find Windows Boot Manager).
*   Reboot: `reboot` (GRUB menu should now show both Arch Linux and Windows 11).

**[00:23:45] Removing Arch Linux (Bonus Section)**
*   Reboot into **Windows 11**.
*   Open Disk Management (`diskmgmt.msc`).
*   Delete the Arch Linux Root and Swap partitions.
*   **To delete the Arch EFI partition (which Disk Management cannot):**
    *   Open **Command Prompt as Administrator**.
    *   Type `diskpart`
    *   `list disk` (Identify your main drive, usually `Disk 0`).
    *   `select disk 0` (Replace `0` with your disk number).
    *   `list partition` (Identify the Arch EFI partition, typically around 800MB and not labeled).
    *   `select partition <partition_number>` (Replace `<partition_number>` with the Arch EFI partition's number).
    *   `delete partition override`
*   The Arch Linux partitions are now unallocated. You can extend your Windows partition to reclaim this space.
*   Reboot your computer. It should now boot directly into Windows 11 without issues.

---

**[00:27:00] Conclusion**
This detailed guide enables users to safely set up and manage a dual-boot system with Arch Linux and Windows 11, including a crucial section on how to cleanly remove Arch Linux if no longer needed. The video emphasizes following each step carefully to avoid data loss and ensure a smooth experience.