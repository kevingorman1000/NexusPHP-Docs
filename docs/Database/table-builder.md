# NexusPHP Table Class Documentation

The `Table` class is responsible for managing database tables, including creating, dropping, and modifying tables. It provides a convenient interface to interact with the database and perform common table-related operations.

## Namespace

```php
namespace Nxp\Core\Database;
```

## Constructor

The constructor initializes the database connection using the `Database` class.

```php
public function __construct()
```

## `createTable`

This method creates a new table in the database with the given parameters.

```php
public function createTable($table, $columns, $primaryKey = '', $engine = 'InnoDB', $options = '')
```

- **Parameters** :
    - `$table` (string): The name of the new table to be created.
    - `$columns` (array): An associative array of column names and their data types.
    - `$primaryKey` (string, optional): The name of the primary key column, if any.
    - `$engine` (string, optional): The name of the database engine to use, defaulting to InnoDB.
    - `$options` (string, optional): Any additional options to include in the SQL statement, if any.

**Example:**

```php
use Nxp\Core\Database\Table;

// Creating a new table named 'users' with two columns: 'id' and 'username'.
$table = new Table();
$table->createTable('users', [
    'id' => 'INT(11) AUTO_INCREMENT',
    'username' => 'VARCHAR(50) NOT NULL',
]);
```

## `indexExists`
This method checks if an index with the given name exists on the specified table.

```php
private function indexExists($table, $index_name)
```

- **Parameters** :
    - `$table` (string): The name of the table to check.
    - `$index_name` (string): The name of the index to check for.
- **Returns** :
    - `bool`: Whether the index exists on the table.

## `tableExists`

This method checks if the specified table exists in the database.

```php
public function tableExists($table)
```

- **Parameters** :
    - `$table` (string): The name of the table to check.
- **Returns** :
    - `bool`: Whether the table exists in the database.

**Example:**

```php
use Nxp\Core\Database\Table;

$table = new Table();
if ($table->tableExists('users')) {
    echo "Table 'users' exists in the database.";
} else {
    echo "Table 'users' does not exist in the database.";
}
```

## `tablesExist`
This method checks if the specified tables exist in the database.

```php
public function tablesExist($tables)
```

- **Parameters** :
    - `$tables` (array): An array of table names to check.
- **Returns** :
    - `array`: An associative array of table names and their existence in the database.

**Example:**

```php
use Nxp\Core\Database\Table;

$table = new Table();
$tableNames = ['users', 'posts', 'comments'];
$tableExistsMap = $table->tablesExist($tableNames);

foreach ($tableExistsMap as $tableName => $exists) {
    echo "Table '$tableName' " . ($exists ? "exists" : "does not exist") . " in the database.";
}
```

## `dropTable`

This method drops the specified table from the database.

```php
public function dropTable($table)
```

- **Parameters** :
    - `$table` (string): The name of the table to drop.

**Example:**

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->dropTable('users');
```

## `addColumn`
This method adds a new column to the specified table.
```php
public function addColumn($table, $column, $type)
```

- **Parameters** :
    - `$table` (string): The name of the table to add the column to.
    - `$column` (string): The name of the new column.
    - `$type` (string): The data type of the new column.

**Example:**

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->addColumn('users', 'email', 'VARCHAR(255) NOT NULL');
```

## `dropColumn`
This method drops the specified column from the specified table.

```php
public function dropColumn($table, $column)
```

- **Parameters** :
    - `$table` (string): The name of the table to drop the column from.
    - `$column` (string): The name of the column to drop.

**Example:**

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->dropColumn('users', 'email');
```

## `addIndex`

This method adds an index to the specified table and column. 

```php
public function addIndex($table, $column, $unique = false)
```

- **Parameters** : 
    - `$table` (string): The name of the table to add the index to. 
    - `$column` (string): The name of the column to add the index to. 
    - `$unique` (bool, optional): Whether the index should be unique or not. Default is `false`.

**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->addIndex('users', 'email', true);
```


## `dropIndex`

 This method drops the index from the specified table and column. 

```php
public function dropIndex($table, $column)
```
- **Parameters** : 
    - `$table` (string): The name of the table to drop the index from. 
    - `$column` (string): The name of the column to drop the index from.

**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->dropIndex('users', 'email');
```

## `addForeignKey`
This method adds a foreign key constraint to a table. 
```php
public function addForeignKey($table, $column, $refTable, $refColumn, $onDelete = 'CASCADE', $onUpdate = 'CASCADE')
```
- **Parameters** : 
    - `$table` (string): The name of the table. 
    - `$column` (string): The name of the column that will have the foreign key constraint. 
    - `$refTable` (string): The name of the referenced table. 
    - `$refColumn` (string): The name of the referenced column. 
    - `$onDelete` (string, optional): The action to take when the referenced row is deleted. Defaults to 'CASCADE'. 
    - `$onUpdate` (string, optional): The action to take when the referenced row is updated. Defaults to 'CASCADE'.

**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->addForeignKey('orders', 'customer_id', 'customers', 'id', 'SET NULL', 'NO ACTION');
```


## `dropForeignKey`
This method drops a foreign key constraint from a table. 
```php
public function dropForeignKey($table, $column)
```

- **Parameters** : 
    - `$table` (string): The name of the table. 
    - `$column` (string): The name of the column that has the foreign key constraint.

**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->dropForeignKey('orders', 'customer_id');
```


## `disableForeignKeyChecks`

This method disables foreign key constraint checks for the current connection.

```php
public function disableForeignKeyChecks()
```


**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->disableForeignKeyChecks();
```

## `enableForeignKeyChecks`
This method enables foreign key constraint checks for the current connection.
```php
public function enableForeignKeyChecks()
```

**Example:** 

```php
use Nxp\Core\Database\Table;

$table = new Table();
$table->enableForeignKeyChecks();
```

## Conclusion

The `Table` class provides a set of useful methods to interact with database tables. By using these methods, you can create, drop, modify tables, add indexes, and manage foreign key constraints effectively.

Please note that these examples assume you have properly set up the database connection using the `Database` class before using the `Table` class methods.
