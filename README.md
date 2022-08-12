# Regex-Tutorial

## Summary

Today, we will be discussing regular expressions, also known as RegEx. RegEx is a tool that may be used to define a search term parameter, and can be applied in many differnt circumstances, accross multiple coding languages. 

The RegEx we will be breaking down searches for an email address pattern within a string. Please review the following code snippit: 
```
/[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/
```

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components
The RegEx we are dissecting today has three elements that we will look into further.  
Complete Regex for Reference:```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/    /[\w._%+-]+@[\w.-]+\.[a-zA-z]{2,4}/```

Element 1: Username
```[\w._%+-]+```
* This element will check to match the username portion of the email address. It may contain any letters, any numbers, periods, underscores, or dahses.
* Example : ```$araH%75``` would fail due to the special characters, however```sarah75``` would match. 

Element 2: Domain
```[\w.-]+\```
* This element will check to match the domain portion of the email address. It may contain letters, numbers and dashes. 
* Example: ```domain_name``` would fail due to the underscore, however ```domain-name``` would match. 

Element 3: Suffix
```[a-zA-z]{2,4}```
* this element checks the suffix fo the email address. Think ".com"/".edu". It may contain only letters, and they must be between 2 and 6 characters long. 
* Example: ```.company``` would fail due to the character count, however ```.com``` would match. 

For additional breakdowns of how each element in this RexEx works, please see more details explanations below. 

### Anchors
Anchors encapulate regex components to define what search pattern to find. 
Examples of Anchors are as follows:

* `^` - matches any string that start with the anterior word
* `$` - matches a string that end with preceeding word before the character
* Examples:
```
^Hello          matches any string starting with `Hello`
World$          matches any string ending with `World`
^Hello World$   matches exact string
goodbye         matches any string that has the exact text `goodbye` in it
```

### Quantifiers
```+``` = Repeats the previous item one or more times (Greedy Match)
* Example: ```a+``` would return a positive match for all items where the ```a``` character occurs one or more times.  


```{a,b}``` = defines a minimum ```a``` and a maximum ```b``` number of characters. 
* Example: ```{2,4}``` would retrun a positive match for items containing between 2 and 6 characters 


### OR Operator
OR Operators (Alternation Operator) matches on of a choice of regular expressions: if you put the character(s) representing the alternation operator between any two characters in the regular expression, the result matches the union of the strings that those two characters match.

Examples of OR Operators are as follows:

* `(|)` - matches a string that has any anterior characters followed by the characters on the left or right of the vertical bar
* `[]` - matches a string that has any anterior characters without any characters within the brackets
* Examples: 
```
x(y|z)  matches a string that has x followed by y or z (and captures y or z)
x[yz]   matches a string that has x, but without capturing b or c
```

### Character Classes
 ```.``` = Any character except newline
* When combined with the ```\``` anchor, ```\.```
```[a-z]``` = Accepts any letter between ```a``` and ```z```
```[0-9]``` = Accepts any digit between ```0``` and ```9```

### Flags
Flags are optional parameters that we can add to a plain expression to make it search in a different way. Each flag is denoted by a single alphabetic character, and serves different purposes in modifying the expression's searching behavior.

Examples of Flags are as follows:
* `g` - Global, does not return after the first match, which restarted any subsequest searches from the end of the previous match (Makes the expression search for all occurences)
* `m` - Multi-line, when enabled the Anchors (^ $) will match the start and end of a line, rather than the whole string
* `i` - Insensitive, makes the entire expression case-insensitive
* Examples:
```
/Hello/g   matches all `Hello` in the test
/Hello/m   matches the beginning and ending of each line with `Hello`, rather than the whole string `Hello` itself
/Hello/i   matches all `hello` despite case (Hello, hEllo, heLlo, hellO, hello, HELLO all match)
```

### Grouping and Capturing
* Example: ```[\w._%+-]+``` where the () group together the ```[\w._%+-]``` bracket expression with the ```+``` quantifier.
* This regex matches any letter or number a-z or 0 to 9, accepts underscores, periods and dashes. Then the quantifier matches one or more of the previous token. 

### Bracket Expressions
Bracket expressions are the syntax theroy on combining character classes. Multiple character classes may be combined in a single bracket expression. 

* Example: [\w.] where the regex would match any letter or number. 

### Greedy and Lazy Match
```{a, }``` = Lazy match, searches number ```a``` or more
```{a,b}``` = greedy match, search BETWEEN numbers ```a``` and ```b```

### Author

-Yousef Kangarani, UW Coding Bootcamp Student


### Sources and References

- [regexr](https://regexr.com/)
- [BackRef](https://www.regular-expressions.info/backref.html)
- [RegExpression](https://www.regular-expressions.info/wordboundaries.html)