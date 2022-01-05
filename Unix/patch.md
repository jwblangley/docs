# Patch

The `patch` command can usefully apply patches that are created with the `diff` tool.

For example:
Generate a patch file
```bash
diff foo.txt bar.txt > foo2bar.patch
```
Apply the patch file
```bash
patch foo.txt foo2bar.patch
```
Reverse the patch
```bash
patch -R foot.txt foo2bar.patch
```
