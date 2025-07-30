# Waybar Configuration for Hyprland: A Comprehensive Guide

This video demonstrates how to configure Waybar, a status bar for Wayland compositors like Hyprland, showcasing both standard and custom modules.  The creator emphasizes customization using CSS and provides their configuration files on GitLab.

## Setting up Waybar with Hyprland [00:00:50]

*   The video begins by introducing Waybar and its popularity with Hyprland users.
*   The presenter highlights Waybar's compatibility and ease of use with Hyprland, specifically mentioning the included Hyprland modules.  [00:00:30]
*   The creator's GitLab repository, containing their Waybar configuration, is mentioned. [00:00:45]

## Waybar Modules and Configuration [00:01:10]

The video then showcases the presenter's Waybar setup, explaining each module:

*   **Left-side modules:**
    *   A custom "apps" button launching Rofi (application launcher). [00:01:20]
    *   The "tasks" module displaying running applications with workspace switching functionality. [00:01:30]
    *   The focused window title module. [00:01:40]
*   **Center module:**
    *   The workspace indicator with smooth transitions. [00:01:45]
*   **Right-side modules:**
    *   A custom module showing system updates. [00:01:50]
    *   The volume control module. [00:01:55]
    *   System information (disk, CPU, memory) module with custom styling. [00:02:00]
    *   A custom logout module. [00:02:05]
    *   Network information module. [00:02:10]
    *   The clock module. [00:02:10]
*   **Laptop-specific modules (shown later):** Bluetooth and battery status. [00:02:20]

The dynamic color scheme matching the wallpaper is also highlighted. [00:02:15]

## Installation and Configuration Files [00:02:30]

The video details the installation process on Arch Linux using `sudo pacman -S waybar` and adding Waybar to the Hyprland config. A script for managing multiple Waybar instances and reloading the configuration is also explained. [00:02:35]  A keybinding (Super+Shift+B) is shown for reloading Waybar after configuration changes. [00:02:55]

The core configuration files are located in a `.config/waybar` directory:

*   `config`: General settings (position, etc.). [00:03:05]
*   `modules.json`: Module configurations. [00:03:15]
*   `style.css`: Styling definitions using CSS. [00:03:25]

The video emphasizes the modular and structured approach to configuration.  Module grouping is demonstrated. [00:03:20]

## Custom Modules and Styling [00:03:40]

The video delves into creating custom modules:

*   Simple custom modules:  A Brave browser launcher, a Rofi application launcher, and a logout module. [00:03:45]
*   Advanced custom module: An update checker with thresholds (green, yellow, red) and JSON output.  This module's script is explained in detail, including threshold settings and JSON formatting. [00:04:10]  The use of Font Awesome icons is shown. [00:04:00]
*   CSS styling: The video demonstrates how CSS is used to style the modules, including dynamic color adjustments based on the wallpaper.  The use of a `piwall` template for generating color schemes is highlighted. [00:05:00]

## Conclusion [00:05:25]

The video concludes by encouraging viewers to try Waybar and use the provided configuration files.  The emphasis is on the flexibility and customization options offered by Waybar, especially its CSS styling capabilities which are attractive to web developers.
