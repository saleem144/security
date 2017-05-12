Main ways of identifying flaws in applications:

1. If source code is available , then source code review 
2. If application is close sourced, then reverse engineering
3. Fuzzing to find bugs

**Fuzzing :**

Fuzzing involves sending malformed data into application input and watching for unexpected crashes.

An unexpected crash indicates that the application might not filter certain input correctly. This could lead to discovering an exploitable vulnerability

**Steps:**

1. Fuzzing and crash replication
   1. Create a fuzzing script and find the exact location where the crash occurs.
   2. Recreate the crash with the modified script and run it
   3. Attach the application to the debugger and find the register values \( ESP and EIP\) after the pause of debugger
2. Controlling the EIP
   1. Ruby Pattern creator 
   2. Getting our input to load into EIP and get the location 
   3. 
3. ShellCode
4. Bad Character
5. Redirecting Execution
6. Mona
7. Shell Execution





