# The splitting/deprecation of git checkout

The `git checkout` command has two distinct uses. One is to switch and/or create branches and the other is to restore files to a previous index.
These two functions have been separated out to avoid confusion.

## Switch

To switch branches, you should now use the following:

```bash
git switch <branch>
```

adding `-c` to create a new branch.

## Restore

To restore files from a previous index, you should now use the following:

```bash
git restore -s <ref> <path>
```

This allows a new feature: restoring with patches using the `-p` command, [similar to it's usage in `git add`](./patch.md#interactive-patch-staging).
