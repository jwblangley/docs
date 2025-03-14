# Custom Linux (Ubuntu) Install - Method for Setting Up Dual Boot

Before proceeding make note of the disk partitioning scheme on the boot drive (MBR or GPT).
This, in turn will denote the boot mechanism (BIOS/Legacy or EFI).
When creating the boot media AND when actually booting to that USB device, ensure that the correct boot mechanism (BIOS/Legacy or EFI) is being used.
If a warning comes up on the last stage of the install, you probably have not matched the boot mechanism with the existing boot mechanism and will get a failed install.

Usually best to install Windows first over the whole disk for a dual boot setup.

1. Continue wizard until "Installation type"
2. Select "Something else"
3. (For dual boot) Shrink Windows partition to make free space. Recovery partition can be left untouched.
4. Create the following partitions
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
        * Mount point: /home
