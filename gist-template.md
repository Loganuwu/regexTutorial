# Regex tutorial

Regex is used to filter through text and bring back queries that is looking for specifics formats or text throughout a database of inputs.

## Summary

A Regex (Regular Expression) is a string of text that can be used to create search patterns that locate, match and manage text. Here is an example code snippet of regex:
 ```
 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
 ```

* This Regex is used to match an e-mail address

A Regex can be used from the command line and text editors as well to locate text residing in a file.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors are characters contained within the regular expression that enables a user to match strings which may begin or end, or both, certain characters.

Examples of Anchors:

* `^` - matches any string that start with the anterior word
* `$` - matches a string that end with preceeding word before the character

```
^Engineer          matches any string starting with `Engineer`
Sciences$          matches any string ending with `Science`
^New Job$   matches exact string
juniorDeveloper         matches any string that has the exact text `juniorDeveloper` in it
```

### Quantifiers

Quantifiers are characters contained within the regular expression that specify how many instances a character, group, or character class must be represented in the input to be matched.

Examples of Quantifiers:

* `*` - matches a string that has the anterior followed by zero or more of the last character
* `+` - matches a string that has the anterior followed by one or more of the last character
* `?` - matches a string that has the anterior followed by zero or one of the last character
* `{}` -  matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string
* `()*` - matches a string that has any anterior characters followed by zero or more copies of the string within the brackets

```
xyz*        matches a string that has xy followed by zero or more z
xyz+        matches a string that has xy followed by one or more z
xyz?        matches a string that has xy followed by zero or one z
xyz{3}      matches a string that has xy followed by 3 z
xyz{3,}     matches a string that has xy followed by 3 or more z
xyz{3,6}    matches a string that has xy followed by 3 up to 6 z
x(yz)*      matches a string that has a followed by zero or more copies of the sequence yz
x(yz){3,6}  matches a string that has a followed by 3 up to 6 copies of the sequence bc
```

### Grouping Constructs

Grouping unifies a pattern or string so that it is matched in a complete block

Examples of Grouping are as follows:
* `()` - parentheses creates a capture group
* `(?:)` - using `?:` disables the capturing group
* `(?<>)` - using `?<>` puts a name to the group

```
x(yz)           parentheses create a capturing group with value yz
x(?:yz)*        using ?: we disable the capturing group
x(?<end>yz)     using ?<end> we put a name to the group
```

### Bracket Expressions

Bracket Expressions are characters enclosed by a bracket `[]` matching any single character within the brackets. 
*note*: if the first character within the brackets is a `^` then it signifies any character *not* in the list, and is unspecified whether it matches an encoding error. 

Examples of Bracket Expressions:
 
* `[]` - matching any single character within the brackets
* `[]%` - matching the string inside the brackets before the `%`
* `[^]` - matching any string that has not a letter from within the brackets (negation of expression)

```
[xyz]         matches a string that either has 'x' or 'x y' or 'x z' (same as x|y|z)
[x-y]         behaves the same as [xyz]
[u-zU-Z0-9]   a string that represents a single case insensitive hexadecimal digit
[0-9]%        a string that has a character from 0-9 before a %
[^a-zA-Z]     a string that does not contain a letter from 'a' to 'z' or from A to Z
```

### Character Classes

Character Classes, or character set, tells the regex engine to match only one out of several specific characters including digits, words, or whitespace

Examples of Character Classes:

* `\d` - matches a single character that is a digit
* `\w` - matches a word character (any alphanumeric character plus underscore)
* `\s` - matches a whitespace character (including tabs and line brakes)
* `.` - matches any character
* the capital case for any previously mentioned characters will inverse the match

```
\d    matches a single any digit 0-9
\w    matches a single any character that is a-z
\s    matches ` `
.     matches any character
\D    matches a single non-digit character
\W    matches a single any non-character that is a-z
\S    matches a single non-` `
```

### The OR Operator

OR Operators, or alternation operator, matches the choice of a regular expression: if you put the character(s) representing the alternation operator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar
* `[]` - matches a string that has any anterior characters without any characters within the brackets

```
x(y|z)  matches a string that has 'x' followed by 'y' or 'z' (and captures y or z)
x[yz]   matches a string that has 'x', but without capturing 'y' or 'z'
```

### Flags

Flags are optional parameters that a user can add to a standard expression to make it search in a different way. Each flag is denoted by a single alphabetical character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags:

* `g` - Global, does not return after the first match, which restarted any previous searches from the end of the previous match (Makes the expression search for all occurrences)
* `m` - Multi-line, when enabled with the Anchors ^ $ will match the start and end of a line, rather than the whole string
* `i` - Insensitive, will make the entire expression case-insensitive

```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```
### Character Escapes

The backslash \ in a regular expression precedes a literal character. You also escape certain letters that represent common character classes, such as \w for a word character or \s for a space. The following example matches word characters (alphanumeric and underscores) and spaces.

```
\ 	    Backslash 	                           Used to escape a special character
^ 	    Caret 	                               Beginning of a string
$ 	    Dollar sign 	                         End of a string
. 	    Period or dot 	                       Matches any single character
|       Vertical bar or pipe symbol 	         Matches previous OR next character/group
?       Question mark 	                       Match zero or one of the previous
* 	    Asterisk or star 	                     Match zero, one or more of the previous
+	      Plus sign                              Match one or more of the previous
( ) 	  Opening and closing parenthesis 	     Group characters
[ ] 	  Opening and closing square bracket 	   Matches a range of characters
{ } 	  Opening and closing curly brace 	     Matches a specified number of occurrences of the previous
```

## Author

My name is Logan Barajas and I am a full time Software Engineering student attending California State University, San Marcos. I am attending the UCI fullstack bootcamp to get more real world experience under my belt and hopefully get my foot into the work force during my last year and a half of university.

[GitHub Profile](https://github.com/Loganuwu)