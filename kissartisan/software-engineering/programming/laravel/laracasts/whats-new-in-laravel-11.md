
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
   - Scheduling now can be put on `console.php` in the `routes.php` file
      - We can call the `Schedule::command(...)->daily()` inside it
      - We can now chain the CRON functions (`daily()`, `weekly()`, etc.) into any commands (e.g. `Artisan::command(...)->weekly()`)
