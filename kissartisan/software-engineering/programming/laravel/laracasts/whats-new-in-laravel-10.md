## [What's new in Laravel 10](https://laracasts.com/series/whats-new-in-laravel-10)?
1. Native Type Declaration
  - Remove all @param declaration on docblock on laravel codebase
  - As it's superflous because method parameters already have typehints
2. Generate Secure Passwords
  - We can now use `Illuminate\Support\Str::password()` or the string helper equivalent: `str()->password()`
3. Quicker Project Scaffolding
  - Pest scaffolding using `--pest` flag 
  - Breeze scaffolding using `--breeze` flag
4. The New `Process` Facade

```
Laravel 10 ships with a new Process facade. This facade, built on top of Symfony's excellent Process component, allows you to easily invoke and execute shell commands, and even run them asynchronously in the background.
```
5. [Laravel Pennant](https://laravel.com/docs/10.x/pennant) - feature flagging
  - First party lightweight feature flag functionality of Laravel
  - Will create a `features` table
  - Can use using `@feature` blade component
