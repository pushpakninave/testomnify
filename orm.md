# ORM in Laravel Documentation

## Introduction
Eloquent is an (ORM) tool in laravel. ORM is object relational mapping used as a bridge to simplify interaction between object oriented programs and relational-DBs. When using Eloquent, each database table has a corresponding "Model" that is used to interact with that table. In addition to retrieving records from the database table, Eloquent models allow you to insert, update, and delete records from the table as well.

### model class
Models typically live in the `app\Models` directory and extends the `Illuminate\Database\Eloquent\Model` class.

### creating model class
using the Artisan command to generate new model.
`php artisan make:model Flight`

### Eloquent model conventions
By convention, the "snake case", plural name of the class will be used as the table name unless another name is explicitly specified. So, in this case, Eloquent will assume the Flight model stores records in the flights table, while an `AirTrafficController` model would store records in an `air_traffic_controllers` table.
have a look at below example
```php
namespace App\Models;
use Illuminate\Database\Eloquent\Model;
class Flight extends Model
{
    // ...
} 
```

### Defining Primary Keys
Eloquent will also assume that each model's corresponding database table has a primary key column named `id`.
Defining a protected `$primaryKey` property on `Flight`. 
```php
namespace App\Models;
use Illuminate\Database\Eloquent\Model;
class Flight extends Model{
    /**
     * The primary key associated with the table.
     *
     * @var string
     */
    protected $primaryKey = 'flight_id';
    /**
     * by default the id is set to increment in an integral manner.
     * Indicates if the model's ID is auto-incrementing.
     * 
     * @var bool
     */
    public $incremeting = false;
}
```

### Connecting DB
By default all Eloquent models use default db connection that is configured by the application.
Defining custom configuration for connecting database by `$connection` property on the model.
```php
namespace App\Models;
use Illuminate\Database\Eloquent\Model;
class Flight extends Model{
    /**
     * the db connection used by model.
     * 
     * @var string 
     */
    protected $connection = 'sqlite';
}
```
### Defining attributes
By default the newly instantiated model instance will not contain any attribute. But for custom attributes we can use `$attributes` property.
usecase:
```php
namespace App\models;
use Illuminate\Database\Eloquent\Model;
class Flight extends Model{
    /**
     * custom attributes with default values.
     * 
     * @var array
    */
    protected $attributes = [
        'options' => '[]',
        'delayed' => false,
    ]
}
```
