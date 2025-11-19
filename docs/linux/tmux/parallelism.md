# Tmux Parallelism

After splitting panes within tmux, a useful trick is to use `setw synchronize-panes` to be able to type in multiple panes at once.
If you are doing this to parallise work, you are likely wanting to partition work to be done.
To do this, within those panes, you can access a pane index using `${TMUX_PANE:1}`.
This index can be used as a partitioning key to parallelise work.

Note that this is an environment variable so will not persist over `ssh`.
I find the best way to do this is to tabulate the work using `paste` with machine names and the work to be done.
The machines can be `ssh`'d to and then look up their work with `grep` and `awk`.
