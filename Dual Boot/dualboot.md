# Dual Boot

## Custom Linux (Ubuntu) Install
Usually best to install Windows first and let it install fresh over the whole disk.

1. Continue wizard until "Installation type"
2. Select "Something else"
3. Create the following partitions
    1. Swap partition
        * Size: >= RAM (for hibernation)
        * Type: Primary (can be logical if "unstable" issue occurs)
        * Location: Beginning of space
        * Use as: swap area
    2. Root filesystem - used for kernel, boot files, system files, (most) installed programs, libraries, etc.
        * Size: >20GB, I recommend 50GB
        * Type: Logical
        * Location: Beginning of space
        * Use as: ext4 fs
        * Mount point: /
    3. Home directory - used for user files. (For dual boot systems I recommend having a common data partition so this becomes less needed)
        * Size: Up to you. Recommended >10GB
        * Type: Logical
        * Location: Beginning of space
        * Use as: ext4 fs
        * Mount point: /

## Windows Booting Without `GRUB` Boot Menu even appearing
This can sometimes happen after a Windows update; the bootloader default has been set to Windows rather than `GRUB`.

To fix: set bootloader back to `GRUB`
1. Open `cmd` (Administrator)
2. `bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi`
