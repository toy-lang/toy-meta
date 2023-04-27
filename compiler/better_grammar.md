# less ambiguous grammar

oh crap this is gonna take a long time...

```haskell
root_body = import
class_body = _

expr = caller | tuple | op | STRING | NUMBER | ARRAY | "true" | "false"
caller = IDENTIFIER"!"? tuple
tuple = ("(" expr ("," expr) * ")")

-- Ops
op = equality
equality = comparison (( "==" | "!=" ) comparison)? * -- Big thanks to crafting interpreters for helping with this part <3
comparison = term ( ( ">", ">=", "<" "<=" ) term )? *
term = factor ( ( "-" | "+" ) factor )? *
factor = pow ( ( "*" | "/" ) pow )? *
pow = unary ( "^" unary )? *
unary = ( "!" | "-" )? unary | primary
primary = expr

-- KEYWORDS/SIMILAR
import = "import" STRING ("as" expr)?
pup_attribute = "#![" attr_caller "]"
attribute = "#[" attr_caller "]"
attr_caller = IDENTIFIER ("(" attr_caller? "," * ")")?
fn = ("pub" | "pub(pup)")? "fn" 
```
