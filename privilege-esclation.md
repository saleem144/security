## Fundamentals:

\(1\) during pentesting engagements a low-priv shell is often all the proof you need for the customer,

\(2\) in staged environments you often pop the Administrator account,

\(3\) meterpreter makes you lazy \(getsystem = lazy-fu\),

\(4\) build reviews to often end up being --&gt; authenticated nessus scan, microsoft security baseline analyser

#### OS -&gt; User -&gt;Permission-&gt;Network Interfaces-&gt;scheduled tasks-&gt;

#### 

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

Now we have this basic information we list the other user accounts on the box and view our own user's information in a bit more detail. We can already see that Machine is part of the localgroup Administrators.

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

We got to know about users and permissions  . next we need to know abt networking , wht is the machine connected to and what rules does it impose on those connections.

Network interfaces:

```
C:\Windows>ipconfig /all  | more

Windows IP Configuration

   Host Name . . . . . . . . . . . . : saleem
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Ethernet:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 68-F7-28-A0-14-24
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Qualcomm Atheros AR956x Wireless Network Adapter
   Physical Address. . . . . . . . . : D0-53-49-CF-5E-17
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::4c65:3518:f6b3:cbd%17(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.15.104(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 31 March 2017 14:25:56
   Lease Expires . . . . . . . . . . : 01 April 2017 18:25:48
   Default Gateway . . . . . . . . . : 192.168.15.1
   DHCP Server . . . . . . . . . . . : 192.168.15.1
   DHCPv6 IAID . . . . . . . . . . . : 365974345
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1D-AF-10-44-68-F7-28-A0-14-24
   DNS Servers . . . . . . . . . . . : 192.168.15.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

Routing Table:

```
C:\Windows>route print
C:\Windows> arp -A

Interface: 192.168.132.1 --- 0x2
  Internet Address      Physical Address      Type
  192.168.132.254       00-50-56-e2-f5-22     dynamic
  192.168.132.255       ff-ff-ff-ff-ff-ff     static
  224.0.0.2             01-00-5e-00-00-02     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static

Interface: 192.168.223.1 --- 0x4
  Internet Address      Physical Address      Type
  192.168.223.254       00-50-56-e6-d4-62     dynamic
  192.168.223.255       ff-ff-ff-ff-ff-ff     static
  224.0.0.2             01-00-5e-00-00-02     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static

Interface: 192.168.15.104 --- 0x11
  Internet Address      Physical Address      Type
  192.168.15.1          98-de-d0-28-3d-46     dynamic
  192.168.15.103        34-de-1a-53-be-cf     dynamic
  192.168.15.255        ff-ff-ff-ff-ff-ff     static
  224.0.0.2             01-00-5e-00-00-02     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
```

 active network connections and the firewall rules.

```
C:\Windows\system32> netstat -ano
C:\Windows\system32> netsh firewall show state
C:\Windows\system32> netsh firewall show config
```

Finally we will take a brief look at the what is running on the compromised box: scheduled tasks, running processes, started services and installed drivers.

```
C:\Windows\system32> schtasks /query /fo LIST /v

# The following command links running processes to started services.

C:\Windows\system32> tasklist /SVC

#These Windows services are started

C:\Windows\system32> net start



```





