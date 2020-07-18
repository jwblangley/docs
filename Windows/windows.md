# Windows

## Accessing the Command Line (Root Admin)
1. `shift` + restart or Windows boot USB
2. Troubleshoot
3. Advanced Options
4. Command Prompt

## Turn on/off `Administrator` Account
```cmd
net user Administrator /active:<yes|no>
```

## Changing and Enabling/Disabling Passwords
```cmd
net user <username> <new_password>
```
```cmd
net user <username> /passwordreq:<yes|no>
```

## Changing Passwords
```cmd
net user <username> <new_password>
```

## `diskpart`
Used for managing partitions, assigning volume letters, etc.
* `list <disk|volume|partition>`
* `select <disk|volume> <num>`
* `clean`: removes all partitions (and data!)
* `<assign|remove> letter=<letter>` (with volume selected)

## Recovering a Computer that Fails to Boot
```cmd
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```

Restart to check if fixed

Still no fix?

```cmd
C:
cd boot
attrib bcd -s -h -r
ren bcd bcd.old
bootrec /rebuildbcd
```

This can be reverted with `bcdedit /import C:\boot\bcd.old`

Restart to check if fixed

Still no fix?

```cmd
diskpart
diskpart> list disk
diskpart> select disk <num> # disk with os installed
diskpart> list volume
diskpart> select volume <num> # approx 260MB, FAT32 -> looking for EFI partition
diskpart> assign letter=b

cd /d b:\EFI\Microsoft\Boot\
bootrec /fixboot
ren BCD BCD.old
bcdboot C:\Windows /l en-gb /s b: /f ALL
```

Fingers crossed and reboot one last time :)
