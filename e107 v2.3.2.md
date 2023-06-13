# e107 v2.3.2 

+ Vendor Homepage　: https://e107.org/
+ Software Link　: https://e107.org/download
+ Version　: 2.3.2
+ Testeted on　: Windows 10 using XAMPP
+ issue :　Stored XSS (Cross-Site Scripting)
+ payload : https://gist.github.com/kurobeats/9a613c9ab68914312cbb415134795b45

> This is where admins add new content to the main page
![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/ae4716e9-1395-4c4b-8d87-9cd8d8e46c4f)

Affected position:
http://localhost/e107/e107_admin/newspost.php?mode=main&action=edit&id=6

When I went to add content, under the SEO project, there was a Description, and the management page had a restricted <script> string format, so I had to use other XSS scripts to bypass the restriction

![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/03369764-30b8-492a-8293-22f5cafb42dc)
  
![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/a20dd002-4bda-4469-858f-795441984f06)

After pressing update. 

It will return to the previous page http://localhost/e107/e107_admin/newspost.php?mode=main&action=list , and you can see that the content just typed in Description will be displayed

https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/b1068704-a64b-4bdd-8263-72e2240971e6

![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/96a156fd-ca60-4d5c-b931-eea30591ffd7)
  
**Refer to github's XSS Vectors Cheat Sheet, some will work, some will be blocked**
  
```"><h1><IFRAME SRC="javascript:alert('XSS');"></IFRAME>">123</h1>```
  
+ This is the screen displayed on the front end
![image](https://github.com/Trinity-SYT-SECURITY/XSS_vuln_issue/assets/96654161/d824aa58-28c9-4e63-a545-cdbc05dfec7a)

