+++
date = "2020-04-12T00:55:16+05:00"
title = "PostgreSQL range types support for Laravel"
source = 'https://github.com/belamov/postgres-range'
imagelink = "img/laravel.jpg"
+++
It's a Laravel package for PosgreSQL range types support

I discovered this article [Date Ranges in Laravel](https://medium.com/@palypster/ranges-in-laravel-7-using-postgresql-c4bc69b91758) by [Pavol Perdík](https://github.com/palypster) 
and approaches described there could really help me out in my [Rehearsals booking project](/projects/rehearsals-booking/). 
They really simplify a lot of queries for managing rehearsal time and prices' intervals.

I implemented them inside my project and was very happy with results, 
so I decided to extract that implementation into package 
(also added support for other range types, though I didn't use them).

During the creation I dug deep into how Laravel manages migrations, 
and creates fields in database, that was a lot of fun! 
Also I finally got acquainted with Github Actions and CI, 
this project was perfect candidate to try them out on. 

I continued to stream my work, so if you are interested in watching 
my struggles, [there is a playlist](https://www.youtube.com/playlist?list=PL2znuYuctNg_o5Wg6tbRHfS0CAft0AKCk) 
with livecoding of this package from scratch.

Source code and documentation are available at [github](https://github.com/belamov/postgres-range)