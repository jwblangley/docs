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

## Asymmetric Encryption

You can see a list of keys with `gpg --list-keys`. `--list-secret-keys` and `--list-public-keys` are also available.

1. Generate a key pair

    ```bash
    gpg --gen-key
    ```

1. Export your public key

    ```bash
    gpg --export --armor <name> > <name>.pub
    ```
    
1. (Optional) Make a backup of your private key. Only ever store this backup in offline media.
    ```bash
    gpg --export-secret-keys --armor <name> > <name>.priv
    ```

1. Import the other's public key

    ```bash
    gpg --import key.pub
    ```

1. (Optional) Trust the key
    
    ```bash
    gpg --edit-key <name>
    ```
    Enter `trust` then the level you wish to trust it to

1. Encrypt a file

    ```bash
    gpg --encrypt --recipient <recipient> <file>
    ```

1. Decrypt a received file

    ```bash
    gpg --decrypt <file>.gpg --output <file>
    ```
