# MPV (remote) control library

[![PkgGoDev](https://pkg.go.dev/badge/github.com/slashformotion/gompv)](https://pkg.go.dev/github.com/slashformotion/gompv)

This library provides everything needed to (remotely) control the [mpv media player](https://mpv.io/).

It provides an easy api, a json api and rpc functionality.

## Usage

```bash
go get github.com/slashformotion/gompv
```

Start mpv:

```bash
mpv --idle --input-ipc-server=/tmp/mpvsocket
```

Remote control:

```go
import (
    mpv github.com/slashformotion/gompv
)

func main(){
    ipcc := mpv.NewIPCClient("/tmp/mpvsocket") // Lowlevel client
    c := mpv.NewClient(ipcc) // Highlevel client

    // Play "movie.mp4"
    c.LoadFile("movie.mp4", mpv.LoadFileModeReplace)
    // Pause
    c.SetPause(true)
    // Seek a position in the track
    c.Seek(600, mpv.SeekModeAbsolute)
    c.SetFullscreen(true)
    // Unpause
    c.SetPause(false)

    // Get position
    pos, err := c.Position()
    fmt.Printf("Position in Seconds: %.0f", pos)
}
```


## Features

- Low-Level and High-Level API

## Contribute

Feel free to make a pull request.

## License

See [LICENSE](LICENSE) file.
