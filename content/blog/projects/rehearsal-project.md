+++
date = "2018-09-17T11:28:12+05:00"
title = "rehearsals booking project"
+++

i've been thinking about this project for a long time. i even began to working on it. first i tried to implement it with django, but this framework really disappointed me. i didn't like it personally. i don't think that python is good language for complex business logic. in my opinion it is more suitable for some kind of relatively small scripts or something academic, like machine learning. 

later i've rewritten it in laravel but i got stuck in frontend. i was using some admin template, but it was too difficult and overwhelming, a lot of features and unnecessary complexion. i got frustrated and bailed on this project completely.

but now i decided to finish it. it will be a very good piece for my portfolio and also it has very good potential, i think.

the idea of project is very simple.

## problem

in my city there is about 10 places where you can book a rehearsal for your band. you simply paying for hours and practice with your band.

but the process of booking is painful. the main inconvenience is that all of this places are not connected in any way. you have to manually search for them and talk to owners about available time. zero interactivity.

i've never spoken to rehearsal base's owners, but i'm guessing that they have outdated way of managing their bases. it is probably some sort of textbook, maybe excel.

## solution

i would like to aggregate all rehearsal stuff in one place. there will be list of all bases, very good search engine and filter, so band members will find a place to gather in no time and without any effort. each base will have interactive schedule updated in real time, no more talking to owners, just pick your hours and book it. 

and for owners there will be management page, where they can see how business is going, all relevant statistics and information.

## plan

very core functionality will be implemented in the beginning: bases search, rehearsal booking, admin panel to manage your base.

i struggled with frontend in previous iteration, probably because there wass a lot of bad jqery code (i'm not good with javascript).

now i want spa build with vuejs. in the backend there will be only rest api build with laravel.

1. so first of all i need to learn vuejs enough to build spa. i got some courses for that framework.

2. next is backend. i'm very confident with laravel and rest api stuff, so there will be no problems

3. when mvp is ready and functional, make some presentation and contact rehearsal base owners, offer them a cooperation. tbh, i didn't think what kind of cooperation it would be. there's several options, i haven't decide yet. i guess we will come to resolution during interrogation 

4. next step will depend on the deal with bases owners. if there will be no success, i'm still going to continue working on that, just because it is interesting. i could learn new technologies, new products on relatively real project
 