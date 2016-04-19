### Call linux's command inside a ruby program

There's several ways to call a linux's command inside a ruby program:

* Use `%x` or `\``
  ```ruby
  %x(echo hi) #=> "hi\n"
  %x(echo hi >&2) #=> "" (prints 'hi' to stderr)

  `echo hi` #=> "hi\n"
  `echo hi >&2` #=> "" (prints 'hi' to stderr)
  ```
  This method returns the stdout, and redirect stderr to the program's.
* Use `system`
  ```ruby
  system 'echo hi' #=> true (prints 'hi')
  system 'echo hi >&2' #=> true (prints 'hi' to stderr)
  system 'exit 1' #=> nil
  ```
  This method returns `true` if the command was successful. It redirects all output to the program's. An error status is available in `$?`.
* Use `exec`
  ```ruby
  fork { exec 'sleep 60' } # you see a new process in top, "sleep", but no extra ruby process.
  exec 'echo hi' # prints 'hi'
  # the code will never get here
  ```
  This replaces the current process with the one created by the command.
* Use `spawn`
  ```ruby
  spawn 'sleep 1; echo one' #=> 430 (PID)
  spawn 'echo two' #=> 431
  sleep 2
  # this program will print "two\none"
  ```
  This method does not wait for the process to exit and returns the PID.
* Use `IO.popen`
  ```ruby
  io = IO.popen 'cat', 'r+'
  $stdout = io
  puts 'hi'
  $stdout = IO.new 0
  p io.read(1)
  io.close
  # prints '"h"'
  ```
  This method will return an IO objecct that represents the new processes' input/output.
* Use `Open3`
  ```ruby
  require 'open3'

  stdout, stderr, status = Open3.capture3(some_command)
  STDERR.puts stderr
  if status.successful?
    puts stdout
  else
    STDERR.puts "OH NO!"
  end
  ```
  `Open3` has several other functions for getting explicit access to the two output streams. It's similar to `popen`, but gives you access to stderr.
