# Regex Hex

The hexadecimal (also known as base 16 or hex) is a positional numeral system that uses 16 distinc symbols. The symbols are "0"-"9" to represent values 0 to 9 and "A"-"F", or "a"-"f", to represent values 10 to 15.

One of the many uses of the hex system are hex color codes. A hex color code is a hexadecimal representation of a color in RGB format. RGB format defines a color by the amount of red, green and blue. Some examples of hex color codes are:

#fddfd2 #8ac5d2 #2c333e

In some cases we can define a hex color code using only three characters. This can be used when the same character is used twice to represent each value in the RGB combination. For example: #FFCC00 can be rewritten as #FC0. Depending on the application, the numeral sign can also be left out of the hex code.


## Summary

A regular expression, or regex, is a sequence of characters that defines a search pattern for text. Those characters can be literal characters or meta characters. 

The regex that we are going to analyze is: /^#?([a-f0-9]{6}|[a-f0-9]{3})$/

This particular regex allows us to find any hex code, whether it begins with a numeral sign (#) or not, and whether it has 6 or 3 characters (digits and leters) in it.

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

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

Characters ^ and $ are known as anchors. ^ anchor signifies a string that begins with the characters that follow it. $ anchor signifies a string that ends with the characters thats before it.  For example, ^abc will match any line or string that begins with abc, while xyz$ will match any line or string that ends with xyz.


### Quantifiers 

These appear before the $ anchor and set limits on the string your regex matches, such as the length/number of characters.
It can be written as exact {n}, at least {n,}, or a range {n, x}. For example, `{3, 16}` finds strings with 3-16 matches.

We find these in our hex regex example right after the bracket, where {6} finds a hex code with 6 characters and 3 for {3}:
`[a-f0-9]{6}|[a-f0-9]{3}`

### Grouping Constructs

The primary way of grouping is using parentheses, which hold "subexpressions". They can be separated with a colon.
For example, `(abc):(xyz)`.

In our example, we only have one subexpression because only one set of parentheses:
`([a-f0-9]{6}|[a-f0-9]{3})`

### Bracket Expressions

These signify the range of characters we want to match. For example, [abc] matches "aaa", "bin", "court", which can also
be written [a-c]. [a-zA-Z] is all lower and uppercase letters. These expressions can be turned negative with ^ after the
first bracket, as a means to say, "do not find this". For example, no vowels is [^aeiouAEIOU].

The * means the preceding item will match 0 or more times. ? means 0 or 1. + means 1 or more. These characters thus
lose their meaning inside bracket expressions, so you must use character escapes to get a literal intrepretation.

In our example, we are searching for lowercase letters a through f and digits 0 through 9 that follow a hashtag once, due to the ?:
`/^#?([a-f0-9]

### Character Classes

These define a set of characters. The period finds any character; \d matches any digit; \w matches any alphanumberic value;
\s matches a single white space character. The effect of the latter 3 can be inversed with capital letters. \D, \W, \S

For example, this searches for any digit and any letter, including . and -:
`([\da-z\.-]+)`

### The OR Operator

Bracket expressions don't require the search to meet ALL the requirements, it only needs one. The OR operator allows you to
denote when you want to match one case or the other. For example, `(t/T)` matches strings with t or T.

In our example, it searches for a pound sign with 6 or 3 characters attached:
`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

### Flags

Placed at the end of the regex, after second slash, and define additional regex limits. g is global search, i is case-insensitive
search, and m is multi-line search.

If you searched "dog", using g, it would only search for "dog". However, if you used gi, it would find "dog" and "Dog".

### Character Escapes

For characters that would be interpretted literally, but you do not want them to be: add a backslash in front of them.
For example, { would usually start a bracket expression, but if you combine with a backslash \{, then the regex would look
for an open curly, not start an expression.

This is how this includes . and - in the search:
`([\da-z\.-]+)`

## Author

https://github.com/XyzExia
