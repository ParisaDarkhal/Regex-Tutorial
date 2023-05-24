# RegEx Tutorial for Matching an Email

## Introduction

RegEx, or regular expression, is a sequence of characters that defines a search pattern for text. RegEx can be used to check if a string matches a specified pattern, or to extract the parts that match.

## Summary

In this gist, we will explain the RegEx for **matching an email**, which is:
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

This RegEx consists of several components, such as **anchors, quantifiers, grouping constructs, bracket expressions, character classes, OR operator, flags, and character escapes**. We will explain each of them in detail below.

## Table of Contents

- [RegEx Tutorial for Matching an Email](#regex-tutorial-for-matching-an-email)
  - [Introduction](#introduction)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [**Anchors**](#anchors)
    - [**Quantifiers**](#quantifiers)
    - [**Grouping Constructs**](#grouping-constructs)
    - [**Bracket Expressions**](#bracket-expressions)
    - [**Character Classes**](#character-classes)
    - [**The OR Operator**](#the-or-operator)
    - [**Flags**](#flags)
    - [**Character Escapes**](#character-escapes)
  - [**Author**](#author)

## Regex Components

### **Anchors**

In general, Anchors are special characters that specify the position of the match in the string. There are two types of anchors: `^` and `$`. The `^` anchor matches the beginning of the string. For example, `^a` matches any string that starts with `a`. The `$` anchor matches the end of the string. For example, `a$` matches any string that ends with `a`.

In our email-matching RegEx, we use both anchors to ensure that the whole string is an email address. The `^` anchor matches the start of the string, and the `$` anchor matches the end of the string. **This means that nothing can precede or follow the email pattern.** For example, this RegEx will match `alice@example.com`, but NOT `hello alice@example.com` or `alice@example.com bye` (because of space).

### **Quantifiers**

Quantifiers are special characters that specify how many times a character or a group of characters can be repeated in the match. There are several types of quantifiers: `*`, `+`, `?`, `{n}`, `{n,m}`, and `{n,}`. Here we explain them individually:

- The `*` quantifier matches **zero or more** times. For example, `a*` matches any string that contains zero or more `a`s.
- The `+` quantifier matches **one or more** times. For example, `a+` matches any string that contains one or more `a`s.
- The `?` quantifier matches **zero or one** time. For example, `a?` matches any string that contains zero or one `a`.
- The `{n}` quantifier matches **exactly n times**. For example, `a{3}` matches any string that contains exactly three `a`s.
- The `{n,m}` quantifier matches **between n and m times**, inclusive. For example, `a{2,4}` matches any string that contains between two and four `a`s.
- The `{n,}` quantifier matches **at least n times**. For example, `a{2,}` matches any string that contains at least two `a`s.

We can see some of these quantifiers in our email-matching RegEx:

- The first part of the email address RegEx is `[a-z0-9_\.-]+` . This means that it can contain **one or more characters** from the range `[a-z]`, `[0-9]`, `_` (underline), `.` (literal dot), or `-` (dash). For example, this part can match `alice`, `bob123`, or `john.doe`. As you see, some of the characters that have specific meaning in RegEx explanation (such as `.` or `-`), become literal when they go inside the brackets.
- The second part of the email address RegEx is `[\da-z\.-]+`. This means that it can contain **one or more characters** from the range [0-9] (because of `\d`), `[a-z]`, `.` (dot), or `-`. For example, this part can match example, `gmail`, or `co.uk`.
- The third part of the email address RegEx is `[a-z\.]{2,6}`. This means that it can contain **between two and six characters** from the range `[a-z]` or `.` (dot). For example, this part can match `.com`, `.org`, or `.co.in`.

### **Grouping Constructs**

Grouping constructs are special characters that group parts of the RegEx together and capture them as submatches. There are two types of grouping constructs: parentheses `( )` and non-capturing parentheses `(?: )`.

- The parentheses `( )` create a capturing group, which means that the part of the string that matches the group can be accessed later by using a backreference `\n`, where n is the number of the group. For example, `(a)\1` matches any string that contains two consecutive `a`s.
- The non-capturing parentheses `(?: )` create a non-capturing group, which means that the part of the string that matches the group is not stored for later use. This is useful for applying quantifiers or alternation to a group without capturing it. For example, `(?:ab)+` matches any string that contains one or more repetitions of ab.

In our email-matching RegEx, we use three capturing groups to separate each part of the email address. The first group is`([a-z0-9_\.-]+)`, which captures the user name part. The second group is `([\da-z\.-]+)`, which captures the domain name part. The third group is `([a-z.]{2,6})`, which captures the top-level domain part. It is interesting that we can use these groups to access each part of the email address later by using backreferences `\1`, `\2`, and `\3`. For example, we can use `\1@\2.\3` to reconstruct the email address from its parts.

### **Bracket Expressions**

Bracket expressions are special characters that specify a set or a range of characters to match. A bracket expression starts with `[` and ends with `]`. Inside the brackets, we can list individual characters or ranges separated by `-`. We can also use a caret `^` at the beginning to negate the set and match any character except those listed.
For example, `[abc]` matches any character from the set `{a,b,c}`. `[a-c]` matches any character from the range `{a,b,c}`. `[abcx-z]` matches any character from the set `{a,b,c,x,y,z}`. `[^abc]` matches any character except those from the set `{a,b,c}`.

In our email-matching RegEx, we use several bracket expressions to specify the allowed characters for each part of the email address.

- The first bracket expression is `[a-z0-9_\.-]`. This means that it can match any character from the range `[a-z]`, `[0-9]`, `_` , `.` , or `-`.
- The second bracket expression is `[\da-z\.-]`. This means that it can match any character from `\d`, which is equivalent to `[0-9]`, `[a-z]`, `.` , or `-`.
- The third bracket expression is `[a-z\.]`. This means that it can match any character from `[a-z]` or `.`

### **Character Classes**

A character class is a special notation that matches any one of a specified set of characters. A character class is enclosed by square brackets `[ ]`. Inside the brackets, we can list individual characters or ranges separated by `-`. We can also use a caret `^` at the beginning to negate the set and match any character except those listed.
For example, `[abc]` matches any character from the set `{a,b,c}`. `[a-c]` matches any character from the range `{a,b,c}`. `[abcx-z]` matches any character from the set `{a,b,c,x,y,z}`. `[^abc]` matches any character except those from the set `{a,b,c}`.
In our email-matching RegEx, we use several character classes to specify the allowed characters for each part of the email address.

- The first character class is `[a-z0-9_\.-]`. This means that it can match any character from the range `[a-z]`, `[0-9]`, `_`, `.` , or `-`.
- The second character class is `[\da-z\.-]`. This means that it can match any character from `\d`, which is equivalent to `[0-9]`, `[a-z]`, `.` , or `-`.
- The third character class is `[a-z\.]`. This means that it can match any character from `[a-z]` or .

### **The OR Operator**

The OR operator is a special character that matches either one of two alternatives. The OR operator is denoted by a vertical bar `|`. The OR operator has the lowest precedence among all RegEx operators, so it is usually used with parentheses `( )` to group the alternatives. For example, `(a|b)` matches either `a` or `b`. `(red|blue|green)` matches either `red`, `blue`, or `green`.

In our email-matching RegEx, we do not use the OR operator explicitly, but we can think of some parts of the RegEx as using it implicitly. For example, the bracket expression `[a-z0-9_\.-]` can be seen as matching either one of the characters inside the brackets. Similarly, the grouping construct `([a-z\.]{2,6})` can be seen as matching either one of the possible top-level domains that have between two and six characters from `[a-z]` or `.` .

### **Flags**

Flags are special characters that modify the behavior of the RegEx. Flags are usually added after the closing delimiter `/` of the RegEx. There are several flags available in different RegEx engines, but we will focus on three common ones: `i`, `g`, and `m`.

- The `i` flag stands for **case-insensitive**. It makes the RegEx match both uppercase and lowercase letters. For example, `/a/i` matches both `A` and `a`.
- The `g` flag stands for global. It makes the RegEx match **all occurrences** of the pattern in the string, not just the first one. For example, `/a/g` matches all `a`s in the string.
- The `m` flag stands for multiline. It makes the anchors `^` and `$` match the **beginning** and **end** of each line in the string, not just the whole string. For example, `/^a/m` matches any line that starts with `a`.

In our email-matching RegEx, we do not use any flags explicitly, but we can add them if we want to change the behavior of the RegEx. For example, if we want to match email addresses that have uppercase letters as well as lowercase letters, we can add the `i` flag like this:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/i`

### **Character Escapes**

A character escape is a special notation that **matches a literal character that has a special meaning** in RegEx. A character escape is denoted by a backslash `\` followed by the character to be escaped. For example, `\.` matches a literal dot `.`, not any character as it would without the backslash.

In our email-matching RegEx, we use several character escapes to match literal dots and dashes in the email address. For example, `\.` matches a dot between the domain name and the top-level domain. `\.` also matches a dot within the top-level domain. `\.` also matches a dot within the user name or domain name if they contain one. Similarly, `\-` matches a dash within the user name or domain name if they contain one.

## **Author**

This tutorial is prepared by Parisa Darkhal, a GitHub user and developer. You can find her GitHub profile link here:

[Parisa Darkhal](https://github.com/parisadarkhal)
