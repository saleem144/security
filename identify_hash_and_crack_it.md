# Offline password cracking

We might find passwords or other credentials in databases. These are often hashed, so we need to first identify which hash it is and then try to crack it. The first step is to identify the hash-algorithm that was used to hash the password.

## Identify hash

There are generally speaking three pieces of data we can use to identify a hash.

* The length of the hash
* The character set
* Any special characters

In order to identify a hash we can either use specialized tools that analyze the hash and then return a guess on which algorithm it is. An easier way is of course to just look in the documentation of the software where you found the hashes. It usually says in the documentation or the source code which type of hash is being used.

In kali we can use `hash-identifier` or `hashid`:

```
hash-identifier 
hashid
```

Or try these online services:

[http://www.onlinehashcrack.com/hash-identification.php](http://www.onlinehashcrack.com/hash-identification.php)

[https://md5hashing.net/hash\_type\_checker](https://md5hashing.net/hash_type_checker)

## Cracking the hash

Okay so now we know what hash it is, let's get cracking.

If you want to try out the functionality of hashcat or john the ripper you can find example hashes here: [http://openwall.info/wiki/john/sample-hashes](http://openwall.info/wiki/john/sample-hashes).

### Hashcat

Look for the specific type of hash you want to crack in the list produced by the following command:

```
hashcat --help
```

My hash was a Apache md5, so I will use the corresponding code for it, `1600`

`-a 0` - straight

`-o found.txt` - where the cracked hash outputs

\`admin.hash" - the hash you want to crack.

`/usr/share/hashcat/rules/rockyou-30000.rule` - the wordlist we use

```
hashcat -m 11 -a 0 -o found.txt admin.hash /usr/share/hashcat/rules/rockyou-30000.rule
```

### John the ripper

So this is how you usually crack passwords with john

```
john --wordlist=wordlist.txt dump.txt
```

If you do not find the password you can add the john-rules. Which add numbers and such things to each password.

```
john --rules --wordlist=wordlist.txt dump.txt
```

#### Linux shadow password

First you need to combine the passwd file with the shadow file using the unshadow-program.

```
unshadow passwd-file.txt shadow-file.txt > unshadowed.txt
john --rules --wordlist=wordlist.txt unshadowed.txt
```

### Rainbow tables

So basically a rainbow table is a precalculated list of passwords. So instead of having to hash the word you want to try you create a list of hashes. So you do not have to hash them before comparing. This might take a long time to do, hashing a whole wordlist, but when you do the comparison between the password and the test-word it will go a lot faster.

## Using Online Tools

### findmyhash

You can use findmyhash

Here is an example of how to use it:

```
findmyhash LM -h 6c3d4c343f999422aad3b435b51404ee:bcd477bfdb45435a34c6a38403ca4364
```

### Cracking

Crackstation  
[https://crackstation.net/](https://crackstation.net/)

Hashkiller  
[https://hashkiller.co.uk/](https://hashkiller.co.uk/)

Google hashes  
Search pastebin.

## Windows

If you find a local file inclusion vulnerability you might be able to retrieve two fundamental files from it. the `system` registry and the `SAM` registry. There two files/registries are all we need to get the machines hashes.  
These files can be found in several different locations in windows. Here they are:

```
Systemroot can be windows
%SYSTEMROOT%\repair\SAM
windows\repair\SAM
%SYSTEMROOT%\System32\config\RegBack\SAM

System file can be found here
SYSTEMROOT%\repair\system
%SYSTEMROOT%\System32\config\RegBack\system
```

So if the manage to get your hands on both of these files you can extract the password hashed like this:

```
pwdump system sam
```

One more way to use the sam file :

**1. **Bkhive to extract the bootkey

**2. **Using Samdump2 to recover Windows hashes



```
root@bt:~# cat sam
```

 The SAM file is obfuscated because the Windows Syskey utility encrypts the password hashes inside the SAM file with 128-bit Rivest Cipher 4 \(RC4\). Syskey utility is called the bootkey, and it’s stored in the Windows SYSTEM file. key to reverse the encrypted hashes

```
root@kali:~# bkhive system xpkey.txt
bkhive 1.1.1 by Objectif Securite
http://www.objectif-securite.ch
original author: ncuomo@studenti.unina.it
Root Key : $$$PROTO.HIV
Default ControlSet: 001
Bootkey: 015777ab072930b22020b999557f42d5
```

```
root@kali:~# samdump2 sam xpkey.txt
samdump2 1.1.1 by Objectif Securite
http://www.objectif-securite.ch
original author: ncuomo@studenti.unina.it
Root Key : SAM
Administrator:500:e52cac67419a9a224a3b108f3fa6cb6d:8846f7eaee8fb117ad06bdd830b7586c:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
HelpAssistant:1000:df40c521ef762bb7b9767e30ff112a3c:938ce7d211ea733373bcfc3e6fbb3641:::
SUPPORT_388945a0:1002:aad3b435b51404eeaad3b435b51404ee:bc48640a0fcb55c6ba1c9955080a52a8:::
```

Ref : [https://repo.zenk-security.com/Magazine%20E-book/Penetration%20Testing%20-%20A%20hands-on%20introduction%20to%20Hacking.pdf](https://repo.zenk-security.com/Magazine%20E-book/Penetration%20Testing%20-%20A%20hands-on%20introduction%20to%20Hacking.pdf)

