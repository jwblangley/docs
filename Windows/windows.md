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
