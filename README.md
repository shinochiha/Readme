# Lumen PHP Framework

[![Build Status](https://travis-ci.org/laravel/lumen-framework.svg)](https://travis-ci.org/laravel/lumen-framework)
[![Total Downloads](https://poser.pugx.org/laravel/lumen-framework/d/total.svg)](https://packagist.org/packages/laravel/lumen-framework)
[![Latest Stable Version](https://poser.pugx.org/laravel/lumen-framework/v/stable.svg)](https://packagist.org/packages/laravel/lumen-framework)
[![Latest Unstable Version](https://poser.pugx.org/laravel/lumen-framework/v/unstable.svg)](https://packagist.org/packages/laravel/lumen-framework)
[![License](https://poser.pugx.org/laravel/lumen-framework/license.svg)](https://packagist.org/packages/laravel/lumen-framework)

Laravel Lumen is a stunningly fast PHP micro-framework for building web applications with expressive, elegant syntax. We believe development must be an enjoyable, creative experience to be truly fulfilling. Lumen attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as routing, database abstraction, queueing, and caching.

## Official Documentation

Documentation for the framework can be found on the [Lumen website](http://lumen.laravel.com/docs).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell at taylor@laravel.com. All security vulnerabilities will be promptly addressed.

## License

The Lumen framework is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)

## Queue

### Add this config to your .env file to identification your quueue node server id. Default node is 1.
> QUEUE_NODE=1
> SERVICES_USING_QUEUE=<services> (Input queue services separated by comma. Available queue services are inventories,histories and audit_trails)

### How to run queues
#### Open console and typing this command
> php artisan zahir:queues
#### Run queues with supervisor
##### Supervisor config
> [program:zo-inventories-queue]
> process_name=%(program_name)s_%(process_num)02d
> command=/path/to/php/bin/php artisan zahir:queuespv %(program_name) %(process_num)
> directory=/path/to/zahir_online_apps/
> autostart=true
> autorestart=true
> user=username_have_access_supervisor
> numprocs=number_of_process_worker
> redirect_stderr=true
> stdout_logfile=/path/to/error.log
#### Retry queues
##### Retry by console
> php artisan zahir:queue-retry all
##### Retry by API
> GET https://hostname.com/api/v2/queues/retry
#### Monitoring queues
You can view monitoring queues with this API
> GET https://hostname.com/api/v2/queues (View all queues)
> GET https://hostname.com/api/v2/queues?status=active (View all active queues)
> GET https://hostname.com/api/v2/queues?status=failed (View all failed queues)
> GET https://hostname.com/api/v2/queues?status=retry (View all retry queues)
> GET https://hostname.com/api/v2/queues?node=1 (View all queues on node 1)
> GET https://hostname.com/api/v2/queues?type=inventories (View all queues with type inventories)
> GET https://hostname.com/api/v2/queues?type=histories (View all queues with type histories)
> GET https://hostname.com/api/v2/queues?type=audit_trails (View all queues with type audit_trails)
> GET https://hostname.com/api/v2/queues/1c61adec-01d7-4a6a-afc1-643b09aa9d6f (View detail queue by id, please fill id with string uuid data type)

## Using MongoDB for queues and caches
### Add MongoDB Connection
> MONGO_HOST=<mongo host> (defaut : localhost)
> MONGO_PORT=<mongo port> (default : 27017)
> MONGO_DATABASE=<mongo database> (default : zahirqueues)
> MONGO_USERNAME=<mongo username> (default : zahirqueue)
> MONGO_PASSWORD=<mongo password> (default : zahir123!)

### MongoDB Queue
Add this config to .env file
> QUEUE_DRIVER=mongodb
> QUEUE_DATABASE_CONNECTION=mongodb

### Mongo DB Cache
Add this config to .env file
> CACHE_DRIVER=mongodb
> CACHE_DATABASE_TABLE=<collection name> (default: caches)
> CACHE_DATABASE_CONNECTION=mongodb

