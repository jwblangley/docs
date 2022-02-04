# Prevent/Allow Ubuntu Sleeping
e.g. For an Ubuntu Server
```bash
sudo systemctl <mask|unmask> sleep.target suspend.target hibernate.target hybrid-sleep.target
```
`mask` to prevent sleeping, `unmask` to (re)allow sleeping
