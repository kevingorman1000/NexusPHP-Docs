# Basic Routing in NexusPHP

In this document, we will explain the basic routing functionality within the PHP framework using the provided classes: `RouteCollection`, `RouteDispatcher`, and `RouteLoader`.

## Introduction

Routing is the process of determining how an application responds to a client request. It involves defining URL patterns and associating them with corresponding actions or callbacks. The routing system will match incoming URLs to registered routes and execute the associated code.

## Route Collection

The `RouteCollection` class is responsible for storing and managing routes within the PHP framework. It allows adding routes with specific HTTP methods, URL patterns, and associated callbacks.

### Adding a Route

To add a route, use the `add` method:

```php
RouteCollection::add($method, $pattern, $callback, $name = null, $middleware = null);
```

- `$method` (string): The HTTP method (e.g., "GET", "POST", "PUT", "DELETE") for this route.
- `$pattern` (string): The URL pattern to match. It may contain parameters like `:param` and wildcards like `*`.
- `$callback` (mixed): The callback or action to execute when the route is matched.
- `$name` (string|null): Optional. The name of the route to be used for generating URLs.
- `$middleware` (array|null): Optional. An array of middleware classes to run before executing the route callback.

### Grouping Routes

You can group routes under a common URL prefix using the `group` method:

```php

RouteCollection::group($prefix, $routes);
```

- `$prefix` (string): The common URL prefix for the grouped routes.
- `$routes` (array): An array of route definitions to be grouped.

### URL Generation

The `urlFor` method is used for generating URLs based on named routes:

```php

RouteCollection::urlFor($name, $params = array());
```

- `$name` (string): The name of the route for which the URL should be generated.
- `$params` (array): Optional. An associative array of parameters to replace in the URL pattern.

## Route Dispatcher

The `RouteDispatcher` class handles the actual dispatching of the matched route. It takes care of running middleware (if any) and executing the associated callback.

### Dispatching Routes

To dispatch routes, use the `dispatch` method:

```php

RouteDispatcher::dispatch();
```

## Route Loader

The `RouteLoader` class helps in loading route definitions from a file. It includes the routes defined in the specified file.

### Loading Routes

To load routes from a file, use the `load` method:

```php

RouteLoader::load($file);
```

- `$file` (string): The path to the file containing route definitions.

## Example Usage

Let's see an example of how to define routes and their associated actions:

```php

// Define routes in routes.php file
use Nxp\Core\Utils\Navigation\Router\RouteCollection;

RouteCollection::add("GET", "/", "HomeController@index");
RouteCollection::add("GET", "/user/:id", "UserController@show");
RouteCollection::add("POST", "/user", "UserController@store");

// Grouping routes
RouteCollection::group("/admin", [
    ["GET", "/dashboard", "AdminController@dashboard"],
    ["GET", "/users", "AdminController@listUsers"],
]);

// Load the routes from the routes.php file
use Nxp\Core\Utils\Navigation\Router\RouteLoader;

RouteLoader::load("routes.php");
```

In the above example, we have defined three routes using `RouteCollection::add`. We also grouped two routes under the `/admin` prefix using `RouteCollection::group`. These routes will be loaded from the `routes.php` file using `RouteLoader::load`.

When a request comes in, the `RouteDispatcher::dispatch` method will match the requested URL with the defined routes and execute the corresponding action or callback.

That's it! You have now set up basic routing in your PHP framework.

Please note that this is just an overview of basic routing using the provided classes. In a real-world scenario, you would need to integrate these classes with your PHP framework and handle more advanced routing scenarios as per your application's requirements.
