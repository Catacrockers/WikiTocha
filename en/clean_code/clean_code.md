[Go to Index page](https://github.com/Catacrockers/WikiTocha/blob/master/en/INDEX.md)

# Writing clean code

A good developer must write clean code in order for the code to be robust, scalable, free from bugs, readable, testable, flexible.
In this section several topics for writing clean code will be summarized.

## Naming

A very important aspect of clean code is naming because names are an oportunity to communicate with other developers.
+ Choose your names carefully: they are a tool you can use to **communicate with others**.
+ **Communicate your intention** with names: if you need to put a comment or look at code, you failed to communicate your intent.
+ Dont **disinformate** with your names: it must say what it means and mean what it says. Don't let names degrade with refactors.
+ Write **pronounceable names**: people are going to talk about the code
+ Don't use encondings, variable types etc in names: use powerfull IDEs and tests for checking types.
+ Names should help to read code like well written prose: use parts of speech:
   - classes have nouns names
   - variables have nouns names
   - methods have verb names
      - if they are booleans then names must be predicates
      - if they are properties thay can be nouns
+ The length of a variable name should be proportional to its scope.  
+ The length of a function or class name is the inverse.
+ Encapsulate meaningful names in a context by enclosing them in 
   - well-named classes
   - functions
   - namespaces
 
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
+ place most used funcions at the top of the class
+ Tell, don't ask: tell objects what to do, don't ask for their state. Avoid query functions.
+ Law of demeter: functions should not know about the entire navigation of the system. Don't call methods on objects that are returned from previous method.

### Code form
+ Comments should be rare: every time you write a comment you failed to make your code expresive
+ Format your code following a standard: white lines, spaces, indentation, line length, max lines per file.
+ Classes must be a group of functions that hide the implementation of the data they manipulate (**Tell don't ask principle**)
+ If a getter is necessary inside a class, it must hide the implementation of the data abstracting it.
+ Data structures are a group of data with no functions.
+ Concrete things must depend on abstract things. (**dependency inversion principle**)
+ Separate data from objets by putting layers between. The layer will depend on the application objects and on the data.

### Test Driven Development

+ Uncle Bob's 3 laws
   - [x] Write **NO** production code except to pass a failing test
   - [x] Write only **enough** of a test to demonstrate a failure
   - [x] Write only **enough** production code to past the test
 + TDD results in
   + much less time debugging
   + relyable low level documentation
   + decoupled designs
   + no fear to change and clean code
   + prevents code rot

# References

* [Test driven development](http://alexott.net/en/cpp/CppTestingIntro.html)
