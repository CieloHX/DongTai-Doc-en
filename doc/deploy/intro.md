## Introduction

![architecture](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Architecture_architecture.png)

The graph above shows the `high-level architecture` and `information flows` of DongTai IAST:

1. During the regular operation or security testing, the web application will receive an HTTP request from users.

2. DongTai IAST Agent will deploy alongside the web application to monitor and collect the data from the traffic, then send the data to the DongTai IAST Management Server.

3. All the collected data will be analyzed on DongTai IAST Management Server. Once a vulnerability is detected, the server will notify users of the finding. Users also can review the report with include vulnerable lines of code, runtime data, and remediation on the management server.


DongTai IAST consists of the following components:

- DongTai IAST Agent: 

  Use to monitor the data flow of a web application server. The agent monitor requests through code instrumentation and continuously collect data sends these data on to the DongTai IAST Management Server. 
  
  An IAST Agent would be installed on each web application server in case of multiple web applications were deployed on a single machine.

- DongTai IAST Management Server (SaaS): 
  
  The main component of the DongTai IAST architecture that produces the user interface, analyzes the data collected by DongTai IAST Agents to identify vulnerabilities, stores the vulnerabilities, generates vulnerabilities reports. It also notifies users of the finding vulnerabilities, displays the result details, provides Web-APIs, manages user, group, scanned web application projects, and custom rules. 
  
  The frontend of the component was built by `Vue` and `TypeScript` and its backend was built by `Django` and `Django Rest Framework`.

  Enterprises can deploy DongTai IAST Management Server internally by needed. Please refer to On-Premises Version `Open Source Program for Jointly Partnership` below for further information.


### On-Premises Version [Open Source Program for Jointly Partnership]

Get starts to apply DongTai IAST Open Source Program for Jointly Partnership.
[Register Link](https://jinshuju.net/f/PKPl99)



### Contact Us
DongTai IAST Officialy WeChat Account
<div style="text-align:left">
<img width="100" height="100" alt="dongtai_QRCode.jpg" data-origin="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg" src="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg">
</div>

