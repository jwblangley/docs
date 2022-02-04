# Managing Installed Programs

1. Find manually installed programs to find those you no longer need
    ```bash
    sudo apt-mark showmanual
    snap list # for any programs installed by snap
    ```
1. Clean list of `ppa`s after uninstalling
    * `ppa`s are listed in the `sources.list` file *and* as individual files in the `sources.list.d/` subfolder in `etc/apt`
