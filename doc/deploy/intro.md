## Introduction

![architecture](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Architecture_architecture.png)

The graph above shows the `system context diagram` of DongTai IAST:

1. During the regular operation or security testing, the web application will receive HTTP requests from users.

2. DongTai IAST Agent will deploy alongside the web application to monitor and collect the data from the traffic, then send the data to the DongTai IAST Management Server.

3. All the collected data will be analyzed on DongTai IAST Management Server. Once a vulnerability is detected, the server will notify users of the finding. Users also can review the report with include vulnerable lines of code, runtime data, and remediation on the management server.


DongTai IAST consists of the following components:

- DongTai IAST Agent: 

  Use to monitor the data flow of a web application server. The Agent will monitor requests through code instrumentation and continuously collect data, then sends these data on to the DongTai IAST Management Server. 
  
  An IAST Agent would be installed on each web application server in case of multiple web applications were deployed on a single machine.

- DongTai IAST Management Server (SaaS): 
  
  The main component of the DongTai IAST architecture that produces the user interface, analyzes the data collected by DongTai IAST Agents to identify vulnerabilities, stores the vulnerabilities and generates vulnerabilities reports. It also notifies users of the finding vulnerabilities, displays the result details, provides Web-APIs, manages user, group, scanned web application projects, and custom rules. 
  
  The frontend of the component was built by `Vue` and `TypeScript` and its backend was built by `Django` and `Django Rest Framework`.

  Enterprises can deploy DongTai IAST Management Server internally by needed. Please refer to On-Premises Version `Open Source Program for Jointly Partnership` below for further information.

## High-Level Architecture
![architecture](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Architecture_diagram.png)

The graph above is the `high-level architecture` of DongTai IAST, it is a component diagram zooms into the software system in scope. We will describe the using component and how do they work in the following.

- DongTai IAST Client-Side Component: 
  - `Agent`: Deploy alongside with the web application, use to monitor the data flow of a web application server. It will collect the data and send the data to the DongTai IAST Server via OpenApi. The Agent will pull and apply the users’ change from the server every time after restart the web application.

- DongTai IAST Server-Side Component: 
  - `Web`: A management interface for users to manage user groups, scanned web application project, vulnerability report, agent, custom rule, etc.
  - `WebAPi`: Use to handle the requests from users and response the result to them.
  - `OpenAPi`: Use to collect data from the Client-Side Agent and storage the data into the database. It also checks the availability of the Agent by monitor the log sent back by such as heartbeat.
  - `Database`: Storage user, scanned project, report, agent’s rule, raw data collect from Agent etc.
  - `Engine`: Assign the analysis task to Engine Task.
  - `Engine Task`: Retrieve the task from Engine, it will analyze the collected data by the knowledge base of rulepack to identify vulnerability. Once the vulnerability was detected, it will store the vulnerability detail in the database and trigger notification component to notify users of the found.
  - `Notification`: A third party API used to notify users.

## Architecture Diagram
![architecture_diagram](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Architecture_diagram-step.png)

- Diagram of Vulnerabilities Detection: 
`A-1 ~ A-5`
  - A-1: During the regular operation or security testing, the web application will receive HTTP requests from users.
  - A-2: DongTai IAST `Agent` will deploy alongside the web application to monitor and collect the data from the traffic, then send the data to the DongTai IAST Management Server via `OpenAPI`.
  - A-3: Once `OpenAPI` received the data, it will store the data into the database and trigger `Engine`.
  - A-4: `Engine` will assign the analysis task to `Engine Task` to start analysis. The collected data from the database will be analyzed and the detail of the vulnerability will be stored once identified 
  - A-5: At the same time, users will receive notification of the vulnerability found.

- Diagram of Management: 
`B-1 ~ B-4`
  - B-1, B-2: `WebApi` will handle the request such as user group management requests, vulnerabilities reviews, etc. from users via `Web`.
  - B-3, B-4: After that, `WebApi` will respond to the result from the database to users and display it on `Web`.

- Diagram of Modify Agent Setting: 
`C-1 ~ C-4`
  - C-1, C-2: `WebApi` will handle the request from user via `Web` and stored the change in the database.
  - C-4, C-3: Once the client web application restart, Agent will pull and apply the change via `OpenApi`.

### On-Premises Version [Open Source Program for Jointly Partnership]

Get starts to join DongTai IAST Open Source Program for Jointly Partnership.
[Register Link](https://jinshuju.net/f/PKPl99)

### Contact Us
DongTai IAST Officialy WeChat Account
<div style="text-align:left">
<img width="100" height="100" alt="dongtai_QRCode.jpg" data-origin="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg" src="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg">
</div>

