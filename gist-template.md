# Regex Tutorial 

**Regular Expression**, or **regex**, is a sequence of characters that defines a search pattern. It is used to find certain patterns or find and replace a character or sequence of characters within a string. It is also used for validating inputs.
There's a lot of regex that can be used to validate or verify a user such as: email address, username, etc.
 
* Regex to match a valid email address: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
        

## Summary
This regex tutorial will explore the regex of matching an email address:

     /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
        
For this regex, each component has a specific responsibility to make sure or verify that the user enters an email address in the correct format which in this case begins with characters followed by `@` symbol and, lastly, the domain.

We will analyze and examine each component of this regex which plays a different role for the user to enter a valid email address. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [References](#References)
- [Author](#Author)

## Regex Components
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Slashes `/.../` means we are creating a regex using a regex literal which consists of a pattern enclosed between slashes, it has the same role as quotes for strings.

### Anchors
Anchors don't match any characters, it asserts the current position in the string matches the certain position. The caret **`^`** anchor indicates the beginning of the string. The dollar **`$`** anchor indicates the end of the string. In our given regex `^` is on the start and `$` is in the end: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`.

Another example of anchors in a different regex expression, regex of matching a hex value, that shows the `^` at the beginning of the string and a `$` in the end of the string: 

`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

### Quantifiers
Quantifiers specify the numbers of characters or expressions to match. The given regex has two quantifiers: `+` and `{}`. The plus **`+`** matches any string that contains at least one or more expression on its left. In our regex, it matches any string that contains one or more expressions on its left enclosed in square brackets `[]`. 

The curly brackets **`{x, y}`** indicates a range x to y which is the `{2, 6}` in our regex. It matches _two to six_ strings that contains any expressions enclosed in `[]` on its left.

An example of `+`:   in the expression `abc+`, it matches a string that has `ab` followed by at least _one or more_ `c`.

An example of `{x,y}`:   in the expression `abc{2,4}`, it matches a string that has `ab` followed by _two to four_ `c`.

### OR Operator
What is regex operator?
The Regular Expression is a string which is the combination of different characters that provides matching of the text strings. A regular expression can also be referred to as regex or regexp.

### Character Classes
Character Classes distingush specific kinds of characters from a certain set. Our regex has  character classes: `\.` and `\d`. The **`.`** means any character except a line break. By placing a backslash `\` in front of the `.`, it's "escaping" the character and is taken literally. The **`\d`** matches any single digit equivalent to [0-9].

An example of `\.`: in the expression `a\.c`, it matches `a.c`. The `.` is taken literally - as period.

An example of `\d`: in the expression `B3`, it matches `3`. The `\d` finds a digit.

### Flags
What is a flag in regex?
The flag s means dot all. That is, it makes the . dot character (technically refered to as the wildcard character) match everything, even newlines. In other words, with the s flag, the dot matches all possible characters. By default, the dot character in a regular expression matches everything, but newline characters.

### Grouping and Capturing
Grouping and Capturing is when a part of a pattern are enclosed in parentheses `()`. Our regex has three groups:

First group: `([a-z0-9_\.-]+)`, this expression includes **`+`** which means we match at least one or more of any characters in the square brackets `[a-z0-9_\.-]`. **`a-z`** is lowercase letters from a to z, **`0-9`** is numbers from 0 to 9, **`_`** is underscore, **`\.`** is period, and **`-`** is hyphen.

Second group: `([\da-z\.-]+)`, is the domain name which includes **`+`** as well, so we match at least one or more of any characters in the square brackets `[\da-z\.-]`. **`\d`** any digits, **`a-z`** lowercase letters from a to z, **`\.`** period, and **`-`** hyphen.

Third group: `([a-z\.]{2,6})`, is the top-level domains (TLDs). This expression matches _two up to six_ strings which contains **`a-z`** lowercase letters from a to z, and **`\.`** period or dot in this case.

### Bracket Expressions
Bracket expressions are used to specify characters to match, they are enclosed in square brackets`[]`. Our regex has three bracket expressions: `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, and `([a-z\.]{2,6})`.

An example of bracket expressions: in the expression `[abc]`, it matches any character in the brackets; either _a_ or _b_ or _c_.

### Greedy and Lazy Match
The greedy and lazy pattern will match the longest and shortest possible string. The quantifiers `*`, `+`, and `{}` are greedy operators which means the match is expanded as far as they can through the provided expression. In our regex, we have two greedy quantifiers: `+` and `{}`. To make it lazy and find the shortest match, we can use a `?`.

An example of greedy and lazy match: in the expression `<h1>Title</h1>`, using this `<.+>` which includes greedy quantifier will match the whole expression `<h1>Title</h1>`. Adding `?` to make it lazy `<.+?>` will match any character at least one or more times inside the `<` and `>` expanding as needed - the result only matches the h1 tags `<h1>` and `</h1>`.

### Boundaries
The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

There are three different positions that qualify as word boundaries:

Before the first character in the string, if the first character is a word character.
After the last character in the string, if the last character is a word character.
Between two characters in the string, where one is a word character and the other is not a word character.
Simply put: \b allows you to perform a “whole words only” search using a regular expression in the form of \bword\b. A “word character” is a character that can be used to form words. All characters that are not “word characters” are “non-word characters”.

### Back-references
Using Backreferences To Match The Same Text Again

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how: <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>. This regex contains only one pair of parentheses, which capture the string matched by [A-Z][A-Z0-9]*. This is the opening HTML tag. (Since HTML tags are case insensitive, this regex requires case insensitive matching.) The backreference \1 (backslash one) references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

To figure out the number of a particular backreference, scan the regular expression from left to right. Count the opening parentheses of all the numbered capturing groups. The first parenthesis starts backreference number one, the second number two, etc. Skip parentheses that are part of other syntax such as non-capturing groups. This means that non-capturing parentheses have another benefit: you can insert them into a regular expression without changing the numbers assigned to the backreferences. This can be very useful when modifying a complex regular expression.

You can reuse the same backreference more than once. ([a-c])x\1x\1 matches axaxa, bxbxb and cxcxc.

Most regex flavors support up to 99 capturing groups and double-digit backreferences. So \99 is a valid backreference if your regex has 99 capturing groups.

### Look-ahead and Look-behind
Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word anchors explained earlier in this tutorial. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

### References 
## https://gist.github.com/rizznn/7e524af5f10d2b1870e8babe2e936b0f

## https://www.codeguage.com/courses/regexp/flags

## https://www.geeksforgeeks.org/perl-operators-in-regular-expression/

## https://www.regular-expressions.info/wordboundaries.html

## https://www.regular-expressions.info/backref.html

## https://www.regular-expressions.info/lookaround.html


## Author
Rahil Rahimi is a student of University of GWU who is currently taking a coding bootcamp course to be a Full Stack Developer. Github link:
### https://github.com/rahilrahimi?tab=repositories


