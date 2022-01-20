# Diff

`git diff` is a very powerful feature.

One notable use of git diff is that it provides more options than regular `diff`.
For example, if there is one small change within one long line, regular `diff` cannot highlight this for you. `git diff`, on the other hand, can with the `--word-diff` flag.
Furthermore, `git diff` can be used outside a git repository using the `--no-index` flag. This allows is to function as a powerful diff replacement.

`git diff` can also be used in [patching](./patch.md).
