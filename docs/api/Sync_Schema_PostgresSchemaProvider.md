# 🧩 Class: PostgresSchemaProvider

**Full name:** [Merlin\Sync\Schema\PostgresSchemaProvider](../../src/Sync/Schema/PostgresSchemaProvider.php)

## 🚀 Public methods

### __construct() · [source](../../src/Sync/Schema/PostgresSchemaProvider.php#L8)

`public function __construct(PDO $pdo): mixed`

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$pdo` | PDO | - |  |

**➡️ Return value**

- Type: mixed


---

### listTables() · [source](../../src/Sync/Schema/PostgresSchemaProvider.php#L15)

`public function listTables(string|null $schema = null): array`

Lists tables, views, materialized views, and foreign tables.

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$schema` | string\|null | `null` |  |

**➡️ Return value**

- Type: array


---

### getTableSchema() · [source](../../src/Sync/Schema/PostgresSchemaProvider.php#L38)

`public function getTableSchema(string $table, string|null $schema = null): Merlin\Sync\Schema\TableSchema`

**🧭 Parameters**

| Name | Type | Default | Description |
|---|---|---|---|
| `$table` | string | - |  |
| `$schema` | string\|null | `null` |  |

**➡️ Return value**

- Type: [TableSchema](Sync_Schema_TableSchema.md)



---

[Back to the Index ⤴](README.md)
