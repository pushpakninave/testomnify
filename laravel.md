# Laravel Middleware and Controller Documentation

## Introduction

Laravel, is a PHP web application framework, utilizes Middleware and Controllers to handle HTTP requests and responses. , allowing you to process requests before they reach the application's core, while Controllers manage the application logic and respond to user actions.

# Middleware
Middleware acts as a filter. It is basically a filter for the incoming http requests. Works like request and the actions may be before or after the requests. 
Request here is like a demand or query through HTTP and response accordingly.
It intercepts HTTP requests, enabling you to perform actions before they reach the controller. Here are key concepts and usage examples:
all the middlewares are found in app/Http/middleware

### Middleware Classes

Middleware classes handle requests and responses, performing tasks like authentication and logging.

### Middleware Class creation
`php artisan make : middleware TestMiddleware` 


### Middleware Groups

Grouping middleware simplifies their assignment to routes, improving organization.

### Global Middleware

Runs on every HTTP request, we need to include a middleware class in the $middleware property of your `app/Http/kernel.php`.

### Route Middleware

Assigned to specific routes, defined in `app/Http/Kernel.php`.
example:
```php
use App/Http/Middleware/Authenticate;
Route::get('/profile' , function(){
//...
})-> middleware([Authenticate::class, Auth2::class]);
```

### Usage Example

```php
// Creating Middleware
php artisan make:middleware CustomMiddleware

namespace App\Http\Middleware;
 
use Closure;
use Illuminate\Http\Request;
use Symfony\Component\HttpFoundation\Response;
// Middleware Logic
class EnsureTokenIsValid{
/**
     * Handle an incoming request.
     *
     * @param  \Closure(\Illuminate\Http\Request): (\Symfony\Component\HttpFoundation\Response)  $next
     */
public function handle($request, Closure $next)
{
    

     if ($request->input('token') !== 'my-secret-token') {
            return redirect('home');
        }

    // Perform actions before and after the request is handled by the controller.
    return $next($request);
}
}
// Assigning Middleware
protected $middleware = [
    // ...
    \App\Http\Middleware\CustomMiddleware::class,
];
```
<br/><br/>

# Controller
Controllers manage the application's HTTP request handling. It basically make further decisions as per the response. 
Here are key concepts and usage examples:

### Creating Controllers
Generate a new controller class with 
`php artisan make:controller`

### Controller Methods
Methods handle specific actions, returning responses to users.

### Dependency Injection
Controllers support dependency injection for easy access to services and other dependencies.

### Resource Controllers
Organize controllers and define RESTful routes easily.

### Usage Example:
```php
// Creating a Controller
php artisan make:controller UserController

class ValidTokenAction{
    
// Controller Logic
public function index()
{
    // Logic to display a list of users.
}

// Routing to Controllers
Route::get('/users', 'UserController@index');

// Dependency Injection
public function show(User $user)
{
    // $user is automatically injected based on the route parameter.
}

}
```

<p align="center">
  <img width="500" src="https://github.com/pushpakninave/testomnify/assets/65614791/7f2b16f4-b53d-4631-ab6b-6039fa171d21" alt="Description of the image">
</p>