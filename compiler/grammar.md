# Grammar

```markdown
** Grammar syntax note: **

A newline inside of brackets is equal to a | operator unless preceded by a different *grammatical* operator.
-- is a comment
```
```haskell
expr = literal | grouping | unary | binary | comment | attribute | keyword_expr | block | dict

literal = IDENTIFIER | STRING | NUMBER | "true" | "false"
grouping = "(" expr ")"
unary = (
    ("!" | "-") expr
    -- expr ( "x" | "x" )
)
binary = expr (
    "+" | "-" | "*" | "/"                        -- Arithmatic
    "&" | "|" | ">" | "<" | ">" | ">=" | "=<"    -- Comparison
    "?" |
    "=" -- set
) expr
comment = (
    "//" ~ "\n" -- Single line
    "/*" ~ "*/" -- Multi line
)
attribute = ("#[" | "#![") expr ("]\n") -- Attribute (! for pup level)
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
