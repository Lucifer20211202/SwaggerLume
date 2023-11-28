[![Total Downloads](https://poser.pugx.org/DarkaOnLine/swagger-lume/downloads.svg)](https://packagist.org/packages/DarkaOnLine/swagger-lume)
![Build Status](https://github.com/DarkaOnLine/SwaggerLume/actions/workflows/test-config.yml/badge.svg?branch=master)
[![Coverage Status](https://coveralls.io/repos/github/DarkaOnLine/SwaggerLume/badge.svg?branch=master)](https://coveralls.io/github/DarkaOnLine/SwaggerLume?branch=master)
[![Code Climate](https://codeclimate.com/github/DarkaOnLine/SwaggerLume/badges/gpa.svg)](https://codeclimate.com/github/DarkaOnLine/SwaggerLume)
[![StyleCI](https://styleci.io/repos/50113229/shield)](https://styleci.io/repos/50113229)

SwaggerLume
==========

Swagger 2.0-3.0 for Lumen

This package is a wrapper of [Swagger-php](https://github.com/zircote/swagger-php) and [swagger-ui](https://github.com/swagger-api/swagger-ui) adapted to work with Lumen.

Installation
============

 Lumen      | Swagger UI| OpenAPI Spec compatibility | L5-Swagger
:-----------|:----------|:---------------------------|:----------
 10.0       | 3         | 2.0, 3.0                   | ``` composer require "lumen-utils/swagger-lumen:10.*" ```

- Open your `bootstrap/app.php` file and:

uncomment this line (around line 26) in `Create The Application` section:
```php
     $app->withFacades();
```

add this line before `Register Container Bindings` section:
```php
     $app->configure('swagger-lume');
```

add this line in `Register Service Providers` section:
```php
    $app->register(\SwaggerLume\ServiceProvider::class);
```

- Run `php artisan swagger-lume:publish-config` to publish configs (`config/swagger-lume.php`)
- Make configuration changes if needed
- Run `php artisan swagger-lume:publish` to publish everything

Using [OpenApi 3.0 Specification](https://github.com/OAI/OpenAPI-Specification)
============
If you would like to use latest OpenApi specifications (originally known as the Swagger Specification) in your project you should:
- Explicitly require `swagger-php` version 3.* in your projects composer by running:
```bash
composer require 'zircote/swagger-php:3.*'
```
- Set environment variable `SWAGGER_VERSION` to **3.0** in your `.env` file:
```
SWAGGER_VERSION=3.0
```
or in your `config/l5-swagger.php`:
```php
'swagger_version' => env('SWAGGER_VERSION', '3.0'),
```
- Use examples provided here: https://github.com/zircote/swagger-php/tree/3.x/Examples/petstore-3.0

Configuration
============
- Run `php artisan swagger-lume:publish-config` to publish configs (`config/swagger-lume.php`)
- Run `php artisan swagger-lume:publish-views` to publish views (`resources/views/vendor/swagger-lume`)
- Run `php artisan swagger-lume:publish` to publish everything
- Run `php artisan swagger-lume:generate` to generate docs

Swagger-php
======================
The actual Swagger spec is beyond the scope of this package. All SwaggerLume does is package up swagger-php and swagger-ui in a Laravel-friendly fashion, and tries to make it easy to serve. For info on how to use swagger-php [look here](http://zircote.com/swagger-php/). For good examples of swagger-php in action [look here](https://github.com/zircote/swagger-php/tree/master/Examples/petstore.swagger.io).

