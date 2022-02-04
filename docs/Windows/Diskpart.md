# Using diskpart
Used for managing partitions, assigning volume letters, etc.

Access on the command line:

```cmd
diskpart
```

* `list <disk|volume|partition>`
* `select <disk|volume> <num>`
* `clean`: removes all partitions (and data!)
* `<assign|remove> letter=<letter>` (with volume selected)
