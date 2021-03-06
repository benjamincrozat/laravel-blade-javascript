# A Blade directive to export variables to JavaScript

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/laravel-blade-javascript.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-blade-javascript)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/laravel-blade-javascript/master.svg?style=flat-square)](https://travis-ci.org/spatie/laravel-blade-javascript)
[![SensioLabsInsight](https://img.shields.io/sensiolabs/i/07458966-b1a2-4cef-8020-02b03f0dd240.svg?style=flat-square)](https://insight.sensiolabs.com/projects/07458966-b1a2-4cef-8020-02b03f0dd240)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/laravel-blade-javascript.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/laravel-blade-javascript)
[![Total Downloads](https://img.shields.io/packagist/dt/spatie/laravel-blade-javascript.svg?style=flat-square)](https://packagist.org/packages/spatie/laravel-blade-javascript)

This package contains a Blade directive to export values to JavaScript.

Here's an example of how it can be used:

```php
@javascript('key', 'value')
```

The rendered view will output:
```html
<script>window['key'] = 'value';</script>
```

So in your browser you now have access to a key variable:
```js
console.log(key); //outputs "value"
```

You can also use a single argument:
```php
@javascript(['key' => 'value'])
```

Which will output the same as the first example.

There also support for namespacing all variables.

Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## Installation

You can install the package via composer:

``` bash
composer require spatie/laravel-blade-javascript
```

Next up, the service provider must be registered:

```php
'providers' => [
    ...
    Spatie\BladeJavaScript\BladeJavaScriptServiceProvider::class,

];
```

Optionally the config file can be published with

```bash
php artisan vendor:publish --provider="Spatie\BladeJavaScript\BladeJavaScriptServiceProvider"
```

This is the contents of the published config file:

```php
return [

    /**
     * All passed values will be present in this JavaScript namespace. Set this to an empty string
     * to use the window object.
     */
    'namespace' => '',
];
```

## Usage

With the package installed you can make use of a `@javascript` Blade directive.

```php
@javascript('key', 'value')
```

The rendered view will output:
```html
<script>key = 'value';</script>
```

You can also use a single argument:
```php
@javascript(['key' => 'value])
```

This will also output:
```html
<script>key = 'value';</script>
```

When setting the namespace to eg `js` in the config file this will be the output:

```html
<script>window['js'] = window['js'] || {};js['key'] = 'value';</script>
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Freek Van der Herten](https://github.com/freekmurze)
- [Sebastian De Deyne](https://github.com/seb)
- [All Contributors](../../contributors)

This repository contains some code from the [laracasts/PHP-Vars-To-Js-Transformer](https://github.com/laracasts/PHP-Vars-To-Js-Transformer) package written by [Jeffrey Way](https://github.com/JeffreyWay).

## About Spatie
Spatie is a webdesign agency based in Antwerp, Belgium. You'll find an overview of all our open source projects [on our website](https://spatie.be/opensource).

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
