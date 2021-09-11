 ![GitHub](https://img.shields.io/github/license/JustinWeicht/17-regex-tutorial)

  # 17-regex-tutorial

# Regex Tutorial

To begin, Regex is short for regular expressions(reg-ex). Regex is mainly used to parse through text content and look for specific patterns or inputs.

## Summary
High-level description of Regular Expressions, AKA RegEx: An expression that is used to ensure that specific matches/patterns are present within a String.

Practical implication that utilizes RegEx: 
Imagine registering an account for a new website - you typically have to enter in your email and create a password that contains specific characters. This is where Regex can be used to confirm that "@" and "." were both used in your email, You may have experienced ta similar response before - "Email must contain @ followed by .". This is RegEx. Using this example and quite a bit of reading, you will be able to learn the fundamentals of RegEx. 


## Table of Contents

- [17-regex-tutorial](#17-regex-tutorial)
- [Regex Tutorial](#regex-tutorial)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [Example](#example)
    - [Anchors](#anchors)
    - [Quantifiers](#quantifiers)
    - [Character Classes](#character-classes)
    - [Flags](#flags)
    - [Grouping and Capturing](#grouping-and-capturing)
    - [OR Operator](#or-operator)
    - [Bracket Expressions](#bracket-expressions)
    - [Greedy and Lazy Match](#greedy-and-lazy-match)
    - [Boundaries](#boundaries)
    - [Back-references](#back-references)
    - [Look-ahead and Look-behind](#look-ahead-and-look-behind)
  - [Author](#author)

## Regex Components

### Example
In this example we are checking for patterns/specific inputs in an email and password. 

RegEx example for the email: /^([a-z\d\._-]+)@([a-z\d_-]+)\.([a-z]{2,32})(\.[a-z]{2,8})?$/y
RegEx example for the password: /^([a-zA-Z0-9_-.~!@#$%^&*()=+<>,]{3,32})$/y

In the following document we will get started by breaking this example down so we can approach this more easily and understand whats happening inside of these examples.

### Anchors
Anchors are used to match a position within a string.

We are able to define the beginning and ending of a string by using '^' and '$' respectively. Furthermore we can use /b and /B to look for word boundaries and not word boundaries.

### Quantifiers
Quantifiers are used to ensure that the input is a certain length.

In our case we are using {3,32} because we want the password to be be at least 3 characters long and shorter than 32 as a whole.

### Character Classes
Character classes match the specified characters from a given set.

These are all of the character classes with their matching syntax beside:
 - Character Set [ABC]
 - Neglected Set [^ABC]
 - Range [A-Z]
 - Dot .
 - Match Any [\s\S]
 - Word \w
 - Not Word \W
 - Digit \d
 - Not Digit \D
 - Whitespace \s
 - Not Whitespace \S
 - Unicode Category \p{L}
 - Not Unicode Category \P{L}
 - Unicode Script \p{Han}
 - Not Unicode Script \P{Han}

In the example above we are checking for lowercase letters, uppercase letters, digits, and special characters [a-zA-Z0-9~!@#$%^&*()_=+<>,-].

### Flags
Flags alter how the Regex expression is interpreted. They are entered after the closing /.

 - Ignore Case: /i does exactly that - ignores case-sensitivity /i
 - Global Search: /g searches the entirety of the targeted document
 - Multiline: /m uses the beginning and end anchors to match the start and end of a line instead of a string
 - Unicode: /u enable use of unicode escapes in the form, but also makes other escapes more strict resulting in errors
 - Sticky: /y matches starting at the current position in the target string.
 - Dot: /. will match any character character, including a new line

### Grouping and Capturing
A grouping is preformed by using parenthesis within our expression.

 - Capturing Group (ABC)
 - Named Capturing Group (?<name>ABC) can be used to reference a group with a name
 - Numeric Reference (\w)a\1 will reference the first group whereas \2 would reference the second group
 - Non-Capturing Groups (?:ABC) groups tokens together without creating a capture group

In the example we group the character set and quantifier together for the password: ([a-zA-Z0-9~!@#$%^&*()_=+<>,-]{3,32}).

### OR Operator
With your newfound knowledge of grouping and capturing, let's discuss the OR Operator. OR Operators are contained within a group and use the "pipe" character(|) to separate the values (x|y). Multiple pipes can be used if multiple values are required (x|y|z). Since our example doesn't use an OR operator we will look at a new one that does.

OR Operator Example:
We have a (cat|dog), and love to (snuggle|walk) him.

The example OR Operator would match any of the following input strings:
We have a cat, and love to snuggle him.
We have a cat, and love to walk him.
We have a dog, and love to snuggle him.
We have a dog, and love to walk him.

As you can see - any combination of words and/or values in the OR Operator will result in a match.

### Bracket Expressions
A bracket expression used to check for a matching or non-matching expression. This expression uses a set of square brackets([]). Any independent character within these brackets will be matched, example below.

- Match independent characters: ^[AbCdeFGHi]$
- Match a specific string of characters: ^[this is a string]$
- Exclude characters from match: [^AbCdeFGHi]
- Special characters such as '.', ',', '*', '[', and '\\' will lose their properties while inside of a bracket expression

### Greedy and Lazy Match
We'll discuss a Greedy Match, then explain what it does. Afterwards we will look at an example of each match type and compare it to our example. 

A greedy match acts like it's title - it's greedy, and attempts to match every position in the string. Furthermore, it will search the next position if there isn't a match. Let's compare a Lazy, Greedy and our example to one another.

Greedy Example:
RegEx: /".+"/g
String: 'a "witch" and her "broom" is one'
Result: "witch" and her "broom"

Lazy Example:
RegEx: /".+?"/g
String: 'a "witch" and her "broom" is one'
Result: "witch" "broom"

Our Example:
RegEx: /^([a-z\d\._-]+)@([a-z\d_-]+)\.([a-z]{2,32})(\.[a-z]{2,8})?$/y
String: justinweicht11@gmail.com
Result:   Match 1: justinweicht11@gmail.com
          Group 1: justinweicht11
          Group 2: gmail
          Group 3: com

Our greedy match quantifiers are the '+' symbols before the closing parenthesis. ie: ( -_]+)
The lazy match quantifier is the '?' after the last closing parenthesis. ie: 8})?$/y

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author
Created by: [JustinWeicht](https://github.com/JustinWeicht)
  
If you have questions regarding this tutorial, please contact me at: [justinweicht11@gmail.com](justinweicht11@gmail.com)
