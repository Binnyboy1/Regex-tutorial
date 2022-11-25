# Regex tutorial - Matching a Hex Value

Introductory paragraph (replace this with your text)
`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

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

A Regex at it's core is a literal, meaning that it should be treated as a constant that does not change in value. To indicate to our program that our Regex expression should be treated as a literal, we surround our expression with the slash `/ ... /` characters as you'll see soon.

Sample:
"This cake is delicious!"

- `/cake/` returns true
- `/gross/` returns false

### Anchors

Anchors signify whether the search item is limited to the start and/or end of the search area.

- `^` - start anchor
- `$` - end anchor

Sample:
"This cake is delicious!"

- `/^This/` returns true
- `/delicious!$/` returns true
- `/^This cake is delicious!$/` returns true
- `/^cake/` returns false
- `/cake$/` returns false
- `/^cake$/` returns false

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

Square brackets indicate that we are looking for a range of characters instead of a single character. We surround our range of characters with the square bracket `[ ... ]` characters.

Sample:
"This cake is delicious!"

- `^[a-zA-Z]` returns true
- `^[A-Z]` returns true
- `^T` returns true
- `^[a-z]` returns false
- `[0-9]` returns false

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
