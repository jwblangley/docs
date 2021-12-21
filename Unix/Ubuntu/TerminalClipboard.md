# Use of the (Desktop) Clipboard in the Command Line
[`xclip`](https://github.com/astrand/xclip)
* `-o`: paste to `stdout`
* Use `-sel clip` option to use the main clipboard. Defaults to middle-mouse-click temporary clipboard otherwise.
* Very useful when combined with pipes e.g. `echo "test" | xclip -sel clip`
