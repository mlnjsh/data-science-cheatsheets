# Regex Cheatsheet

## Basic Patterns

| Pattern | Matches |
|---------|---------|
| `.` | Any character except newline |
| `\d` | Digit [0-9] |
| `\D` | Non-digit |
| `\w` | Word char [a-zA-Z0-9_] |
| `\W` | Non-word char |
| `\s` | Whitespace |
| `\S` | Non-whitespace |
| `\b` | Word boundary |

## Quantifiers

| Pattern | Meaning |
|---------|---------|
| `*` | 0 or more |
| `+` | 1 or more |
| `?` | 0 or 1 |
| `{3}` | Exactly 3 |
| `{2,5}` | 2 to 5 |
| `{3,}` | 3 or more |

## Anchors and Groups

| Pattern | Meaning |
|---------|---------|
| `^` | Start of string |
| `$` | End of string |
| `(abc)` | Capture group |
| `(?:abc)` | Non-capture group |
| `a\|b` | a OR b |
| `[abc]` | Character class (a, b, or c) |
| `[^abc]` | NOT a, b, or c |
| `[a-z]` | Range |

## Common Patterns

```python
import re

# Email
r'[\w.+-]+@[\w-]+\.[\w.]+'

# Phone (US)
r'\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}'

# URL
r'https?://[\w./\-?=&#]+'

# IP Address
r'\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}'

# Date (YYYY-MM-DD)
r'\d{4}-\d{2}-\d{2}'

# Numbers (with optional decimal)
r'-?\d+\.?\d*'
```

## Python re Module

```python
import re

re.search(pattern, string)       # First match
re.match(pattern, string)        # Match at start only
re.findall(pattern, string)      # All matches (list)
re.finditer(pattern, string)     # All matches (iterator)
re.sub(pattern, repl, string)    # Replace
re.split(pattern, string)        # Split

# Named groups
m = re.search(r'(?P<year>\d{4})-(?P<month>\d{2})', '2024-01-15')
m.group('year')   # '2024'
m.group('month')  # '01'
```

## Flags

```python
re.IGNORECASE  # or re.I — case insensitive
re.MULTILINE   # or re.M — ^ and $ match line boundaries
re.DOTALL      # or re.S — . matches newline too
re.VERBOSE     # or re.X — allow comments in pattern
```
