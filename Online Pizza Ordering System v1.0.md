+ Vendor Homepage: https://www.sourcecodester.com/php/16166/online-pizza-ordering-system-php-free-source-code.html
+ Software Link: https://www.sourcecodester.com/sites/default/files/download/oretnom23/php-opos.zip
+ Version: v1.0
+ Tested on: XAMPP win 10
+ vuln : XSS
+ exploit : <script>alert(1)</script>
+ cve id: CVE-2023-37150
+ CVSS v3.1: `AV:L/AC:L/PR:H/UI:R/S:U/C:L/I:L/A:L/E:F/RL:W/RC:R/CR:L/IR:L/AR:L/MAV:L/MAC:L/MPR:H/MUI:R/MS:U/MC:L/MI:L/MA:L`

![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/63831a13-4e9b-40c8-8e82-21c8496afe92)


I enter the XSS grammar webpage under the Category item under this page and there will be a response

http://localhost/opos/admin/index.php?page=categories

![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/eada90bb-239e-4930-9d6a-7366491b8114)
