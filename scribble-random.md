







linux utilities to file or locate files



1. Locate command: 

Updatedb -- to update the db of the OS

Ex: locate sbd.exe 



2. Which command :

Ex: which sbd : prg can be found under /usr/bin/

3. find command:

Ex: find / -name sbd\*

all files lower case sbd and file format.

find \ -name sbd\* -exec file{} \;



Services:

passwd : change the old and weak pass to new stron gpassword

1. SSH Services : Secure shell

EX : netstat -antp \| grep sshd

Service ssh stop 

2. HTTP Server:

TCP based  and downlad the malicious file to victim

Ex: services spache2 start 

 echo "kali linux rocks" &gt; /var/www/index.html

3. services management : wrapper around /etc/init.d

4.Service persistant 

update -rc.d ssh enable

update-rc.d apache2 enable

RC conf also can be used

bash scripting



1. cat index.html l grep "href="
2. cat index.html \| grep "href=" \| cut -d

Essestial Tools:

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

 





