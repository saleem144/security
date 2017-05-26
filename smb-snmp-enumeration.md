**SMB Enumeration:**

Scan for smb port in IP range

```
nmap -p 139,445 192.168.31.200-254 --open
```

specific tools to  identify SMB , NETBIOS

```
nbtscan 192.168.31.200-254
```

**SMB Null Session :** \(UnAuthenticated netbios session between two hosts\)

To obtain info about the machine . Its imp info for attacker.

Useful tool to explore remote SMB service is rpcclient

```
rpcclient -U "" 192.168.31.206
```

logged to remote windows machine using no credentials usig SMB service

```
 srvinfo -- system info
 enumdomuser -- users
 getdompwdinfo -- password policy
```

enum4linux -- Perl wrapper around the tools like rpcclient

```
enum4linux -v 192.168.31.206
```

user name , password policies etc

**Nmap SMB NSE checks:**

```
ls -l /usr/share/nmap/scripts/ | grep smb
```

check for the smb related scripts in nmap nse directory noe try to use the specific nse script

```
nmap -p 139,445 --script smb-enum-users 192.168.31.206
```

enumerate the users

check for major vulnerabilities \(Exploits\) in SMB service

```
nmap -p 139,445 --script=smb-check-vulns --script-args=unsafe=1 192.168.31.229
```



