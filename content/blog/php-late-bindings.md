+++
date = "2018-08-11T18:45:52+05:00"
title = "late static bindings in php"
+++

so recently i've been working with one php library. this library is a parser that behave as an event dispatcher.

basic usage of it is as follow:

```php
$parser = new parser($factory);
$parser->addlistener("eventa", function (handlera $handler) {
    $data = $handler->getdata();
});
$parser->parse($file);
```

this `$factory` variable is optional, as library contains its own handlers for any event.

but however i needed to tweak factory behavior for my needs. 

library's factory class contained something like this to determinate which handlers are responsible for which event:

```php
class factory
{
    protected static $objects = [
        'eventa' => 'handlera',
        'eventb' => 'handlerb',
        'eventc' => 'handlerc',
    ];
    
    // other logic 
}
```

let's say that i need to write my own handler for event a. `parser` class uses dependency injection to easily switch factory. all internal properties are protected, not private, so it is no problem to just extend this class and override ```objects``` variables. i should do it in no time!

```php
class myfactory extends factory
{
    protected static $objects = [
        'eventa' => 'myhandlera',
        'eventb' => 'handlerb',
        'eventc' => 'handlerc',
    ];
}

$parser = new parser(new myfactory());
$parser->addlistener("eventa", function (myhandlera $handler) {
    $data = $handler->getdata();
});
$parser->parse($file);
```

everything seems right, no errors, no notices, but my tweak doesn't work!. whenever i handle event a, i still working with it in handlera class, not myhandlera class.

what's the problem? let's look into object creation method in factory (very simplified version):

```php
public function createhandler($event)
{
    return new self::$objects[$event];
}
```

seems right, isn't it? it calls ```self::$objects```, and in my extended class this variable is overridden. but why isn't it working?

the problem is in difference of early and late static binding in php.

from [php docs](http://php.net/manual/en/language.oop5.late-static-bindings.php):

> static references to the current class like self:: are resolved using the class in which the function belongs, as in where it was defined:

in other words, it references variable in class that contains this method, not the class that is loaded in runtime.

best way to describe how late static binding works is this code (i found it in stackoverflow):

```php
class a {
    public static function get_self() {
        return new self();
    }

    public static function get_static() {
        return new static();
    }
}

class b extends a {}

echo get_class(b::get_self());  // a
echo get_class(b::get_static()); // b
echo get_class(a::get_self()); // a
echo get_class(a::get_static()); // a
```

so if author of this library used ```static::$objects[$event]``` my tweak would have worked and library would become much more extendable.

i had to copy-paste all of the factory class to make my tweak work. and whenever this library is updated, i have to redo ths gross thing. of course, you can fork this library, but then you have to sync your fork to original. none of this methods are pretty in my opinion.

hope you knew something new and won't fall into this trap in your own libraries.