# Compression

## `gzip`

The `gzip` command can be used to compress single files. Add the `-#` replacing `#` with a number 1-9, for setting the compression level.

## `pigz`

By default, `gzip` does not use all cores. This can be ammended by using the `pigz` command instead. `pigz` is fully compatible with `gzip`

## `tar`

`gzip` can only compress a single file. `tar` (or `zip` - difference being inter-file compression in `tar`) creates a single archive file from multiple.
Combining `tar and gzip` is the standard way of making compressed archives.

* `-c` : Creates archive
* `-x` : Extracts the archive
* `-f` : Creates archive with given filename (use `-` for stdout)
* `-v` : Displays verbose information
* `-z` : Compresses the tar file using gzip

### Examples

#### Create a compressed archive

```bash
tar cfzv archive.tar file1 file2 file3
```

#### Decompress an archive

```bash
tar xfv archive.tar
```

#### Create a compressed archive using all CPU cores and the best compression level

```bash
tar cf - paths-to-archive | pigz -9 > archive.tar.gz
```
