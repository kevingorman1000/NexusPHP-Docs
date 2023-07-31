# Directory Structure

The directory structure of the **NexusPHP** framework is organized in a way to maintain a clean separation of concerns and follow best practices. Here's an overview of the main directories:

1. **app** : This directory holds the core application files. These are the files that should be edited by you.
    - **config** : Contains configuration files for the application settings.
    - **controllers** : Contains the application controllers. The `Welcome` directory holds the default controller.
    - **data** : Stores application data, such as backups and plugins.
    - **core_backup** : Contains core backup data.
    - **plugins** : Holds plugins data.
    - **middlewares** : Contains application middleware classes.
    - **routes** : Houses application routes.
    - **views** : Contains views for the application. The `Welcome` directory holds the default views.

2. **lib** : This directory holds any additional libraries used in the application.

3. **logs** : Contains log files for application logging.

4. **migrations** : Holds database migration files.

5. **public** : This is the web server's document root, where the application's publicly accessible files reside.

6. **src** : This directory holds the core source code for the **NexusPHP** framework.

    - **bin** : Contains binary files.
    - **nexus** : The main executable file for running **NexusPHP** commands.
    - **src** : Source code for the `nexus` binary.
    - **Bootstrap** : Holds bootstrap files.
    - **Controller** : Contains controller classes for the `nexus` binary.
    - **Database** : Contains database-related classes for the `nexus` binary.
    - **Download** : Contains download-related classes for the `nexus` binary.
    - **Info** : Contains information-related classes for the `nexus` binary.
    - **core** : Contains the core classes and components for the framework.
    - **Bootstrap** : Holds bootstrap files for the framework.
    - **Common** : Contains common classes used throughout the framework.
    - **Abstracts** : Abstract classes, including middleware abstracts.
    - **Interfaces** : Interfaces used in the framework, including middleware and plugin interfaces.
    - **Config** : Contains configuration classes for the framework.
    - **Database** : Contains database-related classes and exceptions for the framework.
    - **Hook** : Holds hook classes used for extensibility and plugin management.
    - **Middleware** : Contains middleware classes for the framework.
    - **PluginManager** : Handles the plugin management and registration.
    - **Security** : Contains security-related classes for the framework.
    - **Auth** : Authentication related classes.
    - **Checksum** : Checksum calculation classes.
    - **Client** : Client-related classes.
    - **Cryptography** : Cryptography classes.
    - **Detection** : Detection classes.
    - **Logging** : Logging classes.
    - **Monitoring** : Monitoring classes.
    - **Server** : Server-related classes.
    - **Storage** : Storage-related classes, including backup, caching, and filesystem classes.
    - **Templating** : Contains templating-related classes.

7. **Utils** : Contains utility classes used throughout the framework.
    - **Annotations** : Classes related to annotations used in the framework.
    - **API** : API-related classes.
    - **Assets** : Asset management classes.
    - **Controller** : Controller-related classes.
    - **Conversion** : Conversion-related classes.
    - **Data** : Data-related classes.
    - **ErrorManagement** : Error management classes.
    - **HTTP** : HTTP-related classes.
    - **Manipulator** : Manipulation-related classes.
    - **Math** : Math-related classes.
    - **Navigation** : Navigation-related classes, including router classes.
    - **Performance** : Performance-related classes, including benchmarking and threading.
    - **Randomization** : Randomization classes.
    - **SessionManagement** : Classes for managing sessions.
    - **Tracking** : Tracking-related classes.
    - **Validation** : Validation classes.
    - **Versioning** : Versioning-related classes.
    - **Webhook** : Webhook-related classes.
    - **plugins** : Contains plugin classes for the framework.
    - **Discord** : Contains plugin classes for the Discord plugin.
7. **storage** : Contains various types of storage for the application.
    - **assets** : Stores assets, including audio, CSS, favicons, fonts, images, JavaScript, media, and plugin assets.
    - **certs** : Holds certificate files.
    - **json** : Contains JSON files.

8. **vendor** : Contains third-party dependencies installed via Composer.

This directory structure is designed to provide a clear organization of the **NexusPHP** framework components, making it easier to manage and maintain the application. The separation of core components, middleware, controllers, views, and plugins ensures that the application remains modular and scalable.
