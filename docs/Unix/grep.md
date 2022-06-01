# grep

`grep` is a well-known, useful command line utility to filter stdin.
Here are some lesser-known features.

## Regular expressions

Invoking `grep` with the `-E` flag allows you to use extended regular expressions.

## Matching patterns that come from a file

You might be in a use case where your patterns are defined in a file and you want to use this to grep your input.
This template can be (modified and) used to achieve this.

```bash
grep $(sed "s/^/-e /;s/$/ /" patterns.txt | tr -d "\n")
```
