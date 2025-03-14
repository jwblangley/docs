# Updating Ubuntu

## Do a fresh install!

If your ~/home is on a separate partition, that does not need to be reformated and can be kept!

Although why not take the opportunity to start fresh!

## GUI (recommended)

Sotware Updater

## Terminal
```bash
sudo apt update
sudo apt upgrade
sudo do-release-upgrade # -c to check for upgrades
```

---

### After the updates
* Some `ppa`s and software might have been removed
#### GUI (recommended)
Can be launched with `software-properties-gtk` [(e.g. with ssh -X or -Y)](../SSHDisplay.md)
* Remove anything from "other software" and "authentication" that has been disabled by the upgrade and **make a note of which**.

#### Terminal
* [Manipulate `sources.list`](ManagingInstalls.md) to remove any software that was disabled by the upgrade and **make a note of which**.

---

* `apt update` should now run without any errors or warnings
* Reinstall those that were removed
