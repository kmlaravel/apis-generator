## Apis Generator
[![License](https://poser.pugx.org/kmlaravel/apis-generator/license)](//packagist.org/packages/kmlaravel/apis-generator)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/kmlaravel/apis-generator/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/kmlaravel/apis-generator/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/kmlaravel/apis-generator/badges/build.png?b=master)](https://scrutinizer-ci.com/g/kmlaravel/apis-generator/build-status/master)
[![Code Intelligence Status](https://scrutinizer-ci.com/g/kmlaravel/apis-generator/badges/code-intelligence.svg?b=master)](https://scrutinizer-ci.com/code-intelligence)
[![Code Quality](https://www.code-inspector.com/project/14583/score/svg)](https://www.code-inspector.com/project/14583/score/svg)
# Notes 
> ### laravel 8 not supported yet !
>
apis generator was developed for [laravel 5.8+](http://laravel.com/) to accelerate your
work by building for you new api just a few clicks .

this package came with base controller which helps to handle some logic and generate response,
we will develop all functions that help developers to reduced development time,
simple interface to manage api creations process and view all api you had made before based on credential json file. 

What this package build ?
-------------------------
this package auto build :
- Model : with fill fillable properties depending on the values you chose.
- Request : with validations rules and handle validation error message.
- Controller : with full crud process based on base controller.
- Resource : to get resources data from model.
- Migration : with auto generate for your database columns.

Features
--------
- Friendly simple interface to create your api with dark mode option using [Darkmode.js](https://github.com/sandoche/Darkmode.js).
- Giving you the choice to choose what to build.
- The large development space in the future update.

Installation
------------
##### 1 - Dependency
The first step is using composer to install the package and automatically update your composer.json file, you can do this by running:

```shell
composer require kmlaravel/apis-generator
```
- #### Laravel uses Package Auto-Discovery, so doesn't require you to manually add the ServiceProvider.
##### 3 - Copy the package providers to your local config with the publish command , this will publish asset and config :
```shell
php artisan vendor:publish --provider="KMLaravel\ApiGenerator\Providers\ApisGeneratorServiceProviders"
```
- #### or you may publish asset and config separately.
##### 3 - Copy the package config to your local config with the publish command:
```shell
php artisan vendor:publish --tag=apis-generator-config
```
In `apis_generator.php` configuration file you can determine the properties of the default values and some behaviors.

##### 4 - Copy the package assets to your local resource views with the publish command:
```shell
php artisan vendor:publish --tag=apis-generator-asset
```

Basic usage
-----------
##### 1 - Load your routes
As we said a little while ago we save your process result in `resource/views/ApiGenerator/credential.josn` 
this file contains an array that in turn contains an objects each one contains controller class name , url , api title , and type for your api .

to run this route we have to add this facade class in your `routes/api.php` file.
```php 
\KMLaravel\ApiGenerator\Facade\KMRoutesFacade::getRoutes();
```
now all your routes load automatically from routes in `credential.json` file.
##### 2 - create your api

you should navigate to `{{ your base url }}/apis-generator/create`.

![create_page](assets/create.png)

##### 3 - view all api you have made
you can navigate to `{{ your base url }}/apis-generator/index`.

![index_page](assets/index.png)

config options
----------------
> ## add middleware to package routes
>
the initial package route middleware is `web`
if you want to add any custom middleware you can do that by add middleware keys in middleware arrays
```php
    /*
    |--------------------------------------------------------------------------
    | package routes middleware
    |--------------------------------------------------------------------------
    |
    | this middleware array if you want to add custom middleware to package route,
    | this is applies to ( /apis-generator/index ) and ( /apis-generator/create ).
    |
    */
    //example
    "middleware" => [
        'admin',
    ],
```
> ## add more database column types
>
you can do that by add the type label to column_type array 

```php
    /*
    |--------------------------------------------------------------------------
    | types of column in database which laravel provider.
    |--------------------------------------------------------------------------
    |
    | the options in database column select in create view,
    | you can added or optimize this columns .
    |
    */
    "column_type" => [
        'text',
        'string',
        ...
    ],
```

Changelog
---------
Please see the [CHANGELOG](https://github.com/kmlaravel/apis-generator/blob/master/CHANGELOG.md) for more information about what has changed or updated or added recently.

Security
--------
If you discover any security related issues, please email them first to karam2mustafa@gmail.com, 
if we do not fix it within a short period of time please open new issue describe your problem. 

Credits
-------
[karam mustafa](https://www.linkedin.com/in/karam2mustafa)
