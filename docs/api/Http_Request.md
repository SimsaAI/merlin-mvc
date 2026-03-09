# 🧩 Class: Request

**Full name:** [Merlin\Http\Request](../../src/Http/Request.php)

HTTP Request class

## 🚀 Public methods

### getRequestBody() · [source](../../src/Http/Request.php#L15)

`public function getRequestBody(): string|bool`

Get the raw request body
Caches the body since php://input can only be read once

**➡️ Return value**

- Type: string|bool


---

### getJsonBody() · [source](../../src/Http/Request.php#L30)

`public function getJsonBody(mixed $assoc = true): mixed`

Get and parse JSON request body

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$assoc` | mixed | `true` | When true, returns associative arrays. When false, returns objects |

**➡️ Return value**

- Type: mixed
- Description: Returns the parsed JSON data, or null on error

**⚠️ Throws**

- RuntimeException  if the JSON body cannot be parsed


---

### get() · [source](../../src/Http/Request.php#L46)

`public function get(string|null $name = null, mixed $defaultValue = null): mixed`

Get a parameter from the request (GET, POST, COOKIE, etc.)

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string\|null | `null` |  |
| `$defaultValue` | mixed | `null` |  |

**➡️ Return value**

- Type: mixed


---

### getPost() · [source](../../src/Http/Request.php#L57)

`public function getPost(string|null $name = null, mixed $defaultValue = null): mixed`

Get a POST parameter from the request

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string\|null | `null` |  |
| `$defaultValue` | mixed | `null` |  |

**➡️ Return value**

- Type: mixed


---

### getQuery() · [source](../../src/Http/Request.php#L68)

`public function getQuery(string|null $name = null, mixed $defaultValue = null): mixed`

Get a query parameter from the request

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string\|null | `null` |  |
| `$defaultValue` | mixed | `null` |  |

**➡️ Return value**

- Type: mixed


---

### getServer() · [source](../../src/Http/Request.php#L79)

`public function getServer(string|null $name = null, mixed $defaultValue = null): mixed`

Get a server variable from the request

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string\|null | `null` |  |
| `$defaultValue` | mixed | `null` |  |

**➡️ Return value**

- Type: mixed


---

### getMethod() · [source](../../src/Http/Request.php#L88)

`public function getMethod(): string`

Get the HTTP method of the request, accounting for method overrides in POST requests

**➡️ Return value**

- Type: string


---

### getScheme() · [source](../../src/Http/Request.php#L108)

`public function getScheme(): string`

Get the request scheme (http or https)

**➡️ Return value**

- Type: string


---

### getServerName() · [source](../../src/Http/Request.php#L117)

`public function getServerName(): string`

Get the server name from the request

**➡️ Return value**

- Type: string


---

### getServerAddr() · [source](../../src/Http/Request.php#L126)

`public function getServerAddr(): string`

Get the server IP address

**➡️ Return value**

- Type: string


---

### getHttpHost() · [source](../../src/Http/Request.php#L135)

`public function getHttpHost(): string`

Get the host from the request, accounting for Host header and server variables

**➡️ Return value**

- Type: string


---

### getPort() · [source](../../src/Http/Request.php#L153)

`public function getPort(): int`

Get the port number from the request, accounting for standard ports and Host header

**➡️ Return value**

- Type: int


---

### getContentType() · [source](../../src/Http/Request.php#L170)

`public function getContentType(): string`

Get the Content-Type header from the request

**➡️ Return value**

- Type: string


---

### getClientAddress() · [source](../../src/Http/Request.php#L183)

`public function getClientAddress(bool $trustForwardedHeader = false): string|bool`

Get the client's IP address, optionally trusting proxy headers

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$trustForwardedHeader` | bool | `false` |  |

**➡️ Return value**

- Type: string|bool


---

### getUri() · [source](../../src/Http/Request.php#L215)

`public function getUri(): string`

Get the request URI

**➡️ Return value**

- Type: string


---

### getPath() · [source](../../src/Http/Request.php#L224)

`public function getPath(): string`

Get the request path (URI without query string)

**➡️ Return value**

- Type: string


---

### getUserAgent() · [source](../../src/Http/Request.php#L234)

`public function getUserAgent(): string`

Get the User-Agent header from the request

**➡️ Return value**

- Type: string


---

### getAcceptableContent() · [source](../../src/Http/Request.php#L280)

`public function getAcceptableContent(bool $sort = false): array`

