# Cppcheck

Cppcheck is an analysis tool for C/C++ code. It detects the types of bugs that the compilers normally fail to detect.

## What Cppcheck do

Cppcheck execution will look for common problems in code. It is possible to create your own custom rules. Cppcheck uses the PCRE library to handle regular expressions.
[PCRE](http://www.pcre.org) stands for "Perl Compatible Regular Expressions". Cppcheck offer:

* Automatic variable checking.
* Bounds checking for array overruns.
* Classes checking (e.g. unused functions, variable initialization and memory duplication).
* Usage of deprecated or superseded functions according to Open Group.
* Exception safety checking, for example usage of memory allocation and destructor checks.
* Memory leaks, e.g. due to lost scope without deallocation.
* Resource leaks, e.g. due to forgetting to close a file handler.
* Invalid usage of Standard Template Library functions and idioms.
* Miscellaneous stylistic and performance errors.

## How it works

Providing path with sources and includes, it will analyze the code. It seems to work using lexical analysis [TBC]. Can use parser with regular expressions to provide control, and a stack to provide more information about code analysis.

When you provide source code:

1. Pre-process code. By default, if no pre-processor variables are provided try to analyze all ifdef statements.
2. Tokenizer resultant code.
3. Simplifier.
4. Process result using checks and rules.
5. Report results.

### Installation

```
sudo dnf install cppcheck.x86_64 cppcheck-gui.x86_64
```

### Usage

```
cppcheck --inconclusive path_1_to_check path_2_to_check -ipath_to_ignore -j 2 --enable=all --xml-version=2 2> output/result.txt
```

* --inconclusive: Error messages will also be written when the analysis is inconclusive.
* -I<path>: Set includes path.
* -i<path>: Ignore this path in analysis.
* -j <int>: Multithreading
* -D<macro>: Define preprocess macro. If not defined cppcheck will analyze all code.
* -U<macro>: Undefine preprocess macro.
* --suppress=<error id>:<file>: Disable a error for a file.
* --enable=<severity>: Active message using severity id or all.
* --platform=<config.xml>: Check platform configuration.
* --debug: Generate output debug info. Userful to create your own rules.
* --rule-file==<rulepath/rulename.rule>: Use a rule file
* --xml-version=2: Generate output with xml format.
* Output report: Add ```2> output/result.txt``` at the end.

### Severities

Exist different kind of issues:

* *error*: Used when bugs are found.
* *warning*: Suggestions about defensive programming to prevent bugs.
* *style*: Stylistic issues related to code cleanup (unused functions, redundant code, constness, and such).
* *performance*: Suggestions for making the code faster. These suggestions are only based on common knowledge. It is not certain you'll get any measurable difference in speed by fixing these messages.
* *portability*: Portability warnings. 64-bit portability. code might work different on different compilers. etc.
* *information*: Configuration problems. The recommendation is to only enable these during configuration.

By default only error messages are shown. Through the --enable command more checks can be enabled.

### Developing rules and platforms

To an advanced usage, you can develop in different platforms and use custom rules. Rules seems to check tokes generated from code to do an lexical analysis. Debug flag will show code processed.

#### Custom rules

Cppcheck uses the PCRE library to handle regular expressions and xml. You can create rules, in example:

```xml
<?xml version="1.0"?>
<rule version="1">
  <pattern>.+</pattern>
  <message>
    <id>testRuleDetectAll</id>
    <severity>style</severity>
    <summary>This is a test rule.</summary>
  </message>
</rule>
```

Alternatively, you can write rules in c++. [Here](http://www.cs.kent.edu/~rothstei/spring_12/secprognotes/cppcheck_writing-rules-3.pdf) a guide about it.

#### Platform configuration xml

If you want to analyze code for other system, you can create a custom file, in example:

```xml
<?xml version="1"?>
<platform>
  <char_bit>8</char_bit>
  <default-sign>signed</default-sign>
  <sizeof>
    <short>2</short>
    <int>4</int>
    <long>4</long>
    <long-long>8</long-long>
    <float>4</float>
    <double>8</double>
    <long-double>12</long-double>
    <pointer>4</pointer>
    <size_t>4</size_t>
    <wchar_t>2</wchar_t>
  </sizeof>
</platform>
```

# Creating cppcheck rules

## Rule template

To create a new rule create a new file ```rulename.rule``` and edit ```$(variables)```

```xml
<?xml version="1.0"?>
<rule version="1">
  <pattern></pattern>
  <message>
    <id></id>
    <severity></severity>
    <summary></summary>
  </message>
</rule>
```

* *rulename*: Must contain severity and a short descriptive name. ```severity_name.rule```.
* *pattern*: Must contain a regular expression to use.
* *id*: Unique id.
* *severity*: Group of issue. (error, warning, style, performance, portability, information).
* *summary*: Human readble message when issue appear.

## Execute cppcheck with a rule

You can test a rule with a file using this command:

```
cppcheck --rule-file=<rulename.rule> <file.c>
```

In example:

```
cppcheck --rule-file=severity_rulename.rule custom_rules_1.c
```

* Note: If you want to know more of regexp, take a look to the section.
