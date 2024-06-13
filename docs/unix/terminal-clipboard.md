# Use of the (Desktop) Clipboard in the Command Line

## [`clipcopy` and `clippaste`](https://github.com/ohmyzsh/ohmyzsh/blob/master/lib/clipboard.zsh)

* When using a oh-my-zsh, the commands `clipcopy` and `clippaste` can be used to access the clipboard. These commands are platform-agnostic 

## [`xclip`](https://github.com/astrand/xclip)

* `-o`: paste to `stdout`
* Use `-sel clip` option to use the main clipboard. Defaults to middle-mouse-click temporary clipboard otherwise.
* Very useful when combined with pipes e.g. `echo "test" | xclip -sel clip`

## `clip.exe` for WSL

* Copy into the Windows clipboard from WSL can be done by piping into `clip.exe`
