# Rebase

Rebasing is a method of overwriting history by moving commits fromone place to another.

Typical usage may look like

```bash
git rebase main
```

which will move the commits from the current branch onto the main branch.

## Onto

A typical scenario is creating a branch from an existing non-default branch to continue working (whilst the base branch is in review).
Once the base branch has been merged into the default branch, we want to move the new commits to a new branch off the default branch.
This is achieved using the following.

```bash
git rebase --onto <default_branch> <beginning_of_your_work_exclusive> <end_of_your_work_inclusive>
```

## Interactive

For anything more complicated, I recommend using 

```bash
git rebase <new_base> -i
```

Which can allow you to squash commits etc.

### Fixups

To fix a previous commit and automatically rebase, you can do the following:

```bash
git commit --fixup <ref>
GIT_SEQUENCE_EDITOR=: git rebase -i --autosquash <ref>~1
```

## rerere

To Reuse a previous Recorded conflict Resolution automatically, enable `git rerere`.

```bash
git config --global rerere.enabled true
```

If you do need to resolve a conflict differently, you can use the following after the fact.

```bash
git checkout --conflict=merge <path>
```
