# An Intro to Regeular Expressions

Regular expressions (regex) are powerful tools for pattern matching and validation in strings. In this tutorial, we'll break down a regex that validates email addresses to understand how each part functions.

### What is a Regex?

A regular expression, commonly known as regex, is a sequence of characters that defines a search pattern. This search pattern can be used for various purposes in computer science, including:

1. **Search Operations**: Finding specific patterns within a text. For example, finding all email addresses in a document.
2. **Text Replacement**: Replacing parts of a string that match a pattern with a new string. For example, replacing all instances of "foo" with "bar".
3. **Input Validation**: Validating if input data meets certain criteria. For example, checking if a user's input matches the format of a valid email address.
4. **Text Parsing**: Extracting specific information from text. For example, parsing log files to extract timestamps or error messages.
5. **Syntax Highlighting**: In text editors and IDEs, regex is used to identify keywords and other elements of programming languages to apply syntax highlighting.

Regex is widely used in various programming languages, text editors, and tools for its efficiency in handling text-based operations.

### How is a Regex Structured?

A regex is composed of various components, each serving a specific purpose to define a search pattern's criteria. Here’s a breakdown of the common components:

1. **Literals**: Match the exact characters in the pattern. For example, `cat` matches the substring "cat" in the text.
2. **Metacharacters**: Characters with special meanings, such as `.` (any character), `^` (start of string), `$` (end of string), etc.
3. **Character Classes**: Defined within square brackets `[ ]`, they match any one character from the set. For example, `[a-z]` matches any lowercase letter.
4. **Quantifiers**: Specify the number of times an element should be matched. Common quantifiers include `*` (0 or more), `+` (1 or more), `?` (0 or 1), and `{n,m}` (between n and m times).
5. **Anchors**: Assert a position in the string. For example, `^` asserts the position at the start of the string and `$` at the end.
6. **Groups and Capturing**: Parentheses `( )` group parts of a pattern together and capture them for back-references. Non-capturing groups use `(?: )`.
7. **Alternation**: The pipe `|` acts as a logical OR to match one pattern or another.
8. **Escapes**: Use a backslash `\` to escape metacharacters and match them literally.

Understanding these components and how they interact is key to mastering regex.

## Summary

We'll be dissecting the following regex to understand its components and how it ensures that a string is a valid email address:

```regex
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

This regex ensures that an email address has the correct structure, including a local part, an "@" symbol, a domain name, and a top-level domain (TLD).

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors are used to match positions in a string, such as the start or end/

- `^`: Matches the start of the string.
- `$`: Matches the end of the string.

In our regex, `^` ensures that the string starts with the pattern, and `$` ensures that it ends with the pattern.

### Quantifiers

Quantifiers specify how many times an element can occur.

- `*`: Matches 0 or more of the preceding element.
- `+`: Matches 1 or more of the preceding element.
- `?`: Matches 0 or 1 of the preceding element.
- `{n}`: Matches exactly n of the preceding element.
- `{n,}`: Matches n or more of the preceding element.
- `{n,m}`: Matches between n and m of the preceding element.
  
In our regex:

- `+` after `[a-z0-9_\.-]` means the local part of the email must have one or more characters.
- `{2,6}` after `[a-z\.]` means the TLD must be between 2 and 6 characters long.

### Grouping Constructs

Grouping constructs group multiple tokens together and capture parts of the string.

- `()`: Capturing groups.

In our regex:

- `([a-z0-9_\.-]+)` captures the local part of the email.
- `([\da-z\.-]+)` captures the domain name.
- `([a-z\.]{2,6})` captures the TLD.

### Bracket Expressions

Bracket expressions (character classes) match any one of the enclosed characters.

- `[a-z0-9_\.-]`: Matches any lowercase letter, digit, underscore, dot, or hyphen.
- `[\da-z\.-]`: Matches any digit, lowercase letter, dot, or hyphen.
- `[a-z\.]`: Matches any lowercase letter or dot.

### Character Classes

Character classes define a set of characters to match.

- `\d`: Matches any digit (equivalent to [0-9]).
- `\w`: Matches any word character (equivalent to [a-zA-Z0-9_]).
- `\s`: Matches any whitespace character (equivalent to [ \t\n\r\f\v]).
- `\D`: Matches any non-digit.
- `\W`: Matches any non-word character.
- `\S`: Matches any non-whitespace character.

In our regex:

- `[\da-z\.-]` uses \d to include digits.

### The OR Operator

The OR operator (`|`) matches either the expression before or the expression after it.

Example:

```regex
cat|dog
```

This regex matches either "cat" or "dog".

### Flags

Flags modify the behavior of the regex. Common flags include:

- `i`: Case-insensitive matching.
- `g`: Global matching.
- `m`: Multiline matching.
- `s`: Dot matches newline characters.
- `u`: Unicode matching.
- `y`: Sticky matching.

Example:

```regex
/hello/i
```

This regex matches "hello" in a case-insensitive manner, so it would match "Hello", "HELLO", "heLLo", etc.

```regex
/foo/g
```

This regex finds all matches of "foo" in the string, not just the first one.

```regex
/^abc/m
```

With the `m` flag, this regex matches "abc" at the start of each line in a multi-line string, not just the start of the entire string.

### Character Escapes

Character escapes allow matching characters that have special meanings in regex.

- `\.`: Matches a literal dot.

In our regex, `\.` is used to match the dots in the domain and TLD parts.

## Author

This tutorial was created by Raul Santos, a web development student passionate about learning and sharing knowledge about regular expressions and other programming concepts. You can find more of my work on [Github](https://github.com/raulds-fmtx).
