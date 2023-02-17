# ZSH script ordering

The following scripts run in order for the setup of a zsh shell.

1. `.zshenv` is always sourced
1. `.zprofile` runs for login shells
1. `.zshrc` only runs in interactive shells. Only include setup for interactive shells here
1. `.zlogin` runs for login shells. Much like `.zprofile`, but the shell can be considered fully set up

* `.zlogout` runs to teardown anything set up in `.zlogin`

## Login shells

A login shell is either that initially logged into or accessed with `ssh`.
A notable exception therefore are terminal sessions launched through the terminal apps in any UI session.
For my usage, I find this to be inconvenient, so I will look for and enable a setting to launch these terminal sessions as login shells.
