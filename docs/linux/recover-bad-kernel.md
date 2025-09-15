# Recovering from a bad kernel installation

Every now and then you may come across a bad kernel installation.
The symptoms for this are usually hardware issues: graphics, keyboard/mouse/touchpad and network and the most common.

To fix this, use GRUB to see "Additional options" and select a version with a previous kernel.

This should launch with everything working.

The most likely fix here is to `apt update` and `apt upgrade` as the bug will probably be fixed.
In rare cases where this is not the case,
uninstalling the old linux kernel will prevent needing to use additional options every time,
but this will only last until you next have an update
(which hopefully fixes it anyway!).

## Useful commands

To check current linux kernel version

```bash
uname -r
```

To see installed kernels

```bash
dpkg --list | grep linux-image
```
