# Regex tutorial - Matching a Hex Value

Introductory paragraph (replace this with your text)
`/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [OR Operator](#or-operator)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

A Regex at it's core is a literal, meaning that it should be treated as a constant that does not change in value. To indicate to our program that our Regex expression should be treated as a literal, we surround our expression with the slash `/ ... /` characters as you'll see soon.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/cake/` | True | `cake` |
| `/gross/` | False |

### Anchors

Anchors signify whether the search item is limited to the start and/or end of the search area. Without anchors, regex will search anywhere within the string.

- `^` - start anchor
- `$` - end anchor

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/^This/` | True | `This` |
| `/delicious!$/` | True | `delicious!` |
| `/^This cake is delicious!$/` | True | `This cake is delicious!` |
| `/^cake/` | False |
| `/cake$/` | False |
| `/^cake$/` | False |

### Bracket Expressions

Square brackets indicate that we are looking for a range of characters instead of a single character. We surround our range of characters with the square bracket `[ ... ]` characters.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/^[a-zA-Z]/` | True | `T` |
| `/^[A-Z]/` | True | `T` |
| `/^T/` | True | `T` |
| `/[a-z]/` | True | `his cake is delicious` |
| `/^[a-z]/` | False |
| `/[0-9]/` | False |

Sample:
"5 is an odd number"
| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/[13579]/` | True | `5` |
| `/[02468]/` | False |

Shorthands for some standard ranges are the following:

- `\w`: equivalent to `[a-zA-Z0-9]`
- `\d`: equivalent to `[0-9]`
- `\s`: equivalent to any whitespace such as spaces, tabs, or linebreaks

### OR Operator

The OR operator `|` allows us to have more flexibility in our search options, giving us the choice to search multiple matches and return true if any of them are found.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/this\|that/` | False |
| `/(t\|T)his\|(t\|T)hat/` | True | `This` |
| `/(?\|!\|.)/` | True | `!` |
| `/great\|delicious/` | True | `delicious` |
| `/(c\|C)(a\|A)(k\|K)(e\|E)/` | True | `cake` |

### Quantifiers

Quantifiers limit or determine how many matches we specify.

- `?` - "optional" (0 or 1)
    - Sample: `[-15, 250]`
    - `/-?\d/` returns `[-1, 2]`
- `+` - "at least one" (1+)
    - Sample: `[-15, 250]`
    - `/\d+/` returns `[15, 250]`
- `*` - "zero or more" (0+)
    - Sample: `["hey", "heyyyyy", "he"]`
    - `/hey*/` returns `["hey", "heyyyyy", "he"]`
    - `/y*/` returns `["y", "yyyyy", ""]`
- `{ n }` = matches exactly `n` amount of characters
    - Sample: `["two", "three", "four"]`
    - `/\w{4}/` returns `["", "thre", "four"]`
- `{ n, }` = matches at least `n` amount of characters
    - Sample: `["five", "six", "seven"]`
    - `/\w{4,}/` returns `["five", "", "seven"]`
- `{ n, x }` = matches at least `n` amount of characters and at most `x` amount of characters
    - Sample: `["eight", "nine", "ten", "eleven"]`
    - `/\w{3,5}/` returns `["eight", "nine", "ten", ""]`

### Character Classes

### Flags

### Grouping and Capturing

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
