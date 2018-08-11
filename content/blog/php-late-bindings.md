+++
date = "2018-08-11T18:45:52+05:00"
title = "Late static bindings in php"
+++

So recently I've been working with one php library. This library is a parser that behave as an event dispatcher.

Basic usage of it is as follow:

```php
$parser = new Parser($factory);
$parser->addListener("EventA", function (HandlerA $handler) {
    $data = $handler->getData();
});
$parser->parse($file);
```

This `$factory` variable is optional, as library contains its own handlers for any event.

But however I needed to tweak factory behavior for my needs. 

Library's factory class contained something like this to determinate which handlers are responsible for which event:

```php
class Factory
{
    protected static $objects = [
        'EventA' => 'HandlerA',
        'EventB' => 'HandlerB',
        'EventC' => 'HandlerC',
    ];
    
    // other logic 
}
```

Let's say that I need to write my own handler for event A. `Parser` class uses dependency injection to easily switch factory. All internal properties are protected, not private, so it is no problem to just extend this class and override ```objects``` variables. I should do it in no time!

```php
class MyFactory extends Factory
{
    protected static $objects = [
        'EventA' => 'MyHandlerA',
        'EventB' => 'HandlerB',
        'EventC' => 'HandlerC',
    ];
}

$parser = new Parser(new MyFactory());
$parser->addListener("EventA", function (MyHandlerA $handler) {
    $data = $handler->getData();
});
$parser->parse($file);
```

Everything seems right, no errors, no notices, but my tweak doesn't work!. Whenever I handle event A, I still working with it in HandlerA class, not MyHandlerA class.

What's the problem? Let's look into object creation method in factory (very simplified version):

```php
public function createHandler($event)
{
    return new self::$objects[$event];
}
```

Seems right, isn't it? It calls ```self::$objects```, and in my extended class this variable is overridden. But why isn't it working?

The problem is in difference of early and late static binding in php.

From [PHP Docs](http://php.net/manual/en/language.oop5.late-static-bindings.php):

> Static references to the current class like self:: are resolved using the class in which the function belongs, as in where it was defined:

In other words, it references variable in class that contains this method, not the class that is loaded in runtime.

Best way to describe how late static binding works is this code (I found it in StackOverflow):

```php
class A {
    public static function get_self() {
        return new self();
    }

    public static function get_static() {
        return new static();
    }
}

class B extends A {}

echo get_class(B::get_self());  // A
echo get_class(B::get_static()); // B
echo get_class(A::get_self()); // A
echo get_class(A::get_static()); // A
```

So if author of this library used ```static::$objects[$event]``` my tweak would have worked and library would become much more extendable.

I had to copy-paste all of the Factory class to make my tweak work. And whenever this library is updated, I have to redo ths gross thing. Of course, you can fork this library, but then you have to sync your fork to original. None of this methods are pretty in my opinion.

Hope you knew something new and won't fall into this trap in your own libraries.