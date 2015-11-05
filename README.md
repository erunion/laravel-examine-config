# Laravel Examine Config

Adds a `config:examine` command to Laravel Artisan that lets you examine your configured environment.

## Installation

### 1. Install with Composer
```bash
composer require --dev erunion/laravel-examine-config
```

### 2. Add to `app/config/app.php`
```
    'providers' => array(
        // ...
        Erunion\Providers\ExamineConfigServiceProvider::class,
    ),
```

This registers the Artisan command with Laravel.

## Usage
### Show your entire config

```
$ php artisan config:examine
Configuration: app
+----------+----------+-------------------------------------+
| aliases  |          |                                     |
|          | App      | Illuminate\Support\Facades\App      |
|          | Artisan  | Illuminate\Support\Facades\Artisan  |
…
+----------+----------+-------------------------------------+
Configuration: auth
+----------+----------+-----------------+
| driver   | eloquent |                 |
| model    | App\User |                 |
| password |          |                 |
|          | email    | emails.password |
|          | expire   | 60              |
|          | table    | password_resets |
| table    | users    |                 |
+----------+----------+-----------------+
...
Configuration: view
+----------+----------------------------------------+--------------------------------+
| compiled | /home/site/web/storage/framework/views |                                |
| paths    |                                        |                                |
|          | 0                                      | /home/site/web/resources/views |
+----------+----------------------------------------+--------------------------------+
```

### Show your `app` config
```
$ php artisan config:examine app
Configuration: app
+----------------------+------------------------------------+---------------------------------------------------------------+
| aliases              |                                    |                                                               |
|                      | App                                | Illuminate\Support\Facades\App                                |
|                      | Artisan                            | Illuminate\Support\Facades\Artisan                            |
|                      | Auth                               | Illuminate\Support\Facades\Auth                               |
|                      | Blade                              | Illuminate\Support\Facades\Blade                              |
|                      | Bus                                | Illuminate\Support\Facades\Bus                                |
|                      | Cache                              | Illuminate\Support\Facades\Cache                              |
|                      | Config                             | Illuminate\Support\Facades\Config                             |
|                      | Cookie                             | Illuminate\Support\Facades\Cookie                             |
|                      | Crypt                              | Illuminate\Support\Facades\Crypt                              |
|                      | DB                                 | Illuminate\Support\Facades\DB                                 |
|                      | Eloquent                           | Illuminate\Database\Eloquent\Model                            |
|                      | Event                              | Illuminate\Support\Facades\Event                              |
|                      | File                               | Illuminate\Support\Facades\File                               |
|                      | Hash                               | Illuminate\Support\Facades\Hash                               |
|                      | Input                              | Illuminate\Support\Facades\Input                              |
|                      | Lang                               | Illuminate\Support\Facades\Lang                               |
|                      | Log                                | Illuminate\Support\Facades\Log                                |
|                      | Password                           | Illuminate\Support\Facades\Password                           |
|                      | Redirect                           | Illuminate\Support\Facades\Redirect                           |
|                      | Request                            | Illuminate\Support\Facades\Request                            |
|                      | Response                           | Illuminate\Support\Facades\Response                           |
|                      | Route                              | Illuminate\Support\Facades\Route                              |
|                      | Schema                             | Illuminate\Support\Facades\Schema                             |
|                      | Session                            | Illuminate\Support\Facades\Session                            |
|                      | Storage                            | Illuminate\Support\Facades\Storage                            |
|                      | URL                                | Illuminate\Support\Facades\URL                                |
|                      | Validator                          | Illuminate\Support\Facades\Validator                          |
|                      | View                               | Illuminate\Support\Facades\View                               |
| cipher               | rijndael-128                       |                                                               |
| cookie_domain        | localhost                          |                                                               |
| debug                | true                               |                                                               |
| fallback_locale      | en                                 |                                                               |
| key                  | W4ZQxqTlGycvzKYZFyGi8WJa4ki1bhNO   |                                                               |
| locale               | en                                 |                                                               |
| log                  | daily                              |                                                               |
| name                 | My Site!                           |                                                               |
| providers            |                                    |                                                               |
|                      | 0                                  | Illuminate\Foundation\Providers\ArtisanServiceProvider        |
|                      | 1                                  | Illuminate\Auth\AuthServiceProvider                           |
|                      | 2                                  | Illuminate\Broadcasting\BroadcastServiceProvider              |
|                      | 3                                  | Illuminate\Bus\BusServiceProvider                             |
|                      | 4                                  | Illuminate\Cache\CacheServiceProvider                         |
|                      | 5                                  | Illuminate\Foundation\Providers\ConsoleSupportServiceProvider |
|                      | 6                                  | Illuminate\Routing\ControllerServiceProvider                  |
|                      | 7                                  | Illuminate\Cookie\CookieServiceProvider                       |
|                      | 8                                  | Illuminate\Database\DatabaseServiceProvider                   |
|                      | 9                                  | Illuminate\Encryption\EncryptionServiceProvider               |
|                      | 10                                 | Illuminate\Filesystem\FilesystemServiceProvider               |
|                      | 11                                 | Illuminate\Foundation\Providers\FoundationServiceProvider     |
|                      | 12                                 | Illuminate\Hashing\HashServiceProvider                        |
|                      | 13                                 | Illuminate\Pipeline\PipelineServiceProvider                   |
|                      | 14                                 | Illuminate\Auth\Passwords\PasswordResetServiceProvider        |
|                      | 15                                 | Illuminate\Session\SessionServiceProvider                     |
|                      | 16                                 | Illuminate\Translation\TranslationServiceProvider             |
|                      | 17                                 | Illuminate\Validation\ValidationServiceProvider               |
|                      | 18                                 | Illuminate\View\ViewServiceProvider                           |
|                      | 19                                 | Erunion\Providers\ExamineConfigServiceProvider                |
| timezone             | America/New_York                   |                                                               |
| url                  | http://localhost                   |                                                               |
+----------------------+------------------------------------+---------------------------------------------------------------+
```

### Show your configured `app.timezone`
```
$ php artisan config:examine app.timezone
America/New_York
```

## Changelog
### 1.1.0
* Fixing a bug where trying to pull configured strings (like `app.timezone`) would fail because it wasn't an array, and
couldn't be tableized.

### 1.0.0
* Initial release

## License
MIT
