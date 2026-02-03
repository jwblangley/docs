# Compression

## zstd

While `gzip` is good, `zstd` is becoming the de facto standard for modern systems.
It is significantly faster and produces as good or better (not guaranteed) compression ratios.

## `gzip`

The `gzip` command can be used to compress single files. Add the `-#` replacing `#` with a number 1-9, for setting the compression level.
`gzip` is natively single-threaded, but a multi-threaded implementation called `pigz` exists.

## `xz`

For the absolute best compression ratio, consider `xz`.
The tradeoff is that the compression and decompression time are very high.

## `tar`

Compression algorithms only compress a single file at a time. `tar` creates a single archive file from multiple.
Combining `tar and gzip` is the standard way of making compressed archives.

* `-c` : Creates archive (recursive by default)
* `-x` : Extracts the archive
* `-f` : Creates archive with given filename (use `-` for stdout)
* `-v` : Displays verbose information
* `-z` : Compresses the tar file using gzip

## Parallelism

When compressing multiple files, prefer _external parallelism_.
As an example, compress multiple files in parallel using a single thread each over one file at a time using all threads.
