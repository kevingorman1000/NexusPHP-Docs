# NexusPHP Query Class Documentation

The `Query` class in the NexusPHP framework is a powerful tool for building and executing SQL queries with various operations like SELECT, INSERT, UPDATE, and DELETE. This documentation provides an in-depth guide on how to use the `Query` class along with plenty of examples to demonstrate its capabilities.

## Constructor

The constructor of the `Query` class establishes a connection to the database.

```php
use Nxp\Core\Database\Query;

// Create a new Query object
$query = new Query();
```


## Setting the Table

You must specify the table to query using the `table()` method.

```php
// Set the table to query
$query->table('users');
```

## Selecting Columns

In the query, you can specify the columns to select using the `select()` method. By default, when using `select()`, all columns are selected using the `*`` SQL flag.

If you do not want to select all data, then you are able to provide an array with the column names of what you do want to select.

```php
// Select all columns
$query->table('users')->select();

// Select specific columns
$query->table('users')->select(['id', 'username', 'email']);
```

## The WHERE Clause

You can set the WHERE clause for the query using the `where()` method. It accepts an associative array or a string.

```php
// Using an associative array for WHERE clause
$query->table('users')->select()->where(['id' => 1, 'role' => 'admin']);

// Using a string for WHERE clause
$query->table('users')->select()->where('id = :id', [':id' => 1]);
```

## The ORDER BY Clause

To order the query results, use the `orderBy()` method.

```php

// Order by 'username' in ascending order
$query->table('users')->select()->orderBy('username');

// Order by 'created_at' in descending order
$query->table('posts')->select()->orderBy('created_at', 'DESC');
```

## The LIMIT Clause

Use the `limit()` method to set a maximum number of rows to return.

```php
// Get only the first 5 rows
$query->table('users')->select()->limit(5);
```

## Inner Joins

You can add INNER JOIN clauses to the query using the `join()` method.

```php
// Add an INNER JOIN clause
$query->table('users')
      ->join('posts', 'users.id = posts.user_id');
```


## Executing Queries

To execute the query and get the result set, use the `get()` method.

```php
// Execute the query and get all rows
$result = $query->table('users')->get();

// Execute the query and get the first row
$firstRow = $query->table('users')->first();
```


## The first() Method

The `first()` method returns the first row of the query result or `null` if the result is empty.

```php
// Get the first user
$user = $query->table('users')->where('id = :id', [':id' => 1])->first();
```


## The count() Method

The `count()` method returns the number of rows that match the current query conditions.

```php
// Count the number of active users
$count = $query->table('users')->where('active = :active', [':active' => true])->count();
```


## The insert() Method

The `insert()` method inserts a new row into the database table with the given data and returns the new row's ID.

```php
// Insert a new user
$data = [
    'username' => 'newuser',
    'email' => 'newuser@example.com',
    'created_on' => '2023-07-31 12:00:00'
];
$newUserId = $query->table('users')->insert($data);
```


## The update() Method

The `update()` method updates one or more rows in the database table with the given data and WHERE clause.

```php
// Update the email of a user
$data = [
    'email' => 'updatedemail@example.com',
];
$query->table('users')->where('id = :id', [':id' => 1])->update($data);
```


## The delete() Method

The `delete()` method deletes one or more rows from the database table with the given WHERE clause.

```php
// Delete a user
$query->table('users')->where('id = :id', [':id' => 1])->delete();
```

This comprehensive guide should help you effectively use the `Query` class within the NexusPHP framework for building and executing SQL queries. Happy coding!
