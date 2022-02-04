# Windows Booting Without GRUB Boot Menu even appearing
This can sometimes happen after a Windows update; the bootloader default has been set to Windows rather than `GRUB`.

To fix: set bootloader back to `GRUB`
1. Open `cmd` (Administrator)
2. `bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi`