Gets an array with mime/types and their quality accepted by the browser/client from _SERVER["HTTP_ACCEPT"]

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$sort` | bool | `false` |  |

**➡️ Return value**

- Type: array


---

### getBestAccept() · [source](../../src/Http/Request.php#L289)

`public function getBestAccept(): string`

Gets best mime/type accepted by the browser/client from _SERVER["HTTP_ACCEPT"]

**➡️ Return value**

- Type: string


---

### getClientCharsets() · [source](../../src/Http/Request.php#L298)

`public function getClientCharsets(bool $sort = false): array`

Gets a charsets array and their quality accepted by the browser/client from _SERVER["HTTP_ACCEPT_CHARSET"]

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$sort` | bool | `false` |  |

**➡️ Return value**

- Type: array


---

### getBestCharset() · [source](../../src/Http/Request.php#L307)

`public function getBestCharset(): string`

Gets best charset accepted by the browser/client from _SERVER["HTTP_ACCEPT_CHARSET"]

**➡️ Return value**

- Type: string


---

### getLanguages() · [source](../../src/Http/Request.php#L315)

`public function getLanguages(bool $sort = false): array`

Gets languages array and their quality accepted by the browser/client from _SERVER["HTTP_ACCEPT_LANGUAGE"]

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$sort` | bool | `false` |  |

**➡️ Return value**

- Type: array


---

### getBestLanguage() · [source](../../src/Http/Request.php#L323)

`public function getBestLanguage(): string`

Gets best language accepted by the browser/client from _SERVER["HTTP_ACCEPT_LANGUAGE"]

**➡️ Return value**

- Type: string


---

### getBasicAuth() · [source](../../src/Http/Request.php#L332)

`public function getBasicAuth(): array|null`

Gets auth info accepted by the browser/client from $_SERVER['PHP_AUTH_USER']

**➡️ Return value**

- Type: array|null


---

### getDigestAuth() · [source](../../src/Http/Request.php#L347)

`public function getDigestAuth(): array|null`

Gets auth info accepted by the browser/client from $_SERVER['PHP_AUTH_DIGEST']

**➡️ Return value**

- Type: array|null


---

### isAjax() · [source](../../src/Http/Request.php#L365)

`public function isAjax(): bool`

Checks whether request has been made using AJAX

**➡️ Return value**

- Type: bool


---

### isSecure() · [source](../../src/Http/Request.php#L398)

`public function isSecure(): bool`

Checks whether request has been made using HTTPS

**➡️ Return value**

- Type: bool


---

### isPost() · [source](../../src/Http/Request.php#L407)

`public function isPost(): bool`

Checks whether the request method is POST

**➡️ Return value**

- Type: bool


---

### has() · [source](../../src/Http/Request.php#L417)

`public function has(mixed $name): bool`

Checks whether a parameter is present in the combined request data ($_REQUEST)

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | mixed | - | Parameter name |

**➡️ Return value**

- Type: bool


---

### hasPost() · [source](../../src/Http/Request.php#L427)

`public function hasPost(mixed $name): bool`

Checks whether a parameter is present in the POST data ($_POST)

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | mixed | - | Parameter name |

**➡️ Return value**

- Type: bool


---

### hasQuery() · [source](../../src/Http/Request.php#L437)

`public function hasQuery(mixed $name): bool`

Checks whether a parameter is present in the query string ($_GET)

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | mixed | - | Parameter name |

**➡️ Return value**

- Type: bool


---

### hasServer() · [source](../../src/Http/Request.php#L447)

`public function hasServer(mixed $name): bool`

Checks whether a server variable is present in $_SERVER

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | mixed | - | Server variable name |

**➡️ Return value**

- Type: bool


---

### getFile() · [source](../../src/Http/Request.php#L492)

`public function getFile(string $key): Merlin\Http\UploadedFile|null`

Get an uploaded file for a given key. Returns an UploadedFile object or null if no file was uploaded for the key.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$key` | string | - |  |

**➡️ Return value**

- Type: [UploadedFile](Http_UploadedFile.md)|null


---

### getFiles() · [source](../../src/Http/Request.php#L510)

`public function getFiles(string $key): array`

Get uploaded files for a given key. Returns an array of UploadedFile objects, even if only one file was uploaded.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$key` | string | - |  |

**➡️ Return value**

- Type: array



---

[Back to the Index ⤴](README.md)
