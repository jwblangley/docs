# Mounting Drives/Partitions
* Use `gparted` or `gnome-disks` to find (with GUI) *partition name*. Or use `fdisk -l` to do this via command line (harder to understand). N.B: *devices* look like `/dev/sdx` and partitions look like `/dev/sdxY`. e.g. `/dev/sda` and `/dev/sda1` respectively.
```bash
mount <parition_name> <mount_point>
# ... When finished, don't forget to
umount <mount_point>
```
