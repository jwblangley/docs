# Remote File Access

## `sftp`
* Good for simple single file transfers
* `-a` flag is really useful to continue transfer if it gets interrupted

## `sshfs`
* Mounts the remote file system
* Method:
    ```bash
    mkdir <local_mount_point> # (usually /tmp/remote is a good choice)
    sshfs <user>@<remote>:<remote_mount_point> <local_mount_point>
    # ... When finished, don't forget to
    umount <local_mount_point>
    ```
