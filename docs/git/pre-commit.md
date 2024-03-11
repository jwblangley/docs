# Pre-commit

The pre-commit script found in the local git repository (`.git/hooks/pre-commit)` can be any executable and will run before a `git commit`.
A useful use case is to check the formatting of code.
N.B it is not best practice to modify files in the pre-commit as tempting as it might be, since you may not *always* want the files to change and this can be frustrating.
It is better practice to abort the commit (non-zero return from `pre-commit`) and warn why.
If, after being warned, you want to commit anyway, pass `--no-verify` to `git commit`.

## Example

An example `pre-commit` script might be the following:

```bash
#!/bin/bash

# Exit on any fail and prevent commit
set -e

for file in $(git diff --cached --name-only --diff-filter=d | grep "\.py$")
do
  black --check $file
done
```
