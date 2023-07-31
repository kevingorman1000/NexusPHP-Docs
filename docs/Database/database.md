# Database Class

The `Database` class is responsible for handling the connection to the database using PDO (PHP Data Objects). It allows for connecting to different database types, such as MySQL, PostgreSQL, and CockroachDB.

## Class Overview

```php
<?php
namespace Nxp\Core\Database;

use PDO;
use PDOException;
use Nxp\Core\Config\ConfigHandler;

class Database
{
    // Class properties
    private static $pdo = null;
    private static $connectionAttempts = 0;
    public static $instance = null;

    // Class constructor (private to enforce Singleton pattern)
    private function __construct(){}

    // Singleton pattern - Get the instance of the Database class
    public static function getInstance()
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    // Method to establish a database connection
    public static function connect()
    {
        // ... (code to connect to the database)

    }

    // Method to disconnect from the database
    public static function disconnect()
    {
        // ... (code to disconnect from the database)

    }
}
```


## Class Properties 
- `private static $pdo`: A static variable to hold the PDO instance for the database connection. 
- `private static $connectionAttempts`: A static variable to keep track of the number of connection attempts made. 
- `public static $instance`: A static variable to hold the single instance of the `Database` class (Singleton pattern).

## Methods
### `public static function getInstance(): Database`

This method follows the Singleton pattern and returns the single instance of the `Database` class.

#### Return Value 
- `Database`: The instance of the `Database` class.
### `public static function connect(): PDO`

This method establishes a connection to the database using PDO based on the configuration provided in the `ConfigHandler`.

#### Exceptions 
- `PDOException`: If there are issues with the PDO extension, required PDO extensions are missing, or an invalid database type is provided.

#### Return Value 
- `PDO`: The PDO instance representing the database connection.
### `public static function disconnect(): void`

This method disconnects from the database and resets the connection attempts counter.---

**Note** : The `Database` class should be used as a Singleton to ensure there is only one instance for the entire application to share the same database connection.

You can use the `getInstance()` method to get the instance of the `Database` class, and then call the `connect()` method to establish a connection to the database. Once you are done with the database operations, you can call the `disconnect()` method to close the connection.

Example Usage:

```php
<?php
use Nxp\Core\Database\Database;

// Get the instance of the Database class (Singleton pattern)
$dbInstance = Database::getInstance();

// Establish a connection to the database
try {
    $pdo = $dbInstance->connect();
    // Perform database operations using $pdo
} catch (PDOException $e) {
    // Handle the connection error
}

// Disconnect from the database
$dbInstance->disconnect();
```
---


This documentation provides an overview of the `Database` class and its methods, helping developers understand how to use it within your NexusPHP framework effectively.
