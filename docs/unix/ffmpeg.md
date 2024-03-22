# ffmpeg

[ffmpeg](https://ffmpeg.org/) is a fantastic tool that allows complete conversion of video formats

## Basic syntax

```bash
ffmpeg -i input.avi output.mp4`
```

```bash
ffmpeg -i img%03d.png out.mp4
```

## Gotchas

* Not all h264 formats are available on multiple platforms. The most platform-agnostic format is `yuv420p` (nothing to do with 420 pixels)
    ```bash
    ffmpeg -i input.mp4 -vf format=yuv420p output.mp4
    ``` 
