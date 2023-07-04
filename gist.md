# Regex Tutorial - Matching an Email

A regular expression (regex for short) is a sequence of characters that defines a specific search pattern. Regex are more encompassing and dynamic compared to methods that require a direct match because you can find specific strings that encompasses what we desire throughout the whole text. Here are a few examples how we can use regex:
* Search
    * We can use Regex to search for specific patterns within a larger text

* Validation
    * We can use Regex to validate data. We can ensure that user input matches a specific pattern

* Extraction
    * We can use Regex to extract specific information from a larger text by capturing the patterns

* Text Manipulation
    * We can manipulate text by replacing specific patterns with other text/patterns

## Summary

The Regex I will be focusing on are Emails. I will be breaking down an Email Regex based on the Table of Contents in order describe the purpose and which part of the code pertains to each topic. 

Example Code: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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
- [Credits](#credits)


## Regex Components

### Anchors
* Regex anchors are special characters that match a specific position within the string. Whilst they do not match any actual characters within the string, they allow you to specify where a pattern should occur in relation to the beginning or end of the expression. 
* `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
    1. '^' (caret)- Start of Line Anchor:
        * The caret anchor at the start of the expression informs us that the email address should start at the beginning of the line
    2. '$' (dollar sign)- End of Line Anchor:
        * The dollar sign at the end of the pattern informs us that the email address should end at the end of the line. 
* These anchors ensure that the entire email address matches the pattern from start to finish. Anchors make sure that the pattern does not contain any additional characters before or after the email address.

### Quantifiers
* Regex quantifiers are symbols and/or metacharacters that specify the number of occurences of a preceding element within the pattern. Controlling the repetition or quantification of a character, group, or class within the pattern. 
* `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
    1. '+' (plus sign)- One or More Quantifier:
        * The plus sign is applied to the preceding element/group, indicating that it must occur one or more times. 
        * Here are the following groups the plus sign applies to within our snippet of code: 
            * `[a-z0-9_\.-]`
            * `[\da-z\.-]`
            * `[a-z\.]`
        * Our plus sign quantifier makes sure that the characters within these brackets are present atleast once. 
    2. '{2,6}'- Range Quantifier: 
        * Our range quantifier in our snippet of code ({2,6}) indicates that our pattern in the preceding element should occur between 2-6 times. This quantifier ensures that the top-level domain part of the email address contains 2-6 lowercase letters or periods.
        * Top-level domain (TLD) refers to the name that comes after the last period. For example ".com", ".edu", or ".org" within our email address. 
        * Here are the following groups the {2,6} range quantifier applies to within our snippet code:
            * `[a-z\.]`
### OR Operator
* A regex OR operator allows us to specify multiple alternatives for matching a particular pattern. an OR operator is represented by the vertical bar '|'. There are 2 instances of the OR operator.
    1. `[\da-z\.-]+`:
        * This character sets matches one or more occurences of either a digit ('/d'), a lowercase letter ('[a-z]'), a dot ('\.'), or a hyphen ('-'). The OR operator allows any of these characters to be matched.
    2. `[a-z\.]{2,6}`:
        * This character set matches between 2-6 occurences of either a lowercase ('[a-z]') or a dot ('\.'). The OR operator allows either of these to be matched. 
* In both cases, the OR operator provides alternatives within the character sets, allowing for different characters to be matched at those specific positions within the pattern. 

### Character Classes
* Character classes are enclosed within square brackets '[]' and allow us to define a gorup of characters that can match a single character at the specific position in the pattern. 
* Character classes are a way to specify a set of characters that can be matched at a particular position in a pattern
* Here are the character classes within our snippet code: 
    1. `[a-z0-9_\.-]`:
        * This character class matches any lowercase letter, digit, underscore, period, or hyphen.
    2. `[\da-z\.-]`:
        * This character class matches any digit, lowercase letter, period, or hyphen.
    3. `[a-z\.]`:
        * This character class matches any lowercase letter or period. 

### Flags
* Flags are optional modifiers that can be added after the closing delimiter of a regex pattern to modify the behavior of the pattern matching. There are no flags specified. 
* Here are some commonly used flags in regex:
    1. 'i'- Case Sensitive:
        * The 'i' flag enables case-insensitive matching. Uppercase and lowercase letters are considered equivalent. 
    2. 'g'- Global Search:
        * The 'g' flag performs a global search. It will find all matches rather than stopping at the first match. 
    3. 'm'- Multiline: 
        * The 'm' flag enables multiline mode. The anchors '^' and '$' match the beginning and end of each line within the input text, rather than the entire input string.
    4. 's'- Dotall or Single Line Mode: 
        * The 's' flag modifies the behavior of the dot metacharacter. By default the dot matches any character except newline. With the 's' flag thhe dot matches any character including the newline. 
    5. 'u'- Unicode: 
        * The 'u' flag enables full Unicode matching. It allows the regex engine to handle Unicode characters properly, including support for Unicode code point matching and properties. 

### Grouping and Capturing
* Grouping and capturing are techniques used to isolate and capture specific parts of a matched pattern
    * Grouping uses paranthesis. Placing part of a regex pattern inside the parenthesis creates a group
    * Capturing also uses paranthesis. When a group is created, the regex engine captures the text that matches the group.
    * There are 3 groups created using paranthesis in our snippet of code: 
        1. `([a-z0-9_\.-]+)`
            * This group captures the username part of the email address
        2. `([\da-z\.-]+)`
            * This group captures the domain name part of the email address
        3.`([a-z\.]{2,6})`
            * This group captures the top-level domain part of the email address.

### Bracket Expressions
* Character Classes are the same as Bracket Expressions. Using square brackets '[]' we specify a range or a list of characters to be matched. Please see Character Classes section of this gist. 

### Greedy and Lazy Match
1. Greedy Matching
    * Matching as much of the input as possible while still allowing the overall pattern to match. 
2. Lazy Matching
    * AKA non-greedy matching, appends the '?' to the quantifier. It tells the regex engine to match as little as possible while still allowing the pattern to match.

### Boundaries
* Boundaries are special characters or assertions that define the start or end of a word, line, or input. Commonly used Boundaries: 
    1. Word boundary '\b': 
        * Matches the position between a word character (\w) and a non-word character (\W). 
    2. Start of Line '^' and End of Line '$':
        * The ^ matches the start of a line and the $ sign matches the end of a line. 
    3. Start of Input '\A' and End of Input '\z':
        * The anchor '\A' matches the absolute start of the input and '\z' matches the absolute end of the input. Similar to start of line and end of line. 
    4. Word Start '\B' and Word End '\b':
        * The '\B' matches posiution that are not word boundaries. Any position that is not between 2 word characters or between 2 non-word characters. 

### Back-references
* Back-References allow us to refer to previously matched text and use it later in the same pattern or during replacement operations. Usually represented by the backslash '\' fullowed by a number or a name. 
    1. Numeric Back References: 
        * When using captured groups, each group is assigned a number starting from 1, based on the order of their opening. We can refer to these groups using '\n' where 'n' is the index of the group
    2. Named Back References:
        * When using captured groups, some can be named. You can refer to these groups using '\k"name"' 

* In our snippet of code. We have three groups so we can back reference them using their index. Since we have 3 groups:
        1. `([a-z0-9_\.-]+)`
            * Back Reference '\1'
        2. `([\da-z\.-]+)`
            * Back Reference '\2'
        3.`([a-z\.]{2,6})`
            * Back Reference '\3'
### Look-ahead and Look-behind
* Look ahead and look-behind, collectively called lookaround, mathces characters and only returns the result (match or no match). They only assert whether a match is possible or not. 

1. Positive Look-Ahead (?=...): 
    * It matches the current position if the pattern inside the look-ahead assertion matches, but it doesn't include the matched text in the overall match.
2. Negative Look-Ahead (?!...):
    * It matches the current position if the pattern inside the negative look-ahead assertion does not match.
3. Positive Look-Behind (?<=...):
    * It matches the current position if the pattern inside the look-behind assertion matches, but it doesn't include the matched text in the overall match.
4. Negative Look-Behind (?<!...):
    * It matches the current position if the pattern inside the negative look-behind assertion does not match.

## Credits
- [Power of Regular Expression](https://www.hallme.com/blog/the-power-of-regular-expressions/)  
- [Lookaround](https://www.regular-expressions.info/lookaround.html)  
- [Boundaries](https://www.regular-expressions.info/wordboundaries.html)  
- [Cheat Sheet](https://www.rexegg.com/regex-quickstart.html)  
- [Coding Bootcamp](https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial)  
## Author

* Ryan Kang- DU Coding Student:    
[My Github](https://github.com/RyanSKang/regex-tutorial)

