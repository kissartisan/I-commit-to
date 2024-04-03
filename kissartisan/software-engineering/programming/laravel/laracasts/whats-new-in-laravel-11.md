
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

### 6. [The Dumpable Trait](https://laracasts.com/series/whats-new-in-laravel-11/episodes/6)
   - On the previous Laravel versions, we already have the capability to chain `->dump()` or `->dd()` on Eloquent models and internal Laravel classes. 
   - But now, using the `Dumpable` trait we can now also chain it on our own classes
   - Since `Dumpable` is a trait, that means you can also override its existing methods (`dump()`, `dd()` )

### 7. [Limitless Limits for Eager Loading](https://laracasts.com/series/whats-new-in-laravel-11/episodes/7)
   - In Laravel 10, you cannot eager load associated Eloquent models properly while filtering or limiting the data. Example:
     ```
        User::whereHas('posts')
           ->with(['posts' => fn ($query) => $query->latest()->limit(5)])
           ->paginate(5);
     ```
      - That will only grab 5 posts all of the users instead of 5 posts per user
      - This is due to limits in SQL and you have to install a separate package if you want to get around this constraint
   -  In Laravel 11, it's exactly the opposite as it will correctly grab 5 posts per each user
      ```
        User::whereHas('posts')
           ->with(['posts' => fn ($query) => $query->latest()->limit(5)])
           ->paginate(5);
      ```
   - Refactor Tip: You can put that code above into its own relationship:
     ```
        public function latestPosts(): HasMany
        {
           return $this->hasMany(Post::class)->latest()->limit(5);
        }

        // The previous example
        User::whereHas('posts')->with('latestPosts')->paginate(5);
      ```

### 8. [Super Simple Memoization](https://laracasts.com/series/whats-new-in-laravel-11/episodes/8)
   - A new helper called `once()` is introduced in Laravel 11 to only call the logic once if we wrapped it in the `once()` function
   - The only time it will change is when a new request or new set of data comes in
   - A super simple `once()` function that you can use anywhere in the codebase to ensure that no matter how many times you execute that code in the lifecycle of a request, it will only actually perform it once, and then the value will be returned to you.

### 9. [A Minor Tweak to Model Casts](https://laracasts.com/series/whats-new-in-laravel-11/episodes/9)
   - The `$casts` property that Laravel provides us to cast data before we render it is now available as a function (`public function casts() {}`) instead to ensure a better readability and IDE syntax highlighting

### 10. [Per Second Rate Limits](https://laracasts.com/series/whats-new-in-laravel-11/episodes/10)
   - Laravel 11 now includes `perSecond()` on Laravel's rate limiter (Limit class). Previously they only limit the requests using `perMinute()`
