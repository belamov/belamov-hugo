+++
date = "2018-08-01T10:25:16+05:00"
title = "Laravel Package - RabbitMQ listener"
source = 'https://github.com/belamov/laravel-rabbitmq-listener'
imagelink = "img/laravel.jpg"
+++
This is a package for Laravel framework.

It allows you to listen to RabbitMQ events.

Don't be confused, It's functionality has nothing to do with queues. My coworker was using RabbitMQ as a synchroniser between main server and another web service. Main server generates various events like updating an image or adding a row in database. We got new project written with Laravel that needed to sync via that RabbitMQ bus. I haven't found any package that would solve my problem, so I wrote my own. Now two new projects use this package. Might be useful for somebody too.

I tried to make it as general as possible, so you should implement some abstract classes and add some handler classes, because I can't predict the format of events from RabbitMQ


Throughout instructions could be found in [readme](https://github.com/belamov/laravel-rabbitmq-listener/blob/master/README.md).
 