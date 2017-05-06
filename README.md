# path match

[![Greenkeeper badge](https://badges.greenkeeper.io/blakeembrey/path-match.svg)](https://greenkeeper.io/)

Thin wrapper around [path-to-regexp](https://github.com/component/path-to-regexp) to make extracting the param names easier.

```js
var route = require('path-match')({
  // path-to-regexp options
  sensitive: false,
  strict: false,
  end: false,
});

// create a match function from a route
var match = route('/post/:id');

// match a route
var parse = require('url').parse;
require('http').createServer(function (req, res) {
  var params = match(parse(req.url).pathname);

  // no match
  if (params === false) {
    res.statusCode = 404;
    res.end();
    return;
  }

  // the matched id
  var id = params.id;

  // do stuff with the ID
})
```

## License

(The MIT License)

Copyright (c) 2014 segmentio &lt;team@segment.io&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
