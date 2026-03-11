# 🧩 Class: ClarityEngine

**Full name:** [Merlin\Mvc\Engines\ClarityEngine](../../src/Mvc/Engines/ClarityEngine.php)

Clarity template engine.

Compiles `.clarity.html` templates into isolated PHP classes that are
cached on disk.  Templates have no access to arbitrary PHP — they can
only use the variables passed to render() and the registered filters.

Usage
-----
```php
$ctx->setView(new ClarityEngine());
$ctx->view()
    ->setPath(__DIR__ . '/../views')
    ->setLayout('layouts/main');

// Register a custom filter
$ctx->view()->addFilter('currency', fn($v) => number_format($v, 2) . ' €');
```

Template extension: .clarity.html  (overridable via setExtension())

Cache location: sys_get_temp_dir()/clarity  (configurable via setCachePath())

## 🚀 Public methods

### __construct() · [source](../../src/Mvc/Engines/ClarityEngine.php#L36)

`public function __construct(array $vars = []): mixed`

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$vars` | array | `[]` |  |

**➡️ Return value**

- Type: mixed


---

### render() · [source](../../src/Mvc/Engines/ClarityEngine.php#L271)

`public function render(string $view, array $vars = []): string`

Render a view template and return the result as a string.

If a layout is configured via setLayout(), the view is first rendered and then
wrapped in the layout. The layout receives the rendered content in the `content`
variable.

Templates are automatically compiled to cached PHP classes. The cache is
automatically invalidated when source files change.

**Basic rendering:**
```php
$html = $engine->render('welcome', [
    'user' => ['name' => 'John', 'email' => 'john@example.com'],
    'title' => 'Welcome Page'
]);
```

**With layout:**
```php
$engine->setLayout('layouts/main');
$html = $engine->render('pages/dashboard', [
    'stats' => $dashboardStats
]);
// The layout receives 'content' variable with rendered 'pages/dashboard'
```

**Without layout (override):**
```php
$engine->setLayout(null); // Temporarily disable layout
$partial = $engine->render('partials/widget', ['data' => $widgetData]);
```

**Namespaced templates:**
```php
$engine->addNamespace('admin', __DIR__ . '/admin_templates');
$html = $engine->render('admin::dashboard', $data);
```

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$view` | string | - | View name to render. Can include namespace prefix (e.g. 'admin::dashboard'). |
| `$vars` | array | `[]` | Variables to pass to the template. Objects are automatically converted to arrays. |

**➡️ Return value**

- Type: string
- Description: Rendered HTML/output.

**⚠️ Throws**

- ClarityException  If template not found or compilation fails.


---

### renderPartial() · [source](../../src/Mvc/Engines/ClarityEngine.php#L289)

`public function renderPartial(string $view, array $vars = []): string`

Render a partial view (without applying a layout) and return the output.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$view` | string | - | View name to resolve and render. |
| `$vars` | array | `[]` | Variables for this render call. |

**➡️ Return value**

- Type: string
- Description: Rendered HTML/output.


---

### renderLayout() · [source](../../src/Mvc/Engines/ClarityEngine.php#L319)

`public function renderLayout(string $layout, string $content, array $vars = []): string`

Render a layout template wrapping provided content.

The layout receives the rendered view in the `content` variable.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$layout` | string | - | Layout view name. |
| `$content` | string | - | Previously rendered content. |
| `$vars` | array | `[]` | Additional variables to pass to the layout. |

**➡️ Return value**

- Type: string
- Description: Rendered layout output.


---

### addFilter() · [source](../../src/Mvc/Engines/ClarityEngine.php#L172)

`public function addFilter(string $name, callable $fn): static`

Register a custom filter callable.

Filters transform a piped value and are invoked in templates using pipe syntax:
- Simple filter: `{{ value |> filterName }}`
- Filter with arguments: `{{ value |> filterName(arg1, arg2) }}`
- Chained filters: `{{ value |> filter1 |> filter2 |> filter3 }}`

Filters receive the piped value as the first parameter, followed by any arguments
specified in the template.

**Example: Currency filter**
```php
$engine->addFilter('currency', function($amount, string $symbol = '€') {
    return $symbol . ' ' . number_format($amount, 2);
});
```

Template usage:
```twig
{{ price |> currency }}       {# Output: € 99.99 #}
{{ price |> currency('$') }}  {# Output: $ 99.99 #}
```

**Example: Excerpt filter**
```php
$engine->addFilter('excerpt', function($text, int $length = 100) {
    return mb_strlen($text) > $length
        ? mb_substr($text, 0, $length) . '…'
        : $text;
});
```

Template usage:
```twig
{{ article.body |> excerpt(150) }}
```

