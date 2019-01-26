[Go to index page](https://github.com/Catacrockers/WikiTocha/blob/master/en/INDEX.md)

# Good programming practices

Here are some good programming practices, general for any languages, that stick to the big 3 premises in software development (taken from [Software construction in Java](https://www.edx.org/es/course/software-construction-java-mitx-6-005-1x)):

- Safe from bugs
- Easy to understand
- Ready for change

## 1. Static Checking

Static checking provides bug detection before runtime, like wrong types, sintaxis and structure. Many IDEs provide good tools for static checking (even for programming languages that are not statically-typed), which saves a lot of time in writing code.

You can find some tools for static checking in the following list categorized by programming language:

* https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis

## 2. Code Review

Code review is the practice of **checking and discussing code written by others**. The main purpose is **improving the code** quality by finding bugs, making the code clearer, anticipating problems, checking consistency with style standards, etc.

Also another goal of code review is **improving the programmer** by learning and teaching each others. It is a way of conversation between programmers using the code review as context.

Some concepts to have in mind when reviewing code are:
- **Don't repeat yourself**: avoid duplicated code, DRY the code out
- **Put comments where needed**: good comments are those that explain assumptions, specifications for funtions or links from where the code was copied, inspired. Bad comments are those that try to explain the code because of *bad naming* or because a *method* is needed.
- **Have one purpose for each variable**: name the variable so it self-explains what its purpose is
- **Use good names**: take your time to think good names for methods, classes, variables. Names should describe precisely what the code does so you don't need comments.
- **Don't use global variables**
- **Don't use magic numbers**: magic numbers are numeric values in the code that are placed by the programmer. It is better to use variables instead.
- **Methods return results rather than printing them**: It is important returning results for testing purposes too.
- **Use whitespace for readability**

## 3. Testing

Writing tests is a very hard task but makes code a lot safer. The goal of testing is to **make the code fail**, find bugs in order to fix them.

A good way of development  is test-first programming:
1. Write a specification for a function
2. Write tests that cover that specification
3. Write the code. If it passes the tests you are done.

Tests cases can be chosen by input partitioning and boundaries. Also white box testing and statement coverage are a useful tool. Code coverage tools are a good way to detect parts of the code that are never executed.

**Unit-test** each module in **isolation** as much as possible, so you don't depend on the results of some parts of the code that you are not testing.

It is a good practice to run **automated tests** regularly so you always know that changes on the code never make the tests fail, or if they do fail you will be notified inmediately so you can fix the bugs.

Also **regression tests** are a good way to fix bugs that you find. Every time you find a bug in your code you must make a test that elicits that bug, and then fix it so it passes the test. This way you make sure yout test suite will detect that bug if you ever regress.

## 4. Specifications

It is impossible to delegate responsibility for implementing a method unless you have a clear specification that acts as a contract. The client role writes the specification, and the developer implements the code that satisfies the specification.

Specification precondition is described by the word *requires*. Specification postcondition is indicated by the word *effects*. The precondition is and obligation on the client or caller of the method. The postcondition is an obligation of the implementer of the method.

# Things to improve

## Code analysis

* [John Carmack talks about static code analysis](http://www.viva64.com/en/a/0087/)
* [Codacy manager for Static Code Analysis](http://blog.codacy.com/2016/02/08/automate-your-code-reviews-with-codacy/)
* [GNU Code analysis](https://www.gnu.org/software/hurd/open_issues/code_analysis.html)
* [List of static code analizers](http://spinroot.com/static/)
* [Sonar manager for Static Code Analysis](https://en.wikipedia.org/wiki/SonarQube)

## Coding styles and good practices

* [Best coding practices](https://en.wikipedia.org/wiki/Best_coding_practices)

# Things to avoid

* [Anti-Patters](https://en.wikipedia.org/wiki/Anti-pattern), that shall be avoid in Organization, project management and Software
