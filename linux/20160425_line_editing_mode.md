### Line editing mode

Today when I read `The linux command line`, I found out that I can move the cursor to the end or start of a line in terminal using `Ctrl-E` and `Ctrl-A` respectively. But I failed to do this in my laptop. The reason is my `.bashrc` has a line that change the line editing interface to a `vi-like` mode
  `set -o vi`
The default editing mode is `emacs-like`, which you can achieved by running this command.
  `set -o emacs`
