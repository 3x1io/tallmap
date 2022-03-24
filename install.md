# Install Laravel & TALL Stack Packages

we now have a good env to start building our app, so let's start by setup Laravel v9 on our PC

```bash
cd Sites
```

let's now go and create a new project inside the Sites directory

```bash
composer create-project laravel/laravel tall-app
```

now we need to create a new database for the new project let's do that by using valet+

```bash
now we need to create a new database for the new project let's do that by using valet+
```

it's working now we have a new database you can check it in your phpmyadmin, now let's link and secure the app

```bash
valet link
valet secure
```

the last step to run the project is to edit your .env file with the database info and APP_URL.

```dotenv
APP_NAME=3x1
APP_URL=https://3x1.test
APP_DOMAIN=3x1.test
DB_DATABASE=3x1
DB_USERNAME=root
DB_PASSWORD=3x1
```

Clear cache to reset .env vars

```bash
php artisan config:cache
php artisan migrate
```

## Install packages

first of all let's install filament admin

```bash
composer require filament/filament
```

after install to access the admin panel you need to create a user using this command

```bash
php artisan make:filament-user
```

run this command to publish config files

```bash
php artisan vendor:publish --tag=filament-config
php artisan vendor:publish --tag=filament-translations
```

go to app/Http and create a new folder

```bash
mkdir Livewire
```

now use this command every time you need to update the package

```bash
php artisan filament:upgrade
```

now you have filament ready to use go to URL/admin and login with the user and you will get the dashboard worked.

## Awesome Plugins for filament

he is some awesome packages you muse use for filament

- [Filament Spatie Laravel Media Library](https://filamentphp.com/docs/2.x/spatie-laravel-media-library-plugin/installation)
- [Filament Setting](https://filamentphp.com/docs/2.x/spatie-laravel-settings-plugin/installation)
- [Filament Tags](https://filamentphp.com/docs/2.x/spatie-laravel-tags-plugin/installation)
- [Filament Translatable](https://filamentphp.com/docs/2.x/spatie-laravel-translatable-plugin/installation)
- [Filament Excel](https://github.com/pxlrbt/filament-excel)
- [Filament Themes](https://github.com/3x1io/filament-themes)
- [Filament Translations](https://github.com/3x1io/filament-translations)
- [Filament User](https://github.com/3x1io/filament-user)
- [Filament Shield](https://github.com/bezhansalleh/filament-shield)
- [Filament Log Viewer](https://github.com/rabol/filament-logviewer)
- [Filament Tools](https://github.com/ryangjchandler/filament-tools)
- [Filament Backup](https://github.com/shuvroroy/filament-spatie-laravel-backup)
- [Filament Forms TinyEditor](https://github.com/mohamedsabil83/filament-forms-tinyeditor)
- [Laravel Fortify](https://github.com/wychoong/filament-fortify)
- [Filament Google Analytics](https://github.com/bezhanSalleh/filament-google-analytics)
- [Filament Impersonate](https://github.com/stechstudio/filament-impersonate)
