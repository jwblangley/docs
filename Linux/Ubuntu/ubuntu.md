# Ubuntu

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
