# Grammar

```markdown
** Grammar syntax note: **

A newline inside of brackets is equal to a | operator unless preceded by a different *grammatical* operator.
-- is a comment
```
```haskell
expr = literal | tuple | unary | binary | comment | attribute | keyword_expr | block | dict | doc

run_fn = literal ("(" (expr ","?) * ")")
run_macro = literal ("[" | "{" | "<") (-) ("]" | "}" | "<")
literal = (IDENTIFIER | STRING | NUMBER | "true" | "false")
tuple = "(" expr ")"
unary = (
    ("!" | "-") expr
    -- expr ( "x" | "x" )
)
binary = (expr (
    "+" | "-" | "*" | "/"                                   -- Arithmatic
    "&" | "|" | ">" | "<" | ">" | ">=" | "=<"               -- Comparison
    "?"                                                     -- Other
    -- TODO: maybe change |= syntax?
    "=" | "+=" | "-=" | "*=" | "/=" | "?=" | "&=" | "|="    -- Assignments
) expr)
comment = (
    "//" ~ "\n" -- Single line
    "/*" ~ ("*/" escape "\\") -- Multi line
)
doc = (
    "#doc" ~ ("#/doc" escape "\\")
)
attribute = "\n"("#[" | "#![") expr ("]") -- Attribute (! for pup level)
keyword_expr = (
    "if" expr expr ("else" expr)?
    "for" expr expr
    expr "in" expr
    "while" expr expr
    ("pub" | "pub(pup)")? "fn" expr expr
    "proceed" expr
    "cotime" expr
)

block = "{" expr "}"
dict = "{" (expr (":" expr)? "=" expr)... "}"
```
