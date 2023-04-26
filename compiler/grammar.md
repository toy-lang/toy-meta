# Grammar

```markdown
** Grammar syntax note: **

A newline inside of brackets is equal to a | operator unless preceded by a different *grammatical* operator.
-- is a comment
```
```haskell
expr = literal | grouping | unary | binary | comment | attribute

literal = IDENTIFIER | STRING or NUMBER or "true" or "false"
grouping = "(" expr ")"
unary = (
    ("!" | "-") expr
    -- expr ( "x" | "x" )
)
binary = (
    "+" | "-" | "*" | "/"                        -- Arithmatic
    "&" | "|" | ">" | "<" | ">" | ">=" | "=<"    -- Comparison
)
comment = (
    "//" ~ "\n" -- Single line
    "/*" ~ "*/" -- Multi line
)
attribute = ("#[" | "#![") expr ("]\n") -- Attribute (! for pup level)
```