**Built-in filters:**
- Text: `upper`, `lower`, `trim`, `truncate`, `escape`, `raw`
- Numbers: `number`, `abs`, `round`, `ceil`, `floor`
- Arrays: `join`, `length`, `first`, `last`, `keys`, `values`, `map`, `filter`, `reduce`
- Dates: `date`, `date_modify`, `format_datetime`
- Other: `json`, `default`, `unicode`

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string | - | Filter name used in templates (e.g. 'currency'). |
| `$fn` | callable | - | Callable with signature: fn($value, ...$args): mixed |

**➡️ Return value**

- Type: static
- Description: Fluent interface


---

### addFunction() · [source](../../src/Mvc/Engines/ClarityEngine.php#L188)

`public function addFunction(string $name, callable $fn): static`

Register a custom function callable.

Functions are called directly in templates, e.g. `{{ name(arg) }}`.
This is distinct from filters, which transform a piped value.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string | - | Function name used in templates (e.g. 'formatDate'). |
| `$fn` | callable | - | fn(...$args): mixed |

**➡️ Return value**

- Type: static


---

### setCachePath() · [source](../../src/Mvc/Engines/ClarityEngine.php#L200)

`public function setCachePath(string $path): static`

Set the directory where compiled templates should be cached.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$path` | string | - | Absolute path to the cache directory. |

**➡️ Return value**

- Type: static


---

### getCachePath() · [source](../../src/Mvc/Engines/ClarityEngine.php#L211)

`public function getCachePath(): string`

Get the currently configured cache directory.

**➡️ Return value**

- Type: string
- Description: Absolute path to the cache directory.


---

### flushCache() · [source](../../src/Mvc/Engines/ClarityEngine.php#L221)

`public function flushCache(): static`

Flush all cached compiled templates.

**➡️ Return value**

- Type: static


---

### use() · [source](../../src/Mvc/Engines/ClarityEngine.php#L46)

`public function use(Clarity\Module $module): static`

Register a module, granting it access to this engine instance so it can
self-register filters, functions, services, and block directives.

Modules are the recommended way to bundle related features (e.g. a full
localization set with filters, a locale stack, and `with_locale` blocks).

```php
$engine->use(new ClarityLocalizationModule([
    'locale'            => 'de_DE',
    'translations_path' => __DIR__ . '/locales',
]));
```

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$module` | Clarity\Module | - | Module to register. |

**➡️ Return value**

- Type: static


---

### addInlineFilter() · [source](../../src/Mvc/Engines/ClarityEngine.php#L69)

`public function addInlineFilter(string $name, array $definition): static`

Register an inline filter definition that is compiled directly into the
generated PHP render body (zero runtime call overhead).

The definition must follow the same format as the built-in inline filters:
```php
$engine->addInlineFilter('my_upper', [
    'php' => '\mb_strtoupper((string) {1})',
]);
```
Template placeholders: `{1}` for the piped value, `{2}`, `{3}`, … for
additional parameters declared in `params`.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string | - | Filter name. |
| `$definition` | array | - |  |

**➡️ Return value**

- Type: static


---

### addBlock() · [source](../../src/Mvc/Engines/ClarityEngine.php#L95)

`public function addBlock(string $keyword, callable $handler): static`

Register a handler for a custom block directive (e.g. `with_locale`).

The handler is a callable that receives the raw text after the keyword,
source path and line for error messages, and a `$processExpr` callable
that converts a Clarity expression string to a PHP expression string.
It must return a PHP statement string.

```php
$engine->addBlock('with_locale', function(string $rest, string $path, int $line, callable $expr): string {
    return "\$this->__fl['__locale']->push({$expr(trim($rest))});"
});
$engine->addBlock('endwith_locale', fn(...) => "\$this->__fl['__locale']->pop();");
```

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$keyword` | string | - | The directive keyword in lowercase (e.g. 'with_locale'). |
| `$handler` | callable | - | See `BlockRegistry` for the expected signature. |

**➡️ Return value**

- Type: static


---

### addFilterService() · [source](../../src/Mvc/Engines/ClarityEngine.php#L117)

`public function addFilterService(string $name, mixed $service): static`

Store a non-callable service object in the filter registry so that
compiled template render bodies can access it via `$this->__fl['key']`.

This is primarily used by modules that need shared mutable state (e.g. a
locale stack) accessible both from closures that close over the object
*and* from inline filter PHP templates using `$this->__fl['__key']->method()`.

Key names should be prefixed with `__` to avoid conflicts with real
filter names (e.g. `'__locale'`, `'__translator'`).

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$name` | string | - | Key under which the service is accessible. |
| `$service` | mixed | - | Service value (not required to be callable). |

**➡️ Return value**

- Type: static



---

[Back to the Index ⤴](README.md)
