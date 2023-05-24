# RegEx Tuturial for Matching an Email

## Introduction

RegEx, or regular expression, is a sequence of characters that defines a search pattern for text. RegEx can be used to check if a string matches a specified pattern, or to extract the parts that match.

## Summary

In this gist, we will explain the RegEx for **matching an email**, which is:
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

This RegEx consists of several components, such as **anchors, quantifiers, grouping constructs, bracket expressions, character classes, OR operator, flags, and character escapes**. We will explain each of them in detail below.

## Table of Contents

- [RegEx Tuturial for Matching an Email](#regex-tuturial-for-matching-an-email)
  - [Introduction](#introduction)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [Anchors](#anchors)
    - [Quantifiers](#quantifiers)
    - [Grouping Constructs](#grouping-constructs)
    - [Bracket Expressions](#bracket-expressions)
    - [Character Classes](#character-classes)
    - [The OR Operator](#the-or-operator)
    - [Flags](#flags)
    - [Character Escapes](#character-escapes)
  - [Author](#author)

## Regex Components

### Anchors

In general, Anchors are special characters that specify the position of the match in the string. There are two types of anchors: `^` and `$`. The `^` anchor matches the beginning of the string. For example, `^a` matches any string that starts with `a`. The `$` anchor matches the end of the string. For example, `a$` matches any string that ends with `a`.

In our email-matching RegEx, we use both anchors to ensure that the whole string is an email address. The `^` anchor matches the start of the string, and the `$` anchor matches the end of the string. **This means that nothing can precede or follow the email pattern.** For example, this RegEx will match `alice@example.com`, but NOT `hello alice@example.com` or `alice@example.com bye` (because of space).

### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
