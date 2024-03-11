# Shared tmux Sessions

## Background

* tmux will create (directories of) sockets within `TMUX_TMPDIR` or `/tmp` if unset.
* The default socket name is `default` within this folder
    * This can be changed per call with the `-L` flag
* The socket path (e.g. `/tmp/tmux-1000/default`) can be changed with the `-S` flag

## Sharing

* To share a session, simply allow other users (via unix user groups) access to the socket
* In version (`tmux -V`) 3.3 and later an additional step is required.
    * Use `tmux server-access -a <user>` to add a user (specificying `-r` or `-w` for read or write access)
