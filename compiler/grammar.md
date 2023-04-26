# Grammar

```markdown
** Grammar syntax note: **

A newline inside of brackets is equal to a | operator unless preceded by a different *grammatical* operator.
-- is a comment
```
```haskell
expr = literal | grouping | unary | binary | comment | attribute | keyword_expr | block | dict | doc

literal = IDENTIFIER | STRING | NUMBER | "true" | "false"
grouping = "(" expr ")"
unary = (
    ("!" | "-") expr
    -- expr ( "x" | "x" )
)
binary = expr (
    "+" | "-" | "*" | "/"                                   -- Arithmatic
    "&" | "|" | ">" | "<" | ">" | ">=" | "=<"               -- Comparison
    "?"                                                     -- Other
    -- TODO: maybe change |= syntax?
    "=" | "+=" | "-=" | "*=" | "/=" | "?=" | "&=" | "|="    -- Assignments
) expr
comment = (
    "//" ~ "\n" -- Single line
    "/*" ~ "*/" -- Multi line
)
doc = (
    "#doc" ~ "#\doc"
)
attribute = "\n"("#[" | "#![") expr ("]") -- Attribute (! for pup level)
keyword_expr = (
    "if" expr block ("else" block)?
    "for" expr block
    expr "in" expr
    "while" expr block
)

block = "{" expr "}"
dict = "{" (expr (":" expr)? "=" expr)... "}"

NOTE keywords = [ if else for in while ]
```
