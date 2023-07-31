# NexusPHP Route Parameters

In NexusPHP, the Router component is responsible for handling route parameters, allowing you to define dynamic routes with placeholders. These placeholders can then be used as arguments in your callback functions to extract data from the URL. This guide will show you how to use route parameters effectively in NexusPHP.

## Adding Routes With Parameters

To define routes with parameters, you can use the `RouteCollection` class provided by NexusPHP. The `add()` method allows you to specify the HTTP method, route pattern with placeholders, callback function, and an optional name and middleware. Here's an example of adding a route with parameters:

```php

use Nxp\Core\Utils\Navigation\Router\RouteCollection;

RouteCollection::add('GET', '/users/:id', function($request, $response, $id) {
    // Your callback logic here
    // $id will contain the value extracted from the URL
});
```

In this example, the route pattern is `/users/:id`, where `:id` is a placeholder that will match any value in the actual URL. The callback function takes the `$id` parameter, which will hold the extracted value.

If you would like to learn more about the adding of routes then visit the [Basic Routing](basic-routing.md) page