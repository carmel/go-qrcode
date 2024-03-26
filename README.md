# go-qrcode

Forks of [skip2/go-qrcode](https://github.com/skip2/go-qrcode). Replacing deprecated functions.

## Install

    go get -u github.com/carmel/go-qrcode/...

A command-line tool `qrcode` will be built into `$GOPATH/bin/`.

## Usage

    import qrcode "github.com/carmel/go-qrcode"

- **Create a 256x256 PNG image:**

        var png []byte
        png, err := qrcode.Encode("https://example.org", qrcode.Medium, 256)

- **Create a 256x256 PNG image and write to a file:**

        err := qrcode.WriteFile("https://example.org", qrcode.Medium, 256, "qr.png")

- **Create a 256x256 PNG image with custom colors and write to file:**

        err := qrcode.WriteColorFile("https://example.org", qrcode.Medium, 256, color.Black, color.White, "qr.png")

All examples use the qrcode.Medium error Recovery Level and create a fixed 256x256px size QR Code. The last function creates a white on black instead of black on white QR Code.

## CLI

A command-line tool `qrcode` will be built into `$GOPATH/bin/`.

        ```
        qrcode -- QR Code encoder in Go
        https://github.com/carmel/go-qrcode

        Flags:
        -d disable QR Code border
        -i invert black and white
        -o string
        out PNG file prefix, empty for stdout
        -s int
        image size (pixel) (default 256)
        -t print as text-art on stdout

        Usage:
        1. Arguments except for flags are joined by " " and used to generate QR code.
        Default output is STDOUT, pipe to imagemagick command "display" to display
        on any X server.

        qrcode hello word | display

        2. Save to file if "display" not available:

        qrcode "homepage: https://github.com/carmel/go-qrcode" > out.png
        ```

## Maximum capacity

The maximum capacity of a QR Code varies according to the content encoded and the error recovery level. The maximum capacity is 2,953 bytes, 4,296 alphanumeric characters, 7,089 numeric digits, or a combination of these.

## Borderless QR Codes

To aid QR Code reading software, QR codes have a built in whitespace border.

If you know what you're doing, and don't want a border, just set the parameter `DisableBorder` to `true`. It's still recommended you include a border manually.
