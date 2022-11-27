# Regex tutorial - Matching a Hex Value

This will be a regex tutorial breaking down each component tied to this Hex Value regex.

The Hex Value regex in question: `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

Regex or Regular Expressions is essentially a compact way of matching patterns found in a string of words. Regex is commonly used as a method of validation for inputs.

For our Hex Value Regex, it may look daunting at first, but we can break it down into simple, digestable parts.

```
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

/^#?    ([a-f0-9]{6}|[a-f0-9]{3})   $/
```

Outer
| Anchor | Quantifier | Grouping | Anchor |
| ----------- | ----------- | ----------- | ----------- |
| `/^` | `#?` |  `(...)` |  `$/` |

Inner
| Bracket Expression | Quantifier | OR | Bracket Expression | Quantifier |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| `[a-f0-9]` | `{6}` |  `\|` |  `[a-f0-9]` | `{3}` |

## Table of Contents

- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [Grouping and Capturing](#grouping-and-capturing)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)

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
- `{ n }` = matches exactly `n` amount of characters
    - Sample: `["two", "three", "four"]`
    - `/\w{4}/` returns `["", "thre", "four"]`
- `{ n, }` = matches at least `n` amount of characters
    - Sample: `["five", "six", "seven"]`
    - `/\w{4,}/` returns `["five", "", "seven"]`
- `{ n, x }` = matches at least `n` amount of characters and at most `x` amount of characters
    - Sample: `["eight", "nine", "ten", "eleven"]`
    - `/\w{3,5}/` returns `["eight", "nine", "ten", ""]`

### Grouping and Capturing

We create capture groups by surrounding our regex in parentheses `( ... )` characters. This allows us to isolate or capture specific components of our Regex.

Sample: 
"CP3 870"

| Regex | Match | Returns | Replace | Returns |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| `/([A-Z0-9]{3}\s[A-Z0-9]{3})/` | True | `CP3 870` | $1 | `CP3 870` |
| `/[A-Z0-9]{3}\s([A-Z0-9]{3})/` | True | `CP3 870` | $1 | `870` |
| `/(([A-Z0-9]{3})\s([A-Z0-9]{3}))/` | True | `CP3 870` | $1, $2, $3 | `CP3 870, CP3, 870` |
| `/([A-Z0-9]{3})\s([A-Z0-9]{3})/` | True | `CP3 870` | $1-$2 | `CP3-870` |

### OR Operator

The OR operator `|` allows us to have more flexibility in our search options, giving us the choice to search multiple matches and return true if any of them are found.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/this\|that/` | False |
| `/great\|delicious/` | True | `delicious` |
| `/(t\|T)his\|(t\|T)hat/` | True | `This` |
| `/(?\|!\|.)/` | True | `!` |
| `/(c\|C)(a\|A)(k\|K)(e\|E)/` | True | `cake` |

## Bonus Section

### Character Classes

Character classes or Character sets is a way of specifying a select choice of characters, very similar in comparison to the OR operator. In fact, we can use the same example listed above for replacing the OR operator.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/[tT]his\|[tT]hat/` | True | `This` |
| `/[?!.]/` | True | `!` |
| `/[cC][aA][kK][eE]/` | True | `cake` |

### Greedy and Lazy Match

This is also not relevant to finding Hex Values but still relevant enough that it's worth covering. At it's core, a greedy match will search for the largest match within it's search area while a lazy match will search for the smallest match.

Sample:
`<a href="#about-me">About Me</a>`

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/<.*>/` | True | `<a href="#about-me">About Me</a>` |
| `/<.*?>/` | True | `<a href="#about-me">`, `</a>` |

### Boundaries

Boundaries are very helpful in finding strings of a specific length. So helpful that they are a necessary inclusion in the bonus section. Let's say for example we are trying to find words that have 4 letters, no more, no less.

Sample:
"This cake is delicious!"

| Regex | Match | Returns |
| ----------- | ----------- | ----------- |
| `/\b\w{4}\b/` | True | `This`, `cake` |

## Author

Ian Binstock

- GitHub: [Binnyboy1](https://github.com/Binnyboy1)
- Email: [ibinstock@outlook.com](mailto:ibinstock@outlook.com)
- Twitter: [Binnyboy](https://twitter.com/Binstock_Ian)
