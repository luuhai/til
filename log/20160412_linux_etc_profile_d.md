### Shell environment

* When you open a terminal emulator (like `gnome-terminal`), you're executing what's called interactive, non-login shell.
* When you log into your machine from the command line, via `ssh`, or run a command such as `su username`, you're running an interactive login shell.
* When you log in graphically, the details depend on your system but in general it is the graphical shell that deals with your login. Why many graphical shell will read `/etc/profile` not all of them do
* When you run a shell script, it is a non-interactive, non-login shell.

* `/etc/profile` in invoked only for login shells. It will be run by all [Bourne-compatible shells](http://en.wikipedia.org/wiki/Unix_shell#Bourne_shell_compatible) (including `bash` and `dash`) when started as a login shell.
* `/etc/profile` includes commands to call files inside `/etc/profile.d/` by default.
