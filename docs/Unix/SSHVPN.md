# SSH as a VPN
`ssh` can actually be used to tunnel network traffic also!
```bash
ssh -N -L <local_port>:<remote>:<remote_port> <user>@<remote>
```

e.g.
```bash
ssh -N -L 12345:example.com:443 james@abc.com
```

Will set up a tunnel such that `example.com:443` (443 is `https`) can be accessed at `localhost:12345` tunnelling traffic through `james@abc.com`
