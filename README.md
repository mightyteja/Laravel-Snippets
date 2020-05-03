# 100 (and counting) Laravel Quick Tips!
Prepared by: **Povilas Korop / LaravelDaily Team**
Last updated: **April 2020**


# Intro
| # | Tip Name |
|--|--|
| 1 |  [Single Action Controllers](#Single-Action-Controllers)|
| 2 |  Single Action Controllers|

## Single Action Controllers

If you want to create a controller with just one action, you can use ``__invoke()`` method and even create *"invokable"* controller. 

##### Controller

```

   <?php
namespace App\Http\Controllers;
use App\User;
use App\Http\Controllers\Controller;
class ShowProfile extends Controller
{
/**
* Show the profile for the given user.
*
* @param int $id
* @return Response
*/
public function __invoke($id)
{
return view('user.profile', ['user' => User::findOrFail($id)]);
}
}

```

##### Routes: 

    Route::get('user/{id}', 'ShowProfile'); 

Artisan command to generate this controller:

     php artisan make:controller ShowProfile --invokable





