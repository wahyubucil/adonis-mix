# adonis-mix
> Laravel Mix for AdonisJS

![NPM Badge](https://img.shields.io/npm/v/adonis-mix.svg?style=flat-square)

Adonis Mix is assets bundler your AdonisJs application.

It's based on [Laravel Mix](https://laravel-mix.com/) which is a super easy tool to configure `webpack`.

## Getting Started

This package should be installed with the Adonis CLI.

```shell
$ adonis install adonis-mix
```

Then register the Service Provider within your `start/app.js` file.

```js
const providers = [
  'adonis-mix/providers/AssetsProvider',
]
```

You are now ready to go!

## Bundle the assets

On installation `adonis-mix` copies `webpack.mix.js` configuration file to the project's root folder. See [Laravel Mix Documentation](https://laravel-mix.com/docs/5.0/installation) on how to setup your assets.

After creating your assets in the way you want (Less, SCSS, Stylus, ES2015, ...) you simply need to run the command below and the magic will happen.

```shell
$ adonis assets
# adonis assets --watch -> Watch for change
# adonis assets --production -> Minify for production
```

Laravel Mix will automatically download packages you need to compiles your assets and will then run them.

## Config

The config file is [Laravel Mix](https://laravel-mix.com/docs/5.0/installation) `webpack.mix.js` file.

### Example configuration

For simple AdonisJS project you can use following configuration

```js
const mix = require('laravel-mix')

mix.setPublicPath('public')

mix
  .js('resources/assets/js/app.js', 'public/js')
  .sass('resources/assets/scss/app.scss', 'public/css')
```

Add these to `webpack.mix.js` file in project's root.

## Hot Module Replacement

Read [Laravel Mix instructions](https://laravel-mix.com/docs/5.0/hot-module-replacement) about HMR.

You can add script to your `package.json`

```json
...
"scripts": {
  ...
  "hot": "webpack-dev-server --inline --hot --config=node_modules/laravel-mix/setup/webpack.config.js"
  ...
}
...
```

And run dev server with

```shell
npm run hot
```

## View Helper

Also this package adds `mix` view helper, that parses `mix-manifest.json` file to generate urls to assets.

```html
...
<head>
  {{ style(mix('css/app.css')) }} 
  {{ script(mix('js/app.js)) }}
</head>
...
```
