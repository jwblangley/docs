# xargs

`xargs` is a command line utility that formats stdin correctly for another program's arguments and invokes that program

For example, by default the command `ls` outputs over a number of lines, but `ls | xargs` will push these onto one line (space-separated).
This is very useful for substituting a command's results in another command. e.g. `ls | xargs rm`. N.B: this is a contrived example where `rm -r *` would be easier.

`xargs` is therefore very useful for scripting, but it also becomes essential if you would otherwise have a massive number of program arguments.
For example if you were deleting thousands of files (by name (contrived example)) and were to put them all onto the command line with `$()`, some would be cut short since there is a maximum argument limit. `xargs` obeys this and will split the call into multiple calls if necessary to accommodate this.
This can be manually achieved with the `-n <n>` argument which allows only `n` arguments per call. This also opens up much more scripting potential.
