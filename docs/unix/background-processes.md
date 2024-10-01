# Handling Background Processes

## Quick Reference

* `Ctrl + Z`: suspend job in background
* `jobs`: list jobs
* `bg`: resume a job in the background
* `fg`: bring a job to the foreground
* `wait`: wait for background jobs to finish
* `foo &`: only runs `foo` in the background; stdin and stdout are still connected
* `foo >/dev/null 2>&1 &`: runs foo in the background and pipe all output to `/dev/null`. Some shells allow this syntax: `foo &>/dev/null &`. stdin is still connected
* `nohup foo`: Pipes stdout and stderr to `nohup.out`. stdin reads will result in errors or EOF. A foreground `nohup`'d job makes no real sense, so normally use `nohup foo &`
* `disown`: remove ownership of a job from the current shell. This means the current shell can be closed without killing the job. `nohup` does not do this by itself, so using `disown` after `nohup` is a good idea
* `stty tostop` or `stty -tostop`: Send (or do not send) `SIGTTOU` for background jobs if they try to write output. This causes background jobs to stop (or not) if they attempt terminal output.

## In scripts

See this code snippet on how to handle background processes within a script!

```bash
#!/usr/bin/env bash

echo "Starting a"
./a.sh | sed 's/^/A: /'&

echo "Starting b"
./b.sh | sed 's/^/B: /'&

# Forward signals to child processes
trap 'trap "" SIGTERM; kill 0; wait' SIGINT SIGTERM
# Wait for child processes to finish
wait
```

The `trap` command allows you to catch signals and execute code when they occur.
In this case we remove the trap and execute a `kill` and `wait` on any SIGINT or SIGTERM.
