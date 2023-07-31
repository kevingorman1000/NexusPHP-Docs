# Configuration Files Overview

This document provides an overview of the configuration settings for the various PHP files used in the **NexusPHP** framework.

## app.php

The `app.php` configuration file contains settings that define the general behavior and file uploading settings for the application.

```php
<?php
return array(
    // General Settings
    "CORE_TITLE" => "TITLE",
    "COMMUNITY_NAME" => "COMMUNITY NAME",
    "PRELOADER_TRUE" => false,
    "BASE_PATH" => "/",
    "TIME_ZONE" => 'Europe/London',
    "CURRENT_VERSION" => "0.0.1", // Please ensure you leave this else you may corrupt your instance.

    // File Uploading Settings
    "ALLOWED_FILE_TYPES" => ["jpg", "jpeg", "png", "gif", "pdf", "docx", "xlsx"],
    "MAX_ALLOWED_FILE_SIZE" => 5242880, // 5MB in bytes
    "MAX_FILENAME_LENGTH" => 255, // Change this to your desired maximum filename length
    "MAX_RETRIES" => 10, // Change this to your desired maximum number of retries
    "RETRY_DELAY" => 100000, // Change this to your desired retry delay in microseconds

    // Backup Settings
    "BACKUP_ZIP_LOCATION" => "/data/core_backup"
);
```


## constants.php

The `constants.php` file defines various constants used throughout the application for paths, routes, configurations, plugins, views, and backup locations.

```php

<?php
use Nxp\Core\Config\ConfigHandler;

// Root Constant
define("ROOT", __DIR__ . "/../../");

// Base Constants
define("BASE_ROOT_DIR", ROOT);

// Routes
define("ROUTE_PATH", ROOT . "/app/routes/");

// Config Constants
define("CONFIG_ROOT_PATH", ROOT . "app/config/");

// Plugin Constants
define("PLUGIN_ROOT_PATH", ROOT . "src/plugins");

// Views Constants
define("VIEWS_ROOT_PATH", ROOT . "app/views/");

// Backup Constants
define("DEFAULT_BACKUP_LOCATION_ROOT", ROOT . "app/" . ConfigHandler::get("app", "BACKUP_ZIP_LOCATION"));
```


## database.php

The `database.php` configuration file contains settings for connecting to the database. It specifies the database type, host address, username, password, database name, and port number.

```php

<?php
return array(
    "DATABASE_TYPE" => "mysql", // Select SQL driver (mysql, pgsql, cockroachdb)
    "DATABASE_HOST" => "localhost", // The host address for the database server.
    "DATABASE_USER" => "root", // The username for the database user.
    "DATABASE_PASS" => "", // The password for the database user.
    "DATABASE_NAME" => "database_name", // The name of the database to connect to.
    "DATABASE_PORT" => "3306", // The port number for the database connection.
);
```


## keys.php

The `keys.php` configuration file contains sensitive keys and data, such as encryption keys, nonces, and API keys, securely stored away from the main codebase. This helps maintain good security practices and facilitates easy key rotation if required.

```php

<?php
return array(
    "CIPHER_KEY" => "1GPMv3DlTFO6uxbMPWgaKVymCwjL3Msc6xOIbfId8A/f/WCz8zGjqpDGJXpc3AVj"
);
```

In this Markdown document, we've provided a summary of the configuration settings for each of the specified PHP files in the **NexusPHP**  application. It's essential to store sensitive information securely, and using configuration files like `keys.php` helps ensure that sensitive keys and data are managed in a centralized and secure manner.

