# Start Build you APIs

we are using Laravel Sanctum to handle API Tokens so you can review the packages before starting using this section.

we use an package to generate the APIs form the Table Directly, so let's start by install it with composer

```bash
composer require infyomlabs/laravel-generator
composer require infyomlabs/adminlte-templates
php artisan vendor:publish --provider="InfyOm\Generator\InfyOmGeneratorServiceProvider"
php artisan infyom:publish
```

you can now generate your API with just using this command

```bash
php artisan infyom:api Customer
```

when customer is a Model name
