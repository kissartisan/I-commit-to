
## [What's new in Laravel 11](https://laracasts.com/series/whats-new-in-laravel-11)?

### 1. Fewer Config Files
   - Slimmed down the `config` directory
   - They been pulled down into the Laravel framework and at and any point we can bring them back to make changes as and when required
   - Run `php artisan config:publish` to see all of the config files that are available for us to publish
   - When we make our own service provider (e.g. `php artisan make:provider TestingServiceProvider`), Laravel now auto registers our created service provider
     - On top of this change, `app.php` has no `providers` array key anymore
     - The provider registrations are now relocated to `bootstrap/providers.php`
   
### 2. Missing Middleware
   - All of the files on `app/Http/Middleware` are gone and it's been moved down into the Laravel framework
   - We can add our changes on the existing middlewares on `Providers/AppServiceProvider.php` > `boot()` method
   - For example, if we want to exclude a string on `TrimStrings` middleware, we can use `TrimString:except(['string_to_be_exempted'])` so `"string_to_be_exempted"` won't run on the existing `TrimStrings` middleware
