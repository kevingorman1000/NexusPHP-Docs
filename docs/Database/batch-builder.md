
# Batch Class Documentation

The `Batch` class is used for performing batch operations on a database, such as batch updates, inserts, and deletes.

## Class Overview

Namespace: `Nxp\Core\Database`

```php
namespace Nxp\Core\Database;

class Batch
{
    // Class properties and methods
}
```


## Constructor

The `Batch` class constructor initializes the class by establishing a connection to the database.

```php
/**
 * Constructs a new instance of the Batch class.
 *
 * @return void
 */
public function __construct()
```


## `updateBatch`

Updates multiple rows in a database table using a batch update.

```php
public function updateBatch($table, $data, $column)
```


### Example Usage:

```php
// Example data for updating 'users' table
$data = [
    ['user_id' => 1, 'name' => 'John'],
    ['user_id' => 2, 'name' => 'Jane'],
    // Add more rows as needed
];

$batch = new Batch();
$updatedRows = $batch->updateBatch('users', $data, 'user_id');

echo "Updated $updatedRows rows.";
```

## `insertBatch`

Inserts multiple rows into a database table using a batch insert.

```php
public function insertBatch($table, $data)
```

### Example Usage:

```php
// Example data for inserting into 'products' table
$data = [
    ['product_name' => 'Product A', 'price' => 50.00],
    ['product_name' => 'Product B', 'price' => 30.00],
    // Add more rows as needed
];

$batch = new Batch();
$insertedRows = $batch->insertBatch('products', $data);

echo "Inserted $insertedRows rows.";
```

## `deleteBatch`

Deletes multiple rows from a database table using a batch delete.

```php
public function deleteBatch($table, $column, $values)
```

### Example Usage:

```php
// Example data for deleting from 'orders' table
$idsToDelete = [101, 102, 103];

$batch = new Batch();
$deletedRows = $batch->deleteBatch('orders', 'order_id', $idsToDelete);

echo "Deleted $deletedRows rows.";
```

---

This concludes the documentation for the `Batch` class of the NexusPHP framework. Use these methods to efficiently perform batch database operations in your projects.

