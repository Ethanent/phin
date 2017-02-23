# phin

> Ultra-simple, lightweight, dependency-free Node.JS HTTP request client

[![phin on NPM](https://nodei.co/npm/phin.png)](https://www.npmjs.com/package/phin)

[![phin - Downloads Total](https://img.shields.io/npm/dt/phin.svg)](https://www.npmjs.com/package/phin) [![phin - Version](https://img.shields.io/npm/v/phin.svg)](https://www.npmjs.com/package/phin) [![phin - License](https://img.shields.io/npm/l/phin.svg)](https://www.npmjs.com/package/phin)

---

## Simple Usage
For a simple GET request.

```javascript
var p = require("phin");

p("https://www.ony.io", function(err, response) {
	if (!err) console.log(response.body);
});
```


## Installation

```
npm install phin
```


## Demonstrations

### GET request with custom headers

```javascript
p({
	"url": "https://ony.io",
	"headers": {
		"User-Agent": "phin"
	}
})
```

### POST request with data

```javascript
p({
	"url": "https://ony.io",
	"method": "POST",
	"port": 8080,
	"data": JSON.stringify({
		"name": "John Doe"
	})
}, function(err) {
	if (!err) console.log("Data sent!");
});
```

### GET request with authorization using `auth` option

```javascript
p({
	"url": "https://ony.io:8080",
	"auth": "ethan:letmein"
}, function(err, response) {
	if (!err) console.log(response.body);
});
```

### GET request with authorization through `url`

```javascript
p({
	"url": "https://ethan:letmein@ony.io:8080"
}, function(err, response) {
	if (!err) console.log(response.body);
});
```


---

## API

#### (options, callback)

- `options` - **required** *JS Object* or *String* - object containing request options or a URL to send a GET request to
	- `url` **required** *String* - URL to request (Can include port, auth. These will be used if their respective options are not present.)
	- `method` - *String* - Default: `'GET'` - Request method. Ex. `'GET'`
	- `port` - *Integer* (or integer as string) - Default: For HTTP, `80`. For HTTPS, `443`. - Request port
	- `headers` - *Object* - Request headers
	- `data` - *String* / non-circular JS object - Request data (request body)
	- `auth` - *String* - Authorization in `'user:pass'` format
- `callback` - **required** *Function* - (err, response) callback method
	- `err` - *Error* or *null* - An error object if an error occured or null if no error occured.
	- `response` - HTTP / HTTPS response object. See [Node.JS HTTP docs - HTTP.serverResponse class](https://nodejs.org/dist/latest-v7.x/docs/api/http.html#http-class-http-serverresponse).
		- `body` - Phin adds a `body` field to the `response` object. It is the response content.


## License (MIT)

Copyright 2017 Ethan Davis

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.