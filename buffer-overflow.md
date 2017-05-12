Main ways of identifying flaws in applications:

1. If source code is available , then source code review 
2. If application is close sourced, then reverse engineering
3. Fuzzing to find bugs

**Fuzzing :**

Fuzzing involves sending malformed data into application input and watching for  
 unexpected crashes.

An unexpected crash indicates that the application might not filter certain input correctly. This could lead to discovering an exploitable vulnerability

**Steps:**

1. Fuzzing and crash replication
   1. Create a fuzzing script and find the exact location whr the crash occurs.\(Attach process 2 debugger & enable the putty\)
   2. Once debugger is attached pauses the process , press the play button to allow debugger to release the process and run normally
   3. run the fuzzer prog , at one point debugger pauses and allow use to analyze
   4. F2 to set the breakpoint
   5. Recreate the crash with the modified script and run it
   6. find the register values \( ESP and EIP\) after the pause of debugger
2. Controlling the EIP \(controls execution flow of the prog\)
   1. Locate the EIP position in our buffer
   2. Ruby Pattern creator tool - to create the unique buffer strings
   3. we could figure out unique four bytes in our buffer
   4. pattern-offset : gives position of the four unique bytes
   5. Now we replace the value with the user controlled bytes 
   6. Control the execution flow of the application , by changing the specific \(EIP\) Bytes
3. ShellCode \(User entered code\)
   1. once the shellcode is in memory we can redirect the execution of the application to this shell code
   2.  we need to increase the size of the buffer in order to accommodate the shellcode \(3500\)
4. Bad Character

   1. certain character are considered bad , should not be used in the buffer , return address, shellcode  ex: NOP, \r etc

   2. 

1. Redirecting Execution
2. Mona
3. Shell Execution



