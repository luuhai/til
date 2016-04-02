# Execute external command inside Vim

* To execute an external command inside Vim, type `:! command`
* Using `v` to select some text, then type `! command`, the selected text will become stdin for the command, and then it will be replaced by the output of the command.
