+++
date = "2020-04-12T00:55:16+05:00"
title = "postgresql range types support for laravel"
source = 'https://github.com/belamov/postgres-range'
imagelink = "img/laravel.jpg"
+++
it's a laravel package for posgresql range types support

i discovered this article [date ranges in laravel](https://medium.com/@palypster/ranges-in-laravel-7-using-postgresql-c4bc69b91758) by [pavol perdík](https://github.com/palypster) 
and approaches described there could really help me out in my [rehearsals booking project](/projects/rehearsals-booking/). 
they really simplify a lot of queries for managing rehearsal time and prices' intervals.

i implemented them inside my project and was very happy with results, 
so i decided to extract that implementation into package 
(also added support for other range types, though i didn't use them).

during the creation i dug deep into how laravel manages migrations, 
and creates fields in database, that was a lot of fun! 
also i finally got acquainted with github actions and ci, 
this project was perfect candidate to try them out on. 

i continued to stream my work, so if you are interested in watching 
my struggles, [there is a playlist](https://www.youtube.com/playlist?list=pl2znuyuctng_o5wg6tbrhfs0caft0akck) 
with livecoding of this package from scratch.

source code and documentation are available at [github](https://github.com/belamov/postgres-range)