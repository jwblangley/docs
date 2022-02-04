# xargs

`xargs` is a command line utility that allows the output of one command to be formatted correctly for another programs arguments.

For example, by default the command `ls` outputs over a number of lines, but `ls | xargs` will push these onto one line (space-separated).
This is very useful for substituting a command's results in another command. e.g. `rm $(ls | xargs)`. N.B: this is a contrived example where `rm -r *` would be easier.
