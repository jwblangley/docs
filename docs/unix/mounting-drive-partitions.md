# Mounting Drives/Partitions

* Use `gparted` or `gnome-disks` to find (with GUI) *partition name*. Or use `fdisk -l` to do this via command line (harder to understand). N.B: *devices* look like `/dev/sdx` and partitions look like `/dev/sdxY`. e.g. `/dev/sda` and `/dev/sda1` respectively.

  ```bash
  mount <parition_name> <mount_point>
  # ... When finished, don't forget to
  umount <mount_point>
  ```

* To mount part of a hard drive into the local directory (e.g. so that docker can use it without symlinks), add the following to `/etc/fstab`

  ```
  # Bind /hdd/server to /home/server/hdd
  /hdd/server /home/server/hdd none defaults,bind 0 0
  ```

  Similar to this is what is happening automatically when using [`gnome-disks`](./ubuntu/automatic-mount-on-boot.md)
