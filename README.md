# Process scheduling in Linux  

This exercise is to show you how to use Linux’s scheduling policies for different processes. You will be creating three processes, where each of the three processes will count from 1 to 2^32. The three processes should be created with fork() and thereafter the child processes should use execl() family system calls to run another C file which will do the counting mentioned above.

Reiterating you need to launch three processes, each of which calls another process (the counting process).

The following should be the detailed specification of each of the process, to begin with:

1. **Process 1:** Uses SCHED OTHER scheduling discipline with standard priority (nice:0).

2. **Process 2:** Uses SCHED RR scheduling discipline with default priority.

3. **Process 3:** Uses SCHED FIFO scheduling discipline with default priority.

Each of these processes must time the process of counting from 1 to 2^32. To time the execution, the parent process could get the clock timestamp (using clock_gettime()) before the fork and after each process terminates (the event of which could be identified when the blocking system call waitpid() returns).

We require you to benchmark these three schedulers by changing the scheduling classes of the three processes. You would require generating histograms showing which scheduler completes the task when, depending upon the scheduling policy. You may choose different colors for the histogram bars, with one axis showing the time to complete, and the other showing the scheduling priorities. (You may use python to plot the histogram.)

**Hint:** To correctly benchmark scheduling policy, remember that all the three processes should be in READY state and then it is the policy that decides which process to give the CPU first.

**Grading Rubric:**
- Successful compilation of the program.
- Appropriately used system calls to create processes with the system calls to set the scheduling discipline and their priorities.
- Error Handling.
- Program runtimes and their variations due to the different process scheduling policies and priorities along with their histogram plot showing the same. (With reproducible behavior)
- Makefile to compile the above programs.
- README/Write-up describing the program logic used for achieving the above (no more than one page) and an explanation of the outcomes of the tests/measurements.

---
