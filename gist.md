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
*Regex quantifiers are symbols and/or metacharacters that specify the number of occurences of a preceding element within the pattern. Controlling the repetition or quantification of a character, group, or class within the pattern. 
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

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
