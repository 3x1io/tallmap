# PS1 [Livewire]

We will start by learning about Livewire so please before starting check the [docs](https://laravel-livewire.com/docs/2.x/quickstart) of Livewire

## Create Laravel Project

we will start by create a new laravel 9 project

```bash
composer create-project laravel/laravel livewireps1
```

## Link Project With Valet

let's edit our `.env` file and migrate our database

```bash
cd liveireps1
```

link your project with `.test` domain using `valet`

```bash
valet link
```

now let's add SSL to it

```bash
valet secure
```

create database using `valet` or using `phpmyadmin`

```bash
valet db:create livewireps1
```

```bash
nano .env
```

edit .env data `APP_URL`, `DATABASE`

```bash
php artisan config:cache
```

```bash
php artisan migrate
```

## Create GitHub Repo

let's now create a github repo to save and push our works in project

```bash
git init
```

```bash
git add .
```

```bash
git commit -m "first commit"
```

```bash
git branch -M main
```

let's add a remote where `3x1io` is your GitHub username and `livewireps1.git` is your repo name

```bash
git remote add origin git@github.com:3x1io/livewireps1.git
```

now let's make a first push

```bash
git push -u origin main
```

## Install Livewire

now let's start by install livewire package

```bash
composer require livewire/livewire
```

## Install Frontend UI

to start working with livewire we need to install css lib and js lib to add style and action for livewire components, so let's start by creating this frontend preset as a TALL stack.

```bash
yarn
```

```bash
yarn add tailwindcss postcss autoprefixer alpinejs
```

```bash
npx tailwindcss init
```

now let's edit `webpack.mix.js` and add config for tailwind

```js
mix.js("resources/js/app.js", "public/js")
  .postCss("resources/css/app.css", "public/css", [
    require("tailwindcss"),
]);
```

edit `tailwind.config.js` and select the content that tailwind will use

```js
module.exports = {
  content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./resources/**/*.vue",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

go to path `resources/css/app.css` and add

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

go to path `resources/js/app.js` and add

```js
import Alpine from 'alpinejs'
 
window.Alpine = Alpine
 
Alpine.start()
```

now we have tailwindCSS and alpineJs installed using laravel mix

now let's run watcher to make our app.js and app.css updated when we make any change

```bash
yarn watch
```

## Config Livewire

livewire working with frontend by `PHP` using `BLADE` template so we need to know about `BLADE` so let's start by create a `BLADE` layout and some pages and know some basics of it

to add livewire scripts and laravel mix scripts we will use

let's start by creating our frontend `BLADE` schema, go to `resources/views` and create a new folder `layouts`

```bash
cd resources/views
```

```bash
mkdir layouts
```

and inside this folder let's create some files

```bash
touch app.blade.php
```

create a componets of layout, inside layouts folder let's create another folder `includes`

```bash
mkdir includes
```

```bash
cd includes
```

let's create some components inside it

```bash
touch header.blade.php footer.blade.php js.blade.php css.blade.php
```

let's go back and edit our `app.blade.php`

```bash
cd ..
```

you can edit it on your fav editor we will use here `VSCode` go to main directory of project and use

```bash
code .
```

this command use to open the current folder on VSCode Editor

please review `BLADE` templates [docs](https://laravel.com/docs/9.x/blade) before start this step

edit `app.blade.php` to be like this

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>@yiled('title')</title>
    <link rel="stylesheet" href="{{ mix('css/app.css') }}">
    @include('layouts.includes.css')
    @livewireStyles
    @stack('css')
    
</head>
<body>
    @include('layouts.includes.header')
    @yield('body')
    @include('layouts.includes.footer')
    <script src="{{ mix('js/app.js') }}"></script>
    @include('layouts.includes.js')
    @livewireScripts
    @stack('js')
</body>
</html>
```

we will use this layout for any page we will create

## Create Livewire component for Menu

let's start building our first component using this command

```bash
php artisan make:livewire Header
```

this command will create a component inside `app\Http\Livewire` and add a view to `resources/views/livewire` the component will take a name of `Header.php` , `header.blade.php`

now we will use tailwind UI kit for menu style i use [hyperui](https://www.hyperui.dev/) for this task

go to `resources/views/livewire/header.blade.php` and add this code to it

```html
<header class="shadow-sm">
  <div class="max-w-screen-xl p-4 mx-auto">
    <div class="flex items-center justify-between space-x-4 lg:space-x-10">
      <div class="flex lg:w-0 lg:flex-1">
        <span class="w-20 h-10 bg-gray-200 rounded-lg"></span>
      </div>

      <nav class="hidden space-x-8 text-sm font-medium md:flex">
        <a class="text-gray-500" href="">About</a>
        <a class="text-gray-500" href="">Blog</a>
        <a class="text-gray-500" href="">Projects</a>
        <a class="text-gray-500" href="">Contact</a>
      </nav>

      <div class="items-center justify-end flex-1 hidden space-x-4 sm:flex">
        <a
          class="px-5 py-2 text-sm font-medium text-gray-500 bg-gray-100 rounded-lg"
          href=""
        >
          Log in
        </a>

        <a
          class="px-5 py-2 text-sm font-medium text-white bg-blue-600 rounded-lg"
          href=""
        >
          Sign up
        </a>
      </div>

      <div class="lg:hidden">
        <button class="p-2 text-gray-600 bg-gray-100 rounded-lg" type="button">
          <span class="sr-only">Open menu</span>
          <svg
            aria-hidden="true"
            class="w-5 h-5"
            fill="none"
            stroke="currentColor"
            viewbox="0 0 24 24"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M4 6h16M4 12h16M4 18h16"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
            />
          </svg>
        </button>
      </div>
    </div>
  </div>
</header>
```

we need to load a menu from livewire component and loop on it so let's go to `app\Http\Livewire\Header.php` and add a `public` array to set the menu on it

```php
public array $menu;
```

let's create a `mount()` fn to set the `$menu` item inside the component

```php
public function mount()
{
    $this->menus = [
        [
            "title" => "Home",
            "url" => url('/'),
        ],
        [
            "title" => "About",
            "url" => url('/about'),
        ],
        [
            "title" => "Blog",
            "url" => url('/blog'),
        ],
        [
            "title" => "Contact",
            "url" => url('/contact'),
        ]
    ];
}
```

now to have `$menu` array that contents our menu we can access it on the component view by using easy `$menu`

go to `resources/views/livewire/header.blade.php` and create a loop for menu

```blade
@if(isset($menu) && count($menu))
    @foreach($menu as $item)
        <a class="text-gray-500" href="{{ $item['url'] }}">{{ $item['title'] }}</a>
    @endforeach
@endif
```

now we can see that we are create a menu form livewire component but it's still not appear on our project so let's add it on our project

go to `resources/views/layouts/includes/header.blade.php` add add this tag

```blade
<livewire:header />
```

and you will see that you have a menu on the top of your app

you can pass the data to this component using easy livewire selector to access `public` var

```blade
<livewire:header :menu="{{ $anotherMenu }}"/>
```

that will set the menu with custome one you send it on the view