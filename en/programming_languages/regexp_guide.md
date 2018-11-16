# Regular expression

A regular expression is a sequence of symbols and characters expressing a string or pattern to be searched for within a longer piece of text. It can be parsed by any regular language.

* Act as a finite automata.
* List of states, list of transitions between them.
* Process input until accept or error state is reached.
* No way to maintain state.
* Cannot back trace.

## Definitions

* *Literal*: A literal is any character we use in a search or matching expression, for example, to find ind in windows the ind is a literal string - each character plays a part in the search, it is literally the string we want to find.
* *Metacharacter*: A metacharacter is one or more special characters that have a unique meaning and are NOT used as literals in the search expression, for example, the character ^ (circumflex or caret) is a metacharacter.
* *Target string*: This term describes the string that we will be searching, that is, the string in which we want to find our match or search pattern.
* *Search expression*: Most commonly called the regular expression. This term describes the search expression that we will be using to search our target string, that is, the pattern we use to find what we want.
* *Escape sequence*: An escape sequence is a way of indicating that we want to use one of our metacharacters as a literal. In a regular expression an escape sequence involves placing the metacharacter \ (backslash) in front of the metacharacter that we want to use as a literal, for example, if we want to find (s) in the target string window(s) then we use the search expression \(s\) and if we want to find \\file in the target string c:\\file then we would need to use the search expression \\\\file (each \ we want to search for as a literal (there are 2) is preceded by an escape sequence \).

## Cheatsheet

### Basics

| Token   |      Definition|
|:----------:|:-------------|
| . |  Matches any character, except for line breaks if dotall is false. |
| * |  Matches 0 or more of the **preceding** character. |
| + |  Matches 1 or more of the **preceding** character. |
| ? |  Preceding character is optional. Matches 0 or 1 occurrence. |
| \d |  Matches any single digit |
| \w |  Matches any word character (alphanumeric & underscore). |
| \b | 	Matches a word boundary. If a character is a word’s last or first word character or If a character is between a word or non-word character |
| \B | 	Matches a non-word boundary |
| \d | 	Matches any digit 0 to 9 |
| \D | 	Matches any non-digit |
| \s | 	Matches any whitespace character |
| \S | 	Matches any non-whitespace character |
| \w | 	Matches any word character (letter, number & underscore) |
| \W | 	Matches any non-word character |
| ^ |  Matches the beginning of a string. |
| $ | Matches the end of the string. |
| [abc] | 	Any single character a, b or c |
| [^abc] | 	Any character other than a, b or c |
| [a-z] | 	Character between(including) a to z |
| [\^a-z] | 	Character except from a to z |
| [A-Z] | 	Character between(including) A to Z |
| [XYZ] | Matches any single character from the character class. |
| [XYZ]+ | Matches one or more of any of the characters in the set. |
| (…) | 	Capture everything enclosed |
| (a&#124;b) | 	Match either a or b |
| a? | 	Character a is either absent or present one time |
| a* | 	Character a is either absent or present more times |
| a+ | 	Character a is present one or more times |
| a{3} | 	3 occurences of character a consecutively |
| a{3,} | 	3 or more occurences of character a consecutively |
| a{3,6} | 	3 to 6 occurences of character a consecutively |

## Websites

* [Learn fast reg with examples](https://regexone.com/)
* [Reg expression](http://regexr.com/)
* [Reg expr info](http://www.regular-expressions.info)
