# mjpeg2jpegs
`mjpeg2jpegs` - convert a MJPEG stream to mutliple JPEGs

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]

It allows you to convert a MJPEG stream to multiple JPEGs, which is quite useful if you want to save the MJPEG stream from a webcam into a stream of JPEGs for further post-processing.

## Example

```js
var mjpeg2jpegs = require("mjpeg2jpegs");
var http = require("http");
http.request({
    hostname: "localhost",
    path: "/videostream.cgi",
}, mjpeg2jpegs(function (res) {
    res.on("imageHeader", function (header) {
        console.log("Image header: ", header);
    });
    res.on("imageData", function (data) {
        console.log("Image data: ", data.length);
    });
    res.on("imageEnd", function () {
        console.log("Image end");
    });
})).end();
```

## Installation

```bash
npm install mjpeg2jpegs
```

## License

[MIT](LICENSE)

[npm-image]: https://img.shields.io/npm/v/mjpeg2jpegs.svg
[npm-url]: https://npmjs.org/package/mjpeg2jpegs
[downloads-image]: https://img.shields.io/npm/dm/mjpeg2jpegs.svg
[downloads-url]: https://npmjs.org/package/mjpeg2jpegs
