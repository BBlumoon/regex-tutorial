# Regex Tutorial

Introductory paragraph (replace this with your text)

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

### Anchors
- `abc$` -^start/$end of the string
    - `^` Matches the beginning of the string or the beginning of a line if the multiple flag (m) is enabled. This matches a position, not a character.
    - `$` Matches the end of the string or the end of a line if the multiline flag (m) is enabled. This also matches a position, not a character

- `\b\B` -word, non-word boundary
    - `\b` Matches a word boundary position that is between a word character and a non-word character or position (start/end of string). See the word character class (w) for more info.
    - `\B` Matches any position that is not a word boundary. This matches a position, not a character.

### Quantifiers
Quantifiers indicate that the preceding token must be matched by a certain number of times. A quantifier can be greedy or lazy which is further explained below.
- `a*a+a?` -0 or more, 1 or more, 0 or 1
    - '+' Matches 1 or more of the preceding tokens.
    - '*' Matches 0 or more of the preceding tokens.
    - '?' Matches 0 or 1 of the preceding tokens, making it optional.
    - '?' Makes the preceding quantifier lazy, causing to match as few characters as possible. By default, quantifiers are greedy, and will try to match as many characters as possible.

### OR Operator
- `|` Acts like a boolean OR. Matches the expression before or after the '|' character. It can operate within a group, or on a whole expression. The patterns will be tested in order. Just as in Java will match either set of characters. It will look for this OR that.

### Character Classes
Character classes match a character from a specific set. There are a number of predefined character classes and the user can also define their own sets.
- `[ABC]` Characters inside the bracket will match any character in the set.
- `[^ABC]` Adding a caret will match any character that is not in the set.
- `[A-Z]` Adding a dash between two characters will set a range.
- `.` Will match any characters, expect line breaks. It is like a wildcard and will accept any input
- `[\s\S]` A character set that can be used to match any character, including line breaks, without the dotall flag. An alternative to this is [^] caret in brackets, but it is not supported by all browsers.
- `\w` Matches any word character (alphanumeric & underscore). Only matches low-ascii characters (no accented or non-roman characters).
- `\W` Matches any character that is not a word character (alphanumeric & underscore).
- `\p` Matches any digit character (0-9).
- `\d` Matches a character in the specified unicode category.

### Flags
Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression.
- `i` Ignores case
- `g` Global search retain the index of the last match, allowing subsequent searches to start from the end of the previous match. Without the global flag, subsequent searches will return the same match.
- `m` Multiline flag. When the multiline flag is enabled, beginning and end anchors (^ and &) will match the start and end of a line, instead of the start and end of a whole string.
- `u` Unicode.
- `y` The expression will only match from is last index position and ignores the global (g) flag is set. Since each search in RegExr is discrete, this flag has no further impact on the displayed results.
- `s` Dot(.) will match any character, including new line.

NOTE: Unicode is an information technology standard for the consistent encoding, representation, and handling of text expressed in most of the world's writing systems

### Grouping and Capturing
- `(ABC)` Capturing groups multiple tokens together and creates a capture group for extracting a substring or using a back reference.
- `(?<name>ABC)` Named capturing group captures groups of a specific name
- `(?:ABC)` Groups multiple tokens together without creating a capture group
- `\1` Is a numeric reference

### Bracket Expressions
A bracket expression enclosed in square brackets is a regular expression that matches a single character, or collating element. If the initial character is a circumflex ^, then this bracket expression is complemented.

See Character Class to see some examples.

### Greedy and Lazy Match
- 'Greedy' means matching the longest possible string. A Greedy quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy.
- 'Lazy' means matching the shortest possible string. A lazy quantifier tells the engine to match as few of the quantified tokens as needed. As you'll see in the table below, a regular quantifier is made lazy by appending a ? question mark to it.

See [link]"https://javascript.info/regexp-greedy-and-lazy for more detailed information.

### Boundaries
`\b` An anchor like the caret and the dollar sign. It matches at a position that is called a 'word boundary'. This match is zero-length.

Characters that are matched by the short-hand character class `\w` are the characters that are treated as word characters by word boundaries.

Since digits are considered to be word characters, `\b4\b` can be used to match a 4 that is not part of a larger number. So saying \b matches before and after an alphanumeric sequence is more exact than saying “before and after a word”.

`\B` is the negated version of `\b`. `\B` matches at every position where `\b` does not. Effectively, `\B` matches at any position between two word characters as well as at any position between two non-word characters.

There are more boundries with the Regex Engine. Some examples include Tcl, GNU, and POSIX.

### Back-references
Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag.

For Example: `<([A-Z][0-9]*)\b[^>]*>.*?</\1>` This regex contains only one pair of parentheses, which capture the string matched by `[A-Z][0-9]*`. This is the opening HTML tag. The backreference `\1` references the first capturing group. `\1` matches the exact same text that was matched by the first capturing group. The `/` before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

### Look-ahead and Look-behind
-`(?=ABC)` is a postive lookahead and it matches a group after the main expression without including it in the result.

-`(?!ABC)` is a negitive lookahead and it specifies a group that can not match after the main expression (if it matches, the result is discarded)

-`(?<=ABC>)` is a postive lookbehind and matches a group before the main expression without including it in the result.

-`(?<!ABC)` is a negitive lookbehind and Specifies a group that can not match before the main expression (if it matches, the result is discarded).

Lookaheads and lookbehinds forces the main expressions to be what you have defined it as. Without it being exactly what it is it will not be accepted as a valid input.

## Author
Colin Moon: Rutgers Bootcamp student

* [regexr](https://regexr.com/)
* [BackRef](https://www.regular-expressions.info/backref.html)
* [RegExpression](https://www.regular-expressions.info/wordboundaries.html)

My github https://github.com/BBlumoon 
