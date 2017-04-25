**SMTP Enumeration:**

Under certain misconfiguration , we can gather info abt the host and networks

SMTP verbs: VRFY \(Verify user\)                --- can be absued by attacker

```
Connect to host having mail server 

nc -nv 192.168.31.215 25 
VRFY bob
250 (Successful execution)
550 (Failure)
```

**SNMP Enumeration \(161\):**

SNMP misconfigurations can dramatically lead to loads of information leakage

Based on UDP

Susceptible to IP spoofing and replay attacks

**SNMP MIB \(SNMP Management Information base\)**

```
nmap -sU --open -p 161 192.168.31.200-254 --open
```

```
onesixtyone -c community -i ips
```

Prob and query using SNMPWALK

```
snmpwalk -c public -v1 192.168.31.227
```

So much of information .

To get specific information :

mid-value for running processes -- 1.3.6.1.2.1.25.4.2.1.2

```
snmpwalk -c public -v1 192.168.31.227 1.3.6.1.2.1.25.4.2.1.2
snmpwalk -c public -v1 192.168.31.227 1.3.6.1.2.1.6.13.1.3
```



