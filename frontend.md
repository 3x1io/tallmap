# Start Building Your Tailwind app

our stack is TALL, so we use for CSS TailwindCSS & for js alpineJs so we now will install these packages inside the laravel app we were created on the last step

let's start by installing TailwindCSS

but before we start we need to install NPM & Yarn

```bash
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo bash -
sudo apt install -y nodejs vim
sudo apt install gcc g++ make
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install yarn
```

now it's installed, let's start to build our frontend assets, first install TailwindCSS

```bash
yarn 
yarn add tailwindcss postcss autoprefixer
npx tailwindcss init
```

the last command will generate tailwind.config.js file on the base project folder you can add tailwind plugins, themes, vars on it, now open the file and change content: with

```js
content: [
    "./resources/**/*.blade.php",
    "./resources/**/*.js",
    "./resources/**/*.vue",
],
```

go to webpack.mix.js file and update it with the content of

```js
mix.js("resources/js/app.js", "public/js")
  .postCss("resources/css/app.css", "public/css", [
    require("tailwindcss"),
  ]);
```

go to resources/css/app.css and add this lines

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

the tailwind is installed now, we will install alpinejs, let's install it first

```bash
yarn add alpinejs
```

now let's add a js to resources/js/app.js, replace all content with 

```js
import Alpine from 'alpinejs'

window.Alpine = Alpine

Alpine.start()
```

the last step is to start the watch, this watch uses laravel mix the mixing your assets into one file you can access this file one `public/css/app.css` and `public/js/app.js`

```bash
yarn watch
```

leave the command run, because it compiles every change you are done on your project

## Start Build Your Theme

you can use the package of Filament Themes to build your theme or use direct blade template of laravel, go-to `resources/views` and create a new folder layout, and on it let's create an app.blade.php layout to be the main layout of our app like the next code

```blade
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="{{ asset('css/app.css') }}" rel="stylesheet">
    <title>@yield('title')</title>
    @livewireStyles
</head>
<body>
    <div class="w-full px-4 py-4">
       @yield('body')
    </div>    
    @livewireScripts
    <script src="{{ mix('js/app.js') }}"></script>
</body>
</html>
```

now you can use tailwind and alpineJs on this page

## Awesome Resources for Tailwind

- [Tailwind Kit](https://www.tailwind-kit.com/)
- [Gust UI](https://www.gustui.com/)
- [Lofi UI](https://lofiui.co/)
- [Merak UI](https://merakiui.com/)
- [Windstrap](https://windstrap.netlify.app/)
- [Tailwind Components](https://tailwindcomponents.com/)
- [Kit Wind](https://kitwind.io/)
- [Tailblocks](https://tailblocks.cc/)
- [Tailwind Toolbox](https://www.tailwindtoolbox.com/)
- [Mamba UI](https://www.mambaui.com/)
- [Kutty](https://kutty.netlify.app/)
- [Daisy UI](https://daisyui.com/)
- [Flowbite](https://flowbite.com/)
- [Tailwind UI Kit](https://tailwinduikit.com/)
- [Hyper UI](https://hyperui.dev/)
- [Post Src](https://postsrc.com/)
- [Tailwind Elements](https://tailwind-elements.com/)
