Command Line
============

### Standard I/O

* While we have referred to the first thress of these file streams as standard input, output and error, the shell references them internally as file descriptors 0, 1 and 2.
* Using the pipe operator `|` the standard output of one command can be piped into the standard input of another.

  `command1 | command2`

* tee command: get standard input and copy it to both standard output and one or more files.

  `ls /usr/bin | tee abc.txt | grep zip`

### Expansion

* When used at the beginning of a word, the tilde character `~` expands into the name of the home directory of the named user or, if no user is named, the home directory of the current user

  ```
  $ echo ~foo
  /home/foo
  ```

* Shell allows arithmetic to be performed by expansion, using `$((expression))`. Expressions may be nested.
* Brace expansion `{}` help you create multiple text strings from a pattern containing braces. For example:

  ```
  $ echo Front-{A,B,C}-Back
  Front-A-Back Front-B-Back Front-C-Back
  ```

  Here is an example of using a range of integers:

  ```
  $ echo Number-{1..5}
  Number-1 Number-2 Number-3 Number-4 Number-5
  ```

  Here we get a range of letters in reverse order:

  ```
  $ echo {C..A}
  C B A
  ```

  Brace expansions may be nested

  ```
  $ echo a{A{1,2},B{3,4}}b
  aA1b aA2b aB3b aB4b
  ```

* To enable interpretration of backslash escapes with `echo`, using `-e` option.
