### Interpreter, Just-In-Time, Ahead-Of-Time

![Interpreter vs Compiler](https://i.stack.imgur.com/QhN1E.png)

* Compiler's generated code is faster, because a lot of work are done only once (lexing, parsing, type-checking, optimisation...), while interpreter has to redo them.
* AOT compilers often don't have enough information to do `agressive` optimisation.
* JIT seeks more aggressive optimisation by executing at run time. To prevent to do a full compilation cycle, many JIT compilers compile (and optimise) only hot code, and interpret the rest.
* `Hot code`: the tiny fragment of code that costs majority of a program's execution time (Pareto Principle).
* Discover hot code using counter.

![JIT](https://i.stack.imgur.com/soPN8.png)
