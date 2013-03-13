laravel4-idehelper-generator
============================

Generates a helper file to assist with IDEs with code completion for Laravel 4 in PHPStorm and Sublime Text 2.

## Installation

Edit your project's `composer.json` file to require `jonphipps/idehelpers`.

    "require": {
		"laravel/framework": "4.0.*",
		"jonphipps/idehelper": "dev-master"
	}

Update Composer from the Terminal:

    composer update

And finally add the service provider to the providers array in `app/config/app.php`.

    'JonPhipps\IdeHelper\IdeHelperServiceProvider'

## Usage

Run the `artisan idehelper:generate` command from the Terminal.

    php artisan idehelper:generate

A file named `_ide_helper.php` will be written to the root of the `app` folder of your Laravel project. You can move this file anywhere that suits you.

Every time the generator is run it will simply overwrite this file, so if you make corrections make sure the file is in source control or moved elsewhere.

The file _will_ contain errors that reflect any errors in the Laravel documentation blocks. If you're using PHPStorm, these will be especially dramatically formatted in the display. As of this writing there are quite a few errors in namespaced hints.

This has not been fully tested, so issues and pull requests are welcome.

## How it works

If you're curious, it reads the Laravel config file to get a list of the aliases -- it will do all of the aliases listed there. It then uses the alias to resolve the façade and retun the class represented by the façade. The class is passed to both the PHP ReflectionClass and PHP Documentor's Reflection class.

These two methods of reflection get the method parameters as represented in the code as well as the documentation for the method, using both to build a more complete picture of the methods, parameters, and their defaults.


