# Basic

* Package `main` defines a standalone executable program, not a library.
* Within package `main`, the function `main` is where execution of the program begins.
* We must to tell the compiler what packages are needed in a source file using the `import` declaration that follows the `package` declaration.
* You must import exactly the packages you need. A program will not compile if there're missing packages or unnecessary ones.
* Unlike most languages in C-family, in Go, `i++` and `i--` is statements, not expressions, so command like `j = i++` is illegal. They're also postfix only, so `--i` is not legal either.
* `for` loop is the only loop statement in Go.
