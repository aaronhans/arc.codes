# <a id=arc.json.get href=#arc.css.get>`arc.css.get`</a>

Example `@css` route handler:

```javascript
let arc = require('@architect/functions')

function handler(req, res) {
  res({
    css: `body { background: pink; }`
  })
}

exports.handler = arc.css.get(handler)
```

Things to understand:

- `arc.css.get` accepts one or more functions that follow Express-style middleware signature: `(req, res, next)=>`
- `req` is a plain object with `path`, `method`, `query`, `params`, and `body` keys
- `res` is a function that must be invoked with named params: 
  - `css` a plain `Object` value
  - or `location` with a URL value (a string starting w `/`)
  - `session` (optional) a plain `Object`
  - `status` (optional) HTTP error status code responses: `500`, `403`, or `404`
- `res` can also be invoked with an `Error`
  - optionally the `Error` instance property of `code`, `status` or `statusCode` can be one of `403`, `404` or `500` to change the HTTP status code
- `next` is an optional function to continue middleware execution
