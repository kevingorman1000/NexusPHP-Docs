# NexusPHP Transactions Class Documentation

The `Transactions` class is part of the NexusPHP framework and is responsible for managing database transactions. Transactions provide a way to group multiple SQL queries into a single atomic unit of work, ensuring that either all of the queries are executed successfully or none of them are executed at all. This class provides methods to begin, commit, and rollback transactions, as well as to check if a transaction is active.

## Class Details 
- **Namespace:**  Nxp\Core\Database 
## Constructor
### `__construct()`

The constructor initializes the PDO object by calling the `connect()` method from the `Database` class.

**Example:** 

```php
use Nxp\Core\Database\Transactions;

// Create a new instance of the Transactions class
$transactions = new Transactions();
```

## Methods
### `beginTransaction()`

Initiates a transaction.

**Example:** 

```php
use Nxp\Core\Database\Transactions;

$transactions = new Transactions();
$transactions->beginTransaction();

// Perform database operations within the transaction
// For example, insert, update, or delete data
// ...

// Commit the transaction
$transactions->commitTransaction();
```


### `commitTransaction()`

Commits a transaction, making all the changes performed within the transaction permanent.

**Example:** 

```php
use Nxp\Core\Database\Transactions;

$transactions = new Transactions();
$transactions->beginTransaction();

// Perform database operations within the transaction
// For example, insert, update, or delete data
// ...

// Commit the transaction
$transactions->commitTransaction();
```


### `rollbackTransaction()`

Rolls back a transaction, discarding all changes made within the transaction.

**Example:** 

```php

use Nxp\Core\Database\Transactions;

$transactions = new Transactions();
$transactions->beginTransaction();

try {
    // Perform database operations within the transaction
    // For example, insert, update, or delete data
    // ...

    // Check for some condition
    if ($someCondition) {
        // Rollback the transaction if the condition is not met
        $transactions->rollbackTransaction();
    } else {
        // Commit the transaction if the condition is met
        $transactions->commitTransaction();
    }
} catch (PDOException $e) {
    // Handle exceptions if any occur during transaction operations
    // ...
}
```


### `inTransaction()`

Checks if a transaction is active.

**Return Value:**  
- `true` if a transaction is currently active. 
- `false` if no transaction is active.

**Example:** 

```php

use Nxp\Core\Database\Transactions;

$transactions = new Transactions();
$isTransactionActive = $transactions->inTransaction();

if ($isTransactionActive) {
    // A transaction is active, handle accordingly
    // ...
} else {
    // No transaction is active, handle accordingly
    // ...
}
```

## Error Handling

The `Transactions` class catches any `PDOException` that may occur during transaction operations and logs the error using the `Logger` class from the `Nxp\Core\Security\Logging` namespace. After logging the error, the method `redirectToPreviousPageOrHome()` from the `Nxp\Core\Utils\Navigation` namespace is called to redirect the user to the previous page or the home page.

It is essential to handle exceptions properly to maintain the integrity of the database and ensure the application's robustness. You may customize the error handling as per your specific use case.

**Note:**  Make sure to include the necessary `use` statements for the classes used in the examples.
