# NexusPHP Database Configuration

The NexusPHP framework uses a configuration file to define the settings required for connecting to the database. This file, usually named `database.php` (located in app/config), returns an associative array containing the necessary parameters for establishing a database connection. Below is an explanation of each configuration setting and how to use it in your NexusPHP application.
## Configuration Settings 
1. `DATABASE_TYPE`:
    - Description: Specifies the type of SQL driver to use for the database connection. 
    - Values: Supported SQL drivers are `"mysql"`, `"pgsql"`, and `"cockroachdb"`. 
    - Example: To use MySQL as the database driver, set `"DATABASE_TYPE" => "mysql"`. 
2. `DATABASE_HOST`:
    - Description: Specifies the host address of the database server. 
    - Example: If your database server is running on the same machine as your web server, set `"DATABASE_HOST" => "localhost"`. If the database is hosted on a remote server, provide the appropriate IP address or domain name. Do **NOT** include the port.
3. `DATABASE_USER`:
    - Description: Specifies the username for the database user. 
    - Example: Set `"DATABASE_USER" => "your_db_username"`. 

4. `DATABASE_PASS`:
    - Description: Specifies the password for the database user. 
    - Example: Set `"DATABASE_PASS" => "your_db_password"`. Ensure to keep the password secure and not expose it in your code. 

5. `DATABASE_NAME`:
    - Description: Specifies the name of the database to connect to. 
    - Example: Set `"DATABASE_NAME" => "your_database_name"`. Replace `your_database_name` with the actual name of your database. 

6. `DATABASE_PORT`:
    - Description: Specifies the port number for the database connection. 
    - Example: If your database server is listening on the default MySQL port 3306, set `"DATABASE_PORT" => "3306"`. For PostgreSQL, the default port is 5432.

There is no need to use these details anywhere in your code as NexusPHP will automatically establish a connection to the database provided the details are correct.

Remember to replace the placeholders `'your_db_username'`, `'your_db_password'`, and `'your_database_name'` with your actual database credentials.

## Additional Notes 
- Make sure to keep the `database.php` file secure, as it contains sensitive information like the database username and password. 
- If your application requires different database configurations for development, staging, and production environments, you can create separate `database.php` files for each environment and load the appropriate file based on your environment settings.
