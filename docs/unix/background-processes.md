# Handling Background Processes

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
