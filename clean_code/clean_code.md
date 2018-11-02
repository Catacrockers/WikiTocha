# Writing clean code

A good developer must write clean code in order for the code to be robust, scalable, free from bugs, readable, testable, flexible.
In this section several topics for writing clean code will be summarized.

## Naming

A very important aspect of clean code is naming because names are an oportunity to communicate with other developers.
+ Choose your names carefully
+ Communicate your intention with names
+ Dont disinformate with your names: it must say what it means and mean what it says
+ Write pronounceable names
+ Don't use encondings, variable types etc in names
+ Names should help to read code like well written prose
+ Names for functions used frequently must be short, private names can be longer and descriptive

## Functions

Functions follow these rules:
+ They are small
+ They have the right names: helping navigation through the code
+ Big functions are the place where classes hide
+ Functions do one thing, do it well and do it only
+ If you can extract one function from another, then thar funtions was not doing only one thing

### Function structure
Function structure must be guided by
+ 3 arguments maximum (the same for constructors, setters can be used, or maps passed as argument)
+ no `boolean` arguments (it means the functions does 2 things)
+ don't use output arguments
+ don't pass `null` into functions (it is like a boolean)
