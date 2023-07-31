# Route Grouping in NexusPHP

In NexusPHP, route grouping allows you to group related routes under a common URL prefix, apply middleware to the grouped routes, and make the route organization more structured. This feature enhances code maintainability and readability in larger applications. Let's explore how to use route grouping in NexusPHP.
## Introduction

NexusPHP provides a routing system based on the `RouteCollection` class, which allows you to define routes and group them under a common URL prefix using the `group` method. By grouping routes, you can logically organize routes that share a common URL segment or functionality.
## Route Grouping

To group routes in NexusPHP, use the `group` method in the `RouteCollection` class:

```php
use Nxp\Core\Utils\Navigation\Router\RouteCollection;

RouteCollection::group($prefix, $routes);
```

 
- `$prefix` (string): The common URL prefix for the grouped routes. 
- `$routes` (array): An array of route definitions to be grouped.
## Example Usage

Let's see an example of how to use route grouping in NexusPHP:

```php
use Nxp\Core\Utils\Navigation\Router\RouteCollection;

// Grouping routes under the /user URL prefix
RouteCollection::group('/user', [
    ['GET', '/', '\Nxp\Controllers\User\UserController@index'],
    ['GET', '/profile', '\Nxp\Controllers\User\UserController@profile'],
    ['POST', '/update', '\Nxp\Controllers\User\UserController@updateProfile'],
]);

// Grouping routes under the /admin URL prefix
RouteCollection::group('/admin', [
    ['GET', '/', '\Nxp\Controllers\Admin\AdminController@index'],
    ['GET', '/dashboard', '\Nxp\Controllers\Admin\AdminController@dashboard'],
    ['POST', '/settings', '\Nxp\Controllers\Admin\AdminController@updateSettings'],
]);
```

In the example above, we have grouped user-related routes under the `/user` prefix and admin-related routes under the `/admin` prefix.

When a request is made to an URL like `/user/profile`, NexusPHP will look for the corresponding route in the grouped routes under the `/user` prefix and execute the associated action or callback.
## Benefits of Route Grouping

Route grouping in NexusPHP offers several advantages: 
1. **Organization** : Grouping related routes under a common prefix helps you organize the routes more logically. This makes the codebase cleaner and easier to understand. 
2. **Middleware Application** : By using route grouping, you can apply middleware specifically to the grouped routes. Middleware allows you to perform pre- and post-processing tasks on the request and response, such as authentication, validation, or logging. 
3. **Route Prefixing** : Grouping routes under a common prefix allows you to easily change the URL structure of the grouped routes by modifying the prefix at a single location. 
4. **Code Reusability** : If you have routes with similar functionality, grouping them allows you to reuse the same middleware and callbacks for multiple routes.
## Conclusion

Route grouping is a powerful feature in NexusPHP that helps you organize routes, apply middleware to specific sets of routes, and enhance code maintainability and reusability. By grouping related routes under a common URL prefix, you can create a structured and well-organized routing system that improves the overall quality of your NexusPHP application.
