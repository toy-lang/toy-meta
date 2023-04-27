# less ambiguous grammar

for a shorter read, use `grammar.md`.

```haskell
root_body = ( ( import ) ";"? ) | ""
code_body = ( ( expr ) ";"? ) | ""

idn = IDENTIFIER ( "::" INDENTIFIER )? * ( "." INDENTIFER )?
expr = caller | tuple | op | STRING | NUMBER | ARRAY | "true" | "false" | decl
caller = idn"!"? tuple
tuple = ("(" expr ("," expr) * ")")

-- Ops
op = equality
equality = comparison ( ( "==" | "!=" ) comparison )? * -- Big thanks to crafting interpreters for helping with this part <3
comparison = term ( ( ">", ">=", "<" "<=" ) term )? *
term = factor ( ( "-" | "+" ) factor )? *
factor = pow ( ( "*" | "/" ) pow )? *
pow = unary ( "^" unary )? *
unary = ( "!" | "-" )? unary | primary
primary = expr

-- KEYWORDS/SIMILAR
_import = "import" STRING ( "as" expr )? -- ignore the _ , its for syntax highlighting
pup_attribute = "#![" attr_caller "]"
attribute = "#[" attr_caller "]"
attr_caller = idn ( "(" attr_caller? "," * ")" )?
fn = ( "pub" | "pub(pup)" )? "fn"
decl = "let" "mut"? expr ( ":" expr )? ( "=" expr )?
proceed = "proceed" expr
await = "await" expr
```
