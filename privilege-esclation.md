## Fundamentals:

\(1\) during pentesting engagements a low-priv shell is often all the proof you need for the customer,

\(2\) in staged environments you often pop the Administrator account,

\(3\) meterpreter makes you lazy \(getsystem = lazy-fu\),

\(4\) build reviews to often end up being --&gt; authenticated nessus scan, microsoft security baseline analyser

#### **Initial Information Gathering**

First let's find out what OS we are connected to:

```
C:\Windows>systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.14393 N/A Build 14393
```

Next we will see what the hostname is of the box and what user we are connected as.

```
C:\Windows>hostname
saleem

C:\Windows>echo %username%
Machine

```

Now we have this basic information we list the other user accounts on the box and view our own user's information in a bit more detail. We can already see that user1 is not part of the localgroup Administrators.

```
C:\Windows>net users

User accounts for \\SALEEM

-------------------------------------------------------------------------------
Administrator            DefaultAccount           Guest
Machine
The command completed successfully.


C:\Windows>net user Machine
User name                    Machine
Full Name
Comment
User's comment
Country/region code          000 (System Default)
Account active               Yes
Account expires              Never

Password last set            13-10-2015 22:18:02
Password expires             Never
Password changeable          13-10-2015 22:18:02
Password required            No
User may change password     Yes

Workstations allowed         All
Logon script
User profile
Home directory
Last logon                   31-03-2017 14:25:57

Logon hours allowed          All

Local Group Memberships      *Administrators
Global Group memberships     *None
The command completed successfully.
```



