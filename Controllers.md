# Laravel Controller Documentation

## Introduction
Laravel, is a PHP web application framework, utilizes Middleware and Controllers to handle HTTP requests and responses. Allowing you to process requests before they reach the application's core, while Controllers manage the application logic and respond to user actions.

# Controllers 
Controllers manage the application's HTTP request handling. It basically make further decisions as per the response. Controllers can group related handling logic into a single class. 
example...
>a `UserController` class might handle all incoming requests related to users, including showing, creating, updating and deleting users. By default controllers are stored in the `app/Http/Controllers` directory
Here are key concepts and usage examples:

### Creating Controllers
Generate a new controller class with 
`php artisan make:controller`

### Defining Controller
```php
    namespace App/Http/Controllers;
    use App/Models/User;
    use Illuminate/View/View;

    class UserController extends Controller{

        /**
         * show profile for given user.
        */
        public function show(string $id): View{
            return view('user.profile', [
                'user'=> User::findOrFail($id)
            ]);
        }
    }
```

### Defining route to controller method
```php
use App/Http/Controller/UserController;
Route::get('/user/{id}', [UserController::class, 'show']);
```
when an incoming request matches the specified route URI, the `show` method on the `use App\Http\Controllers\UserController` class will be invoked and the route param will be passed to the method.


### Controller Middleware
Middleware may be assigned to the controller's routes in our routes files:
```php
Route::get('profile', [UserController::class, 'show'])->middleware('auth');
```
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