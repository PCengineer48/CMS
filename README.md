Bootstrap CMS
=============


[![Build Status](https://img.shields.io/travis/GrahamCampbell/Bootstrap-CMS/master.svg?style=flat)](https://travis-ci.org/GrahamCampbell/Bootstrap-CMS)
[![Coverage Status](https://img.shields.io/scrutinizer/coverage/g/GrahamCampbell/Bootstrap-CMS.svg?style=flat)](https://scrutinizer-ci.com/g/GrahamCampbell/Bootstrap-CMS/code-structure)
[![Quality Score](https://img.shields.io/scrutinizer/g/GrahamCampbell/Bootstrap-CMS.svg?style=flat)](https://scrutinizer-ci.com/g/GrahamCampbell/Bootstrap-CMS)
[![Software License](https://img.shields.io/badge/license-Apache%202.0-brightgreen.svg?style=flat)](LICENSE.md)
[![Latest Version](https://img.shields.io/github/release/GrahamCampbell/Bootstrap-CMS.svg?style=flat)](https://github.com/GrahamCampbell/Bootstrap-CMS/releases)


## Introduction

Bootstrap CMS was created by, and is maintained by [Graham Campbell](https://github.com/GrahamCampbell), and is a PHP CMS powered by [Laravel 4.2](http://laravel.com) and [Sentry 2.1](https://cartalyst.com/manual/sentry). It relies on 12 of my packages including [Laravel Core](https://github.com/GrahamCampbell/Laravel-Core) and [Laravel Credentials](https://github.com/GrahamCampbell/Laravel-Credentials). Feel free to check out the [change log](CHANGELOG.md), [releases](https://github.com/GrahamCampbell/Bootstrap-CMS/releases), [license](LICENSE.md), [screenshots](SCREENSHOTS.md), [api docs](http://grahamcampbell.github.io/Bootstrap-CMS), and [contribution guidelines](CONTRIBUTING.md).


## Installation

[PHP](https://php.net) 5.4.7+ or [HHVM](http://hhvm.com) 3.1+, a database server, and [Composer](https://getcomposer.org) are required.

1. You may install by cloning from github, or via composer.
  * Github: `git clone git@github.com:GrahamCampbell/Bootstrap-CMS.git`
  * Composer: `composer create-project graham-campbell/bootstrap-cms --prefer-dist -s dev`
2. See the [Laravel Queuing](https://github.com/GrahamCampbell/Laravel-Queuing) readme for extra requirements before continuing.
3. From a command line open in the folder, run `composer install`.
4. Enter your database details into `app/config/databse.php`.
5. Run `php artisan app:install` to setup and seed your database.
6. You will need to enter your mail server details into `app/config/mail.php`.
  * You can disable verification emails in `app/config/packages/graham-campbell/navigation/config.php`
  * Mail is still required for other functions like password resets and the contact form
  * You must set the contact email in `app/config/packages/graham-campbell/contact/config.php`
  * I'd recommend [queuing](#setting-up-queing) email sending for greater performance (see below)
7. Finally, setup an [Apache VirtualHost](http://httpd.apache.org/docs/current/vhosts/examples.html) to point to the "public" folder.
  * For development, you can simply run `php artisan serve`
8. Additionally, you may to setup some of Bootstrap CMS's other features (see below).
  * Some things, like [caching](#setting-up-caching) and [queuing](#setting-up-queing), are disabled out of the box
  * This is to allow Bootstrap CMS to work with minimal setup
  * Please note that queuing is required in order to use the cron functionality which can do things like notify users of upcoming events, or send out weekly activity digests
  * Also note, without caching asset generation will cause page load delay - to reduce this, I have turned off minification in `app/config/packages/lightgear/asset/config.php` by default


## Setting Up Queuing

Queuing documentation is coming soon.


## Setting Up Caching

Bootstrap CMS provides caching functionality, and when enabled, requires a caching server.
Note that caching will not work with Laravel's `file` or `database` cache drivers.

1. Choose your poison - I'd recommend [Redis](http://redis.io).
2. Enter your cache server details into `app/config/cache.php`.
3. You will probably want to enabled minification in `app/config/packages/lightgear/asset/config.php`.
4. Setting the driver to array will effectively disable caching if you don't want the overhead.


## Setting Up Themes

Bootstrap CMS also ships with 17 themes, 15 from [Bootswatch](http://bootswatch.com).

1. You can set your theme in `app/config/theme.php`.
2. You can also set your nav bar style in `app/config/theme.php`.
3. After making theme changes, you will have to run `php artisan app:update`.


## Setting Up Google Analytics

Bootstrap CMS natively supports [Google Analytics](http://www.google.com/analytics).

1. Setup a web property on [Google Analytics](http://www.google.com/analytics).
2. Enter your tracking id into `app/config/analytics.php`.
3. Enable Google Analytics in `app/config/analytics.php`.


## Setting Up CloudFlare Analytics

Bootstrap CMS can read [CloudFlare](https://www.cloudflare.com/) analytic data through a package.

1. Follow the install instructions for my [Laravel CloudFlare](https://github.com/GrahamCampbell/Laravel-CloudFlare) package.
2. Remember to add your credentials to `app/config/packages/graham-campbell/cloudflare-api/config.php`.
3. Bootstrap CMS will auto-detect the package, only allow admin access, and add links to the navigation bar.


## License

GNU AFFERO GENERAL PUBLIC LICENSE

Bootstrap CMS Is A PHP CMS Powered By Laravel And Sentry 2.1
Copyright (C) 2013-2014  Graham Campbell

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
