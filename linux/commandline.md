Command Line
============

### Standard I/O

* While we have referred to the first thress of these file streams as standard input, output and error, the shell references them internally as file descriptors 0, 1 and 2.
* Using the pipe operator `|` the standard output of one command can be piped into the standard input of another.
    `command1 | command2`
* tee command: get standard input and copy it to both standard output and one or more files.
    `ls /usr/bin | tee abc.txt | grep zip`
