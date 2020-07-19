# Ubuntu

## Prevent/Allow Ubuntu Sleeping
e.g. For an Ubuntu Server
```bash
sudo systemctl <mask|unmask> sleep.target suspend.target hibernate.target hybrid-sleep.target
```

## Managing installed programs
1. Find manually installed programs to find those you no longer need
    ```bash
    sudo apt-mark showmanual
    snap list # for any programs installed by snap
    ```
2. Clean list of `ppa`s after uninstalling
    * `ppa`s are listed in the `sources.list` file *and* as individual files in the `sources.list.d/` subfolder in `etc/apt`

## Updating Ubuntu
#### GUI (recommended)
Sotware Updater

#### Terminal
```bash
apt update
apt upgrade
do-release-upgrade # -c to check for upgrades
```

---

### After the updates
* Some `ppa`s and software might have been removed
#### GUI (recommended)
Can be launched with `software-properties-gtk` (e.g. with ssh -X or -Y)
* Remove anything from "other software" and "authentication" that has been disabled by the upgrade and **make a note of which**

#### Terminal
* [Manipulate `sources.list`](#managing-installed-programs) to remove any software that was disabled by the upgrade and **make a note of which**

---
* `apt update` should now run without any errors or warnings
* Reinstall those that were removed

## To Turn On/Off Mounts From Appearing in the Dock
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts <true|false>
```

## Managing Versions of Programs on the Path
This is particularly relevant for Java (especially when wanting to work with Oracle Java), so these instructions will be tailored to that.

1. Install version files (for java to `/usr/lib/jvm/jdkx.x.x_xxx`)
2. Register with `update-alternatives`
    ```bash
    sudo update-alternatives --install "usr/bin/java" "java" "usr/lib/jvm/jdkx.x.x_xxx/bin/java" 1
    ```
    Installation to, command name, program file, priority for auto-selection (not relevant as we will use manual selection)
3. Select which version to use
    ```bash
    sudo update-alternatives --config java
    ```
    Then type the chosen installation number

N.B for java, it is best to do this process for `java` and `javac`
