can exec comm

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/f669a793-c431-4962-9c8a-3d121145b4f2)
![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/033e85cc-7365-4b47-9ff4-e78d583c1ede)
![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/9765f8aa-838c-4fc1-a8a4-5d54e9d57c22)
![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/d4edd296-d097-45c1-9ad1-d522867eda1b)

----
### Summary
SSTI:
found that SSTI payload can run in the application. Although most strings cannot be recognized in the application, they can be injected through SSTI attack syntax.

RCE:
Arbitrary commands can be executed through the application. This should not be a computer function.

### Details

Users can use system() to perform operations executed by arbitrary instructions. If the application is intended to be a calculator
, then such a function should not exist, and the user should check whether the input is a reasonable calculation formula.

### PoC

----
+ SSTI? 

can made it broken `{"`

example:

`; {{".__class__ }}`

`; {{".__class__.__mro__ }}`

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/ca00057d-f52e-48af-9b64-364ae1ad4fce)

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/a2a6fdc0-ea7b-4876-bb8f-ebc75cc9be07)


injection

+ {1+1}
  
![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/3036c64f-a171-403c-a5a3-c2927ac3d3d3)

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/6d2988f8-df37-495a-ad3f-6683d601dae9)

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/3b3a23ec-7621-4393-b5b1-2d25cdd550cd)


String

![image](https://github.com/Trinity-SYT-SECURITY/vuln_issue_injc/assets/96654161/57b67fc1-ca07-45ca-a166-278e108cb3f5)

------

+ RCE

![image](https://github.com/lcn2/calc/assets/96654161/9932cc87-25b1-4773-a548-43e49408ce5a)

![image](https://github.com/lcn2/calc/assets/96654161/8a1bfc96-0e77-4919-a4c0-b2b5eaea15ad)

This can also be combined with other methods to achieve the effect of local privilege escalation.

![image](https://github.com/lcn2/calc/assets/96654161/124c28c7-d854-4191-9759-091aac5e7d8d)

https://github.com/lcn2/calc/assets/96654161/443e6656-f9a6-43ef-aed5-7625369cff2b

### Impact

calc <=2.15.0.4

### Discoverer
+ CHT Security Noflag
+ Ball45
