# Patch

## Interactive Patch Staging

* If you have modified a file in multiple places but want to only commit some of your changes git add has a patch option that allows you to interactively choose which parts of the file to stage.

```bash
git add [<files>] -p
```

## Creating and Applying Patches

* Similar to unix's [patch](../Unix/patch.md) git can be used to make patches
* The benefit when working in a git repository is that filenames/paths are registered in git history and do not need to be specified

* To create a diff

 ```bash
git diff [<files>] > mypatch.patch
```

* To apply a diff
  
```bash
git apply mypatch.patch
```

* To revert a diff

```bash
git apply -R mypatch.patch
```
