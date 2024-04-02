
## [What's new in Laravel 11](https://laracasts.com/series/whats-new-in-laravel-11)?

### 1. [Fewer Config Files](https://laracasts.com/series/whats-new-in-laravel-11/episodes/1)
   - Slimmed down the `config` directory
   - They been pulled down into the Laravel framework and at and any point we can bring them back to make changes as and when required
   - Run `php artisan config:publish` to see all of the config files that are available for us to publish
   - When we make our own service provider (e.g. `php artisan make:provider TestingServiceProvider`), Laravel now auto registers our created service provider
     - On top of this change, `app.php` has no `providers` array key anymore
     - The provider registrations are now relocated to `bootstrap/providers.php`
   
### 2. [Missing Middleware](https://laracasts.com/series/whats-new-in-laravel-11/episodes/2)
   - `app/Http/Middleware` is now an empty directory as the default files has been moved down into the Laravel framework
   - We can add our changes on the built-in middlewares on `Providers/AppServiceProvider.php` > `boot()` method
   - For example, if we want to exclude a string on `TrimStrings` middleware, we can use `TrimString:except(['string_to_be_exempted'])` so `"string_to_be_exempted"` won't run on the existing `TrimStrings` middleware
   - Another example is the built-in middleware called `RedirectIfAuthenticated` where we use to redirect the user to a specific location
     - On Laravel 11, we can use `RedirectIfAuthenticated::redirectUsing(fn ($request) => route('any_route_you_want'))` code to redirect them wherever we want
   - Custom middlewares will still live in `app/Http/Middleware` directory
   - There's also no `Kernel.php` in the application level in Laravel 11
   - We now register custom middlewares on `bootstrap/app.php` > in `withMiddleware() {}` function
      - e.g. `$middleware->web(MyCustomMiddleWare::class);`
- `ExceptionHandler` is also gone on Laravel 11
      -  Customizing exceptions are also available `bootstrap/app.php` > `withExceptions {}` function

### 3. [Streamlined Scheduling](https://laracasts.com/series/whats-new-in-laravel-11/episodes/3)
   - There's no `kernel.php` in the Laravel 11 skeleton
   - Scheduling can now be put on `console.php` in the `/routes` directory
   - There's a new `Schedule` facade that's been added
      - We can call it like so `Schedule::command(...)->daily()`
   - We can now also chain CRON functions (`daily()`, `weekly()`, etc.) into any commands (e.g. `Artisan::command(...)->weekly()`)

### 4. [Installing an API](https://laracasts.com/series/whats-new-in-laravel-11/episodes/4)
   - There's no `api.php` file on `/routes` directory but we can easily scaffold it using a single command
      - `php artisan install:api` - when running this command you can also see info warnings in your terminal that you may need to follow as well
   - There's also no broadcasting by default but we can scaffold it using a single command
      - `php artisan install:broadcasting`
        
### 5. [Sqlite Out of the Box](https://laracasts.com/series/whats-new-in-laravel-11/episodes/5)
   - Whenever you create a Laravel project using composer, when the application is constructed, it's actually going to install a `SQLite` database for us during installation and it will migrate the database right of the bat
   - To change that default behavior, go in `.env` file and change `DB_CONNECTION` value to your needs (e.g. `MySQL`)

### 6. The Dumpable Trait
      - On the previous Laravel versions, we already have the capability to chain `->dump()` or `->dd()` on Eloquent models and internal Laravel classes. 
      - But now, using the `Dumpable` trait we can now also chain it on our own classes
