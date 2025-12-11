# laravel-nginx-mysql-redis_dockercompose

This is sample project for output of time on php website taken from mysql database.

After downloading docker-compose.yml, nginx/, php/, src/ do following steps:

docker-compose up -d
.
.
.
Install default template Laravel project:

docker-compose exec app composer create-project laravel/laravel .
.
.
.
Change data inside src/.env file:

DB_CONNECTION=mysql

DB_HOST=mysql

DB_PORT=3306

DB_DATABASE=laravel

DB_USERNAME=laravel

DB_PASSWORD=laravel

REDIS_HOST=redis
.
.
.
Change data inside routes/web.php file:

use Illuminate\Support\Facades\DB;

use Illuminate\Support\Facades\Route;

Route::get('/', function () {

    $time = DB::selectOne("SELECT NOW() AS time")->time;
    
    return "Current DB time: " . $time;

});
.
.
.
And finally run:

docker-compose up -d
.
.
.
Then, you can enter website: http://localhost:8000
