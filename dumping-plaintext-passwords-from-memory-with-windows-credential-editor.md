** Dumping Plaintext Passwords from Memory with Windows Credential Editor**

Why bother cracking password hashes if we can get access to plaintext passwords? If we have access to a Windows system, in some cases we can pull plaintext passwords directly from memory.

Windows Credential Editor \(WCE\) :  upload this tool to an exploited target system, and it will pull plaintext passwords from the Local 214 Chapter 9 Security Authority Subsystem Service \(LSASS\) process in charge of enforcing the system’s security policy

```
C:\>wce.exe -w
```

Ref: [http://www.ampliasecurity.com/research/wcefaq.html](http://www.ampliasecurity.com/research/wcefaq.html)

