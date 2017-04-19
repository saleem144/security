**Metasploit:**



written in ruby 

Exploit research 

1. choose various shellcode to the exploit

Useful in every phase of the pentest

MSF -- unified and sensible interface to use all options

**START **

```
/etc/init.d/metasploit start
/etc/init.d/postgresql start
```

Explore exploits \(Aux modules\)

**Aux Modules**

1.show Auxilary : info gathering , scanning and enumeration etc 

```
show snmp
use /auxiliary/scanner/snmp/snmp_enum
show options
set RHOST 192.168.31.200-254
set THREADS 10
run

```

```
set global parameters can be used across various modules 
setg RHOSTS 192.168.31.200-254
setg THREADS 10

```



