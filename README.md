# Matrix GRUB Theme (Red Pill vs Blue Pill)

A full-screen, high-resolution GRUB theme inspired by The Matrix. It uses the "Giant Icon" trick to display different 1920x1080 images for Linux (Red Pill) and Windows (Blue Pill).

---

![Matrix Morpheus GRUB Theme preview showing Arch and Windows boot icons](preview.gif)

## ⚠️ Requirements & Warnings

* **Resolution:** Designed for **1920x1080**. If your monitor is different, you must edit `theme.txt` and `installer.sh` before running.
* **Operating Systems:** Designed for **Linux (Arch/EndeavourOS)** and **Windows** dual-boot.
* **Critical:** This theme requires editing the `/etc/grub.d/40_custom` file with your correct partition **UUIDs**. Failure to do so will result in an unbootable system.

## Installation Steps

1.  **Clone the Repository** and enter the directory.
    ```bash
    git clone [YOUR-REPO-URL]
    cd [YOUR-REPO-NAME]
    ```

2.  **Find Your UUIDs:**
    Use `lsblk -f` or `sudo blkid` to find the UUIDs for:
    * Your Linux root partition (e.g., `ext4` type).
    * Your Windows EFI partition (e.g., `vfat` type).

3.  **Edit `40_custom`:**
    Open the file and replace the placeholders: `YOUR_LINUX_UUID` and `YOUR_WINDOWS_EFI_UUID` with your actual UUIDs.

4.  **Run the Installer:**
    ```bash
    sudo ./installer.sh
    ```
    This script will:
    * Create the theme directory (`/boot/grub/themes/Matrix`).
    * Generate the necessary `font.pf2`.
    * Copy the theme files and your customized `40_custom`.
    * Update `/etc/default/grub`.
    * Generate a new `grub.cfg`.

5.  **Reboot** and enjoy the theme! The black screen delay when booting Linux has been removed by excluding `quiet splash` from the boot parameters.
