+++
date = "2018-09-17T11:28:12+05:00"
title = "Rehearsals booking project"
+++

I've been thinking about this project for a long time. I even began to working on it. First I tried to implement it with Django, but this framework really disappointed me. I didn't like it personally. I don't think that python is good language for complex business logic. In my opinion it is more suitable for some kind of relatively small scripts or something academic, like machine learning. 

Later I've rewritten it in Laravel but I got stuck in frontend. I was using some admin template, but it was too difficult and overwhelming, a lot of features and unnecessary complexion. I got frustrated and bailed on this project completely.

But now I decided to finish it. It will be a very good piece for my portfolio and also it has very good potential, I think.

The idea of project is very simple.

## Problem

In my city there is about 10 places where you can book a rehearsal for your band. You simply paying for hours and practice with your band.

But the process of booking is painful. The main inconvenience is that all of this places are not connected in any way. You have to manually search for them and talk to owners about available time. Zero interactivity.

I've never spoken to rehearsal base's owners, but I'm guessing that they have outdated way of managing their bases. It is probably some sort of textbook, maybe excel.

## Solution

I would like to aggregate all rehearsal stuff in one place. There will be list of all bases, very good search engine and filter, so band members will find a place to gather in no time and without any effort. Each base will have interactive schedule updated in real time, no more talking to owners, just pick your hours and book it. 

And for owners there will be management page, where they can see how business is going, all relevant statistics and information.

## Plan

Very core functionality will be implemented in the beginning: bases search, rehearsal booking, admin panel to manage your base.

I struggled with frontend in previous iteration, probably because there wass a lot of bad jqery code (i'm not good with javascript).

Now I want SPA build with vuejs. In the backend there will be only rest api build with laravel.

1. So first of all I need to learn Vuejs enough to build SPA. I got some courses for that framework.

2. Next is backend. I'm very confident with laravel and rest api stuff, so there will be no problems

3. When MVP is ready and functional, make some presentation and contact rehearsal base owners, offer them a cooperation. tbh, I didn't think what kind of cooperation it would be. There's several options, I haven't decide yet. I guess we will come to resolution during interrogation 

4. Next step will depend on the deal with bases owners. If there will be no success, I'm still going to continue working on that, just because it is interesting. I could learn new technologies, new products on relatively real project
 