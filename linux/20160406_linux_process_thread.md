### Linux Processes, Threads, Lighweight Processes and Process State
* Processes have priority based on which kernel context switches them.
* In Linux, fork() is used to create new processes. These new processes are called as child processes and each child process initially shares all the segments like text, stack, heap etc until child tries to make any change to stack or heap. In case of any change, a separate copy of stack and heap segments are prepared for child so that changes remain child specific. The text segment is read-only so both parent and child share the same text segment.
* A Linux thread is a flow of process execution. A process containing multiple execution flows is known as multi-thread process.
* For Linux kernel, there is no concept of thread. Each thread is viewed by kernel as a seperate process but these processes are somewhat different from another normal processes. These processes are known as Lightweight Processes (LWP). LWPs share same address space and other resources like open files.
* Thread is a term that is used in user level while LWP is a term used at kernel level.
* Process States:
    + RUNNING - Process is either in execution or waiting to get executed.
    + INTERRUPTIBLE - Process is waiting to get interrupted as it is in sleep mode and waiting for some action to wake this process up.
    + UN-INTERRUPTIBLE - Same as INTERRUPTIBLE, the only difference being that a process in this state cannot be waken by delivering a signal. (Read [this](http://stackoverflow.com/questions/223644/what-is-an-uninterruptable-process) for more details.)
    + STOPPED - The process has ben stopped. This may happen if a signal like SIGSTOP, SIGTTIN... is delivered to the process.
    + TRACED - This state specifies that the process is being debugged. Whenever the process is stopped by debugger the process enters this state.
    + ZOMBIE - The process is terminated but still hanging around in kernel process table because the parent of this process has still not fetched the termination status of this process. Parents use `wait()` family of function to fetch the termination status.
    + DEAD - The process is terminated and entry is removed from process table. This state is achieved when the parent successfully fetches the termination status as explained in ZOMBIE state.
