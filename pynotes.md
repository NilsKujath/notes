# Python Notes

## Basics

### Variable Assignment
`=` is used to assign a value (RHS) to a variable (LHS).
Trying to access an undefinied variable will produce an error.
It is possible to assign multiple variables at the same time: `a, b = 1, 2`.

### Math Operators
Comments start with `#` and extend to the end of the line.
Basic math operators are `+`, `-`, `*`, `/` (devision always returns a float).
Floor devision `//` discards any fractional result and returns an integer
Modulo division `%` calculates the remainder.
`**` calculates LHS to the power of RHS.
In interactive mode, the last printed expression it assigned the variable `_`.
If operands are of mixed type (flaot and int), the int is automatically converted to a float.

### Comparison Opertors
`<` (less than), `>` (greater than), `==` (equal to), `<=` (less than or equal to), `>=` (greater than or equal to), `!=` (not equal to).

### Strings
Strings can be enclosed in single quotes `'...'` or double quotes `"..."` (`\` can be used to escape quotes).
Strings can be concatenated with `+` and repeated with `*`.
Ther is no extra character type, a single character is a string of size 1.
A specific character of a string is indexed: if `word = python`, `word[0]` would return `p`.
If indexes are negative numbers, the counting starts from the right.
Slicing allows to obtain a substring: `word[0:2]` would return `py` (characters from pos 0 (incl) to pos 2 (excl)).
An omitted first index `word[:2]` defaults to zero, an omitted second index `word[4:]` defaults to the size of the string being sliced.
```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

### Lists
`listname = [1, 2, 3, 4, 5]`. Lists can be indexed and sliced.
Lists are mutable: `listname[3] = 3` returns `[1, 2, 3, 3, 5]`.
Lists can be nested (that is, it is possible for lists to contain other lists).

## Flow Control

Statements always end in a `NEWLINE`.

### if Statement
```
if_stmt ::=  "if" assignment_expression ":" suite
             ("elif" assignment_expression ":" suite)*
             ["else" ":" suite]
```

### while Statement (Loop)
```
while_stmt ::=  "while" assignment_expression ":" suite
                ["else" ":" suite]
```

### for Statement
```
for_stmt ::=  "for" target_list "in" expression_list ":" suite
              ["else" ":" suite]
```
Can also be done with the range function: `for i in range(5):`.

### break Statement
`break` breaks out of the innermost enclosing of a `for` or `while` loop.

### continue Statement
`continue` continues with the next itiration of the loop.


## Notes on Built-in Functions

### round()
`round(<number> [, <ndigits>])` returns <number> rounded to <ndigits> after the decimal point.
If <ndigits> is ommited or None, it returns the neares integer to its input.

### print()
`print(*objects, sep='', end='\n', file=sys.stdout, flush=False)` all non-keyword arguments are converted to strings like `str()` does and written to the stream.
prefixing a string with r as in `print(r'...')` avoids the interpretations of characters prefixed by `\` as special characters.

## len()
`len(s)` returns the length of an object `s`.

## range() (class)
range is an immutable sequence type. The given end point is never part of the generated sequence.























