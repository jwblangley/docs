# Linux

## Remote file access
### `sftp`
* Good for simple single file transfers
* `-a` flag is really useful to continue transfer if it gets interrupted

### `sshfs`
* Mounts the remote file system
* Method:
    ```bash
    mkdir <local_mount_point> # (usually /tmp/remote is a good choice)
    sshfs <user>@<remote>:<remote_mount_point> <local_mount_point>
    # ... When finished, don't forget to
    umount <local_mount_point>
    ```

## Mounting Drives/Partitions
* Use `gparted` or `gnome-disks` to find (with GUI) *partition name*. Or use `fdisk -l` to do this via command line (harder to understand). N.B: *devices* look like `/dev/sdx` and partitions look like `/dev/sdxY`. e.g. `/dev/sda` and `/dev/sda1` respectively.
```bash
mount <parition_name> <mount_point>
# ... When finished, don't forget to
umount <mount_point>
```

## RAMDISK
```bash
mount -t tmpfs -o rw,size=<size> <name> <mount_point>
# ... When finished, don't forget to
umount <local_mount_point>
```

## Terminal multiplexer
Use [tmux](https://github.com/tmux/tmux/wiki) and [my tmux config](https://github.com/jwblangley/tmux-config)

### Starting Services in Detached Sessions
```bash
tmux new -d [-s <session_name>] <starting_command>
```

## `ssh`
### Graphical applications over `ssh`
* Pass the `-X` or `-Y` flag
### `ssh` as a VPN
`ssh` can actually be used to tunnel network traffic also!
```bash
ssh -N -L <local_port>:<remote>:<remote_port> <user>@<remote>
```

e.g.
```bash
ssh -N -L 12345:example.com:443 james@abc.com
```

Will set up a tunnel such that `example.com:443` (443 is `https`) can be accessed at `localhost:12345` tunnelling traffic through `james@abc.com`

## Command Line Task Manager
[`htop`](https://github.com/hishamhm/htop)

## Use of the (Desktop) Clipboard in the Command Line
[`xclip`](https://github.com/astrand/xclip)
* `-i`: copy from `stdin`
* `-o`: paste to `stdout`
* Very useful when combined with pipes
* Also required to use clipboard in `micro`
