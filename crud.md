# Build A TALL stack CRUD Operation

to build a crud resource with TALL stack it's easy using filament, let's start by creating a new migration

```bash
php artisan make:migration create_customers_table
```

edit the schema as you see and make a migrate

```bash
php artisan migrate
```

create all migrations files first because we will generate all models with one command, first let's install this package

```bash
composer require axn/laravel-models-generator
php artisan vendor:publish --tag=models-generator.config
```

after the installation please run this command, and you will get all models of the table generated on your `App/Models` folder

```bash
php artisan models:generate
```

the last command you will use to generate the resource and full CRUD operation is

```bash
php artisan make:filament-resource Customer --generate
```

it will generate a full CRUD operation for Customer Model, if you like to convert form to a modal popup, as a SPA you can use this command

```bash
php artisan make:filament-resource Customer --generate --simple
```

BINGO! you get your first resource on filament you can check out the docs for more info
