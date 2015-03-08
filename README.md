# HTMLPurifier for Laravel 4

A simple [Laravel 5](http://laravel.com/) service provider for including the [HTMLPurifier for Laravel 5](https://github.com/mewebstudio/purifier).

## Installation

The HTMLPurifier Service Provider can be installed via [Composer](http://getcomposer.org) by requiring the
`ezyang/htmlpurifier`, `mews/purifier` package and setting the `minimum-stability` to `dev` (required for Laravel 5) in your
project's `composer.json`.

```json
{
    "require": {
        "laravel/framework": "~5.0",
        "mews/purifier": "dev-master"
    },
    "minimum-stability": "dev"
}
```

Update your packages with ```composer update``` or install with ```composer install```.

## Usage

To use the HTMLPurifier Service Provider, you must register the provider when bootstrapping your Laravel application. There are
essentially two ways to do this.

Find the `providers` key in `app/config/app.php` and register the HTMLPurifier Service Provider.

```php
    'providers' => array(
        // ...
        'Mews\Purifier\PurifierServiceProvider',
    )
```

Find the `aliases` key in `app/config/app.php`.

```php
    'aliases' => array(
        // ...
        'Purifier' => 'Mews\Purifier\Facades\Purifier',
    )
```

## Configuration

To use your own settings, you can publish configuration file to your application's config directory by running

```$ php artisan vendor:publish```

Make sure that you have added Purifier service provider before you have executed vendor:publish command.

Example config file `app/config/purifier.php`

```php
return array(
    'encoding' => 'UTF-8',
    'finalize' => true,
    'preload'  => false,
    'settings' => array(
        'default' => array(
            'HTML.Doctype'             => 'XHTML 1.0 Strict',
            'HTML.Allowed'             => 'div,b,strong,i,em,a[href|title],ul,ol,li,p[style],br,span[style],img[width|height|alt|src]',
            'CSS.AllowedProperties'    => 'font,font-size,font-weight,font-style,font-family,text-decoration,padding-left,color,background-color,text-align',
            'AutoFormat.AutoParagraph' => true,
            'AutoFormat.RemoveEmpty'   => true,
        ),
        "titles" => array(
            'AutoFormat.AutoParagraph' => false,
            'AutoFormat.Linkify' => false,
        )
    ),
);
```

## Example

default
```php

    Purifier::clean(Input::get('inputname'));

```

dynamic config
```php

    Purifier::clean('This is my H1 title', 'titles');
    Purifier::clean('This is my H1 title', array('Attr.EnableID' => true));
```

                      

## Links

* [HTMLPurifier Library website](http://htmlpurifier.org/)

* [L4 HTMLPurifier on Github](https://github.com/mewebstudio/purifier)
* [L4 HTMLPurifier on Packagist](https://packagist.org/packages/mews/purifier)
* [License](http://www.gnu.org/licenses/lgpl-2.1.html)
* [Laravel website](http://laravel.com)
* [Laravel Turkiye website](http://www.laravel.gen.tr)
* [MeWebStudio website](http://www.mewebstudio.com)
