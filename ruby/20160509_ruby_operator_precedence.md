### Ruby Operator Precedence

From highest to lowest

* Element reference, element set: `[]`, `[]=`
* Exponentiation: `**`
* Not, complement, unary plus and minus (method names for the last two are +@ and -@): `!`, `~`, `+`, `-`
* Multiple, divide and modulo: `*`, `/`, `%`
* Addition and subtraction: `+`, `-`
* Right and left bitwise shift: `>>`, `<<`
* Bitwise AND: `&`
* Bitwise exclusive OR or regular OR: `^`, `|`
* Comparison operators: `<=`, `<`, `>`, `>=`
* Equality and pattern match operators (`!=` and `!~` may not be defined as methods)
* Logical AND: `&&`
* Logical OR: `||`
* Range: `..`, `...`
* Ternary if-then-else: `? :`
* Assignment: `=`, `%=`, `/=`, `-=`, `+=`, `|=`, `&=`, `>>=`, `<<=`, `*=`, `&&=`, `||=`, `**=`
* Check if specified symbol defined: `defined?`
* Logical negation: `not`
* Logical composition: `or`, `and`
* Expression modifiers: `if`, `unless`, `while`, `until`
* Block expression: `begin/end`

Source: http://www.techotopia.com/index.php/Ruby_Operator_Precedence
