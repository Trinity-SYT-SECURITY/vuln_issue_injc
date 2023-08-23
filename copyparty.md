+ Vendor Homepage: https://github.com/9001/copyparty
+ version : 1.9.1
+ EXPLOIT-AUTHOR : Noflag(CHT Security)
+ Software Link : https://github.com/9001/copyparty/archive/refs/tags/v1.9.1.zip
+ Tested on: kali
+ vuln : markdown XSS vuln

vuln issue :
There is a WEEKEND-PLANS function under the "http://192.168.xx.xx/" directory location that allows users to add files in md format. If the user enters xss payload in it, the attack will be successfully executed.

Vulnerability location : 
![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/f06801b0-e1f1-4c2c-b4ea-1d1b185631d9)


POC :
![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/a81e091e-a3e2-4f9e-882c-14f9b56e26a7)

https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/568dc4df-ab68-4d58-bb00-b9b515a830da


