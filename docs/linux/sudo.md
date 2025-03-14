# `sudo`

There are two commands that can be used to run commands as other users: `sudo` and `su`.
The primary difference between these two is that `sudo` is highly configurable on which user and which commands whereas `su` provides blanket access.
Additionally, `su` requires the password of the user that is being switched to whereas `sudo` (normally) requires the password of the user running the command, so is more friendly.
If using these commands for `root` access, it is alwalys recommended to use `sudo` over `su`.
The only time it is recommended to instead use `su` is to login (with a shell session rather than one command) to the account of another non-root user for whom you have access/know the password.

## sudoers Config file

`sudo` is very configurable. The config file is `/etc/sudoers`, however it should only ever be edited with `sudo visudo` to perform syntax checks before saving.
Additionally, the majority of configurations should not change the default `/etc/sudoers` file, but rather add additional permitted behaviour by adding new files to `/etc/sudoers.d`.
Write these files with `sudoedit`, but check them with `sudo visudo --check`.

The primary syntax is the following:

> `User OnHost = (Runas-User:Group) <space> Commands`
>
> [To put it very simple, it is “who where = (as_whom) what”](https://medium.com/kernel-space/linux-fundamentals-a-to-z-of-a-sudoers-file-a5da99a30e7f)

By default, if a command is given only as a binary, any arguemnts can be provided. Specific arguments can be specified to restrict this behaviour.

There are other, use-case-specific, behaviours that can be used, but a common one is to not require a password when running certain `sudo` commands.
This is achieved with the `NOPASSWD:` directive that is prepended before the command.
