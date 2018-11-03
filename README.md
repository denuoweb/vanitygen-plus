-----
Vanitygen PLUS for Htmlcoin!  
-----

**Download the latest linux binary from Releases**  

**WARNING!** This program has not been thoroughly tested.  Please attempt importing an address first.  
Send a tiny amount you don't mind losing to the address.  Then perform a test spend.  
I will not be held liable for lost funds as a result of the use of this program.  

----
Getting Started  
-----  
**Download the latest binary!** 

1 - Extract the files,  
2 - Open a terminal/command prompt,  
3 - Change to the directory to vanitygen-plus 

Running On Linux: `./vanitygen -ARGS`, or `./oclvanitygen -ARGS`, `./keyconv -ARGS`, etc  
Running On Windows is not ready yet: `vanitygen.exe -ARGS`, `oclvanitygen.exe -ARGS`, `keyconv.exe -ARGS`, etc  

 

**For generating addresses using the CPU(slower) use: vanitygen !**  
**For generating addresses using the GPU(faster) use: oclvanitygen !**  

**NOTES:**	All arguments are case sensitive!  
	Address prefix must be at the end of the command.  
	oclvanitygen requires OpenCL and correct drivers.   


**Now lets generate a HTML address with the prefix "Htest":**  
Linux CPU: `./vanitygen -C HTML -o results.txt -i -k Htest`  
Linux GPU: `./oclvanitygen -C HTML -o results.txt -i -k Htest`  
Windows CPU: `vanitygen.exe -C HTML -o results.txt -i -k Htest`  
Windows GPU: `oclvanitygen.exe -C HTML -o results.txt -i -k Htest`  

 * `-C HTML` : Chooses the HTML coin  
 * `-o results.txt` : saves the matches to results.txt  
 * `-i` : case-Insensitive(do not add this flag to match exact case)  
 * `-k` : keep going even after match is found(do not add this flag to stop after the first match)  
 * `Htest` : the address you are searching for(HTML addresses start with "H")  

Example output of above command:  
>Generating HTML Address  
>Difficulty: 4553521  
>HTML Pattern: Htest                                                                  
>HTML Address: Htest6jSVcid5MQAJBrGUR6MLDpdyb8oiQ  
>HTML Privkey: wrRxctq3f7A1zkpyWoZRifRk5eAC2UM9idh83SPLhz6gAFfqdL  

**If you have dependency errors on Linux  
or need instructions for compiling from source(Kaling Rolling/Linux) see link below:**  
https://legacysecuritygroup.com/index.php/projects/recent/12-software/35-oclvanitygen-compiling-and-use  

------  
Fix libcrypto.so.1.0.2 error(Debian, Ubuntu)  
------  
Error:
>./vanitygen: error while loading shared libraries: libcrypto.so.1.0.2: cannot open shared object file: No such file or directory  

Fix it by issuing the below commands, in turn either installing or downgrading libcrypto.  The error comes from an incompatibility with the newer version of libcrypto.  Most older projects have this same bug.  
```
wget http://ftp.us.debian.org/debian/pool/main/g/glibc/libc6-udeb_2.24-11+deb9u3_amd64.udeb
dpkg -i libc6-udeb_2.24-11+deb9u3_amd64.udeb
wget http://ftp.us.debian.org/debian/pool/main/o/openssl1.0/libcrypto1.0.2-udeb_1.0.2l-2+deb9u3_amd64.udeb
dpkg -i libcrypto1.0.2-udeb_1.0.2l-2+deb9u3_amd64.udeb
rm libc6-udeb_2.24-11+deb9u3_amd64.udeb && rm libcrypto1.0.2-udeb_1.0.2l-2+deb9u3_amd64.udeb 
```
-----
Encrypting and Decrypting a vanitygen or oclvanitygen private key  
-----  
**Encrypting generated private key:**  
Linux: `./vanitygen -E password -C HTML Ha`  
Windows: `./vanitygen -E password -C HTML Ha`  
*For GPU use "oclvanitygen" in place of "vanitygen"*  

 * `-C HTML Ha` Choose Htmlcoin and address prefix "Ha"  
 * `-E password` Encrypt key with password as "password",  
**NOTE:** It is more secure to use option `-e` with no trailing password,  
then vanitygen prompts for a password so theres no command history.  
Also please choose a stronger password than "password".  

>Generating HTML Address  
>Difficulty: 23   
>HTML Pattern: Ha                                                                      
>HTML Address: Ha853vQs6QGrTuTHb7Q45tbeB8n4EL47vd  
>HTML Protkey: yTYFUWAsgFmMxCbKtu3RdrrJXosZrjxiQFA2o43neB4jPpfLe5owNNrteTs8mpvua8Ge  

**Decrypting generated ProtKey with Keyconv:**  
Linux: `./keyconv -C HTML -d yTYFUWAsgFmMxCbKtu3RdrrJXosZrjxiQFA2o43neB4jPpfLe5owNNrteTs8mpvua8Ge`  
Windows: `keyconv.exe -C HTML -d yTYFUWAsgFmMxCbKtu3RdrrJXosZrjxiQFA2o43neB4jPpfLe5owNNrteTs8mpvua8Ge`  

 * `-C HTML` Specifies Htmlcoin  
 * `-d` means decrypt the protected key of "yTYFUWAsgFmMxCbKtu3RdrrJXosZrjxiQFA2o43neB4jPpfLe5owNNrteTs8mpvua8Ge"  

>Enter import password:  --- Enter "password" or whatever you specified as password and press enter  
>Address: Ha853vQs6QGrTuTHb7Q45tbeB8n4EL47vd  
>Privkey: 66GRP2W5H4sWbgrBRAuPc3qZxUtP5boubJ9N2M5wZio6fhWjzbr  
