# Encryption

Encryption can be achieved either using `gpg` and/or [`openssl`](./ssl.md).

## Symmetric Encryption

A simple symmetric encryption can be achieved with the following:

```bash
gpg -c <file>
```

which will prompt for a passphrase and produce an encrypted file with an appended `.gpg` suffix.

To decrypt the encrypted file use the following:

```bash
gpg <encrypted_file>
```

### Encryption Algorithm

`gpg` allows a number of algorithms. To view these algorithms run:

```bash
gpg --version
```

For symmetric encryption, look for algorithms listed under `Cypher:`.

Using one of these algorithms can be achieved as follows.

```bash
gpg --cipher-algo <ALGO> <file>
```

No change is required to the decrypt command.
