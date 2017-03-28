# eval-math
Composer/Packagist version of EvalMath by Miles Kaufman
Copyright (C) 2005 Miles Kaufmann <http://www.twmagic.com/>
Version 1.0

Taken from http://www.phpclasses.org/browse/file/11680.html, cred to Miles Kaufmann

NAME
----
    EvalMath - safely evaluate math expressions
  
DESCRIPTION
-----------
    Use the EvalMath class when you want to evaluate mathematical expressions 
    from untrusted sources.  You can define your own variables and functions,
    which are stored in the object.  Try it, it's fun!
        
INSTALLATION
------------
To use it just require this extension in your `composer.json` file:

~~~
"israelfl/eval-math": "0.0.1",
~~~

Or just:
~~~
composer require israelfl/eval-math
~~~


SYNOPSIS
--------
~~~php
$m = new EvalMath;

// basic evaluation:
$result = $m->evaluate('2+2');

// supports: order of operation; parentheses; negation; built-in functions
$result = $m->evaluate('-8(5/2)^2*(1-sqrt(4))-8');

// create your own variables
$m->evaluate('a = e^(ln(pi))');

// or functions
$m->evaluate('f(x,y) = x^2 + y^2 - 2x*y + 1');

// and then use them
$result = $m->evaluate('3*f(42,a)');
~~~

METHODS
-------
~~~php
$m->evaluate($expr);
~~~
Evaluates the expression and returns the result. If an error occurs, prints a warning and returns false. If `$expr` is a function assignment, returns true on success.
~~~php    
$m->e($expr);
~~~
A synonym for $m->evaluate().
~~~php
$m->vars();
~~~
Returns an associative array of all user-defined variables and values.
~~~php
$m->funcs();
~~~
Returns an array of all user-defined functions.

PARAMETERS
----------
~~~php
$m->suppress_errors;
~~~
Set to true to turn off warnings when evaluating expressions
~~~php
$m->last_error;
~~~
If the last evaluation failed, contains a string describing the error. (Useful when suppress_errors is on).
