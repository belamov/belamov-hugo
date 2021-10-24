+++
date = "2018-08-01T10:25:16+05:00"
title = "laravel package - rabbitmq listener"
source = 'https://github.com/belamov/laravel-rabbitmq-listener'
imagelink = "img/laravel.jpg"
+++
this is a package for laravel framework.

it allows you to listen to rabbitmq events.

don't be confused, it's functionality has nothing to do with queues. my coworker was using rabbitmq as a synchroniser between main server and another web service. main server generates various events like updating an image or adding a row in database. we got new project written with laravel that needed to sync via that rabbitmq bus. i haven't found any package that would solve my problem, so i wrote my own. now two new projects use this package. might be useful for somebody too.

i tried to make it as general as possible, so you should implement some abstract classes and add some handler classes, because i can't predict the format of events from rabbitmq


throughout instructions could be found in [readme](https://github.com/belamov/laravel-rabbitmq-listener/blob/master/readme.md).
 