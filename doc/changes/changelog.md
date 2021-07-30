**From July 09, 2020 to July 16, 2021 changelog:** 
1. Vulnerability list:  Add batch verification function
2. System configuration:  Enable/disable policy
3. Vulnerability details: Add taint parameter location mark to the data package
4. Vulnerability details: Vulnerability display data collection, project details, easy to troubleshoot
5. Component management: Component display data collection, project details, easy to troubleshoot
6. System configuration: Customize the rules page, add rules to view rules by rules, and support the enabling and disabling of single-selection/multiple-selection/all-selection operation strategies
7. Vulnerability list: sorting conditions support positive order and reverse order
8. Vulnerability details: add data package debugging function (historical data cannot be debugged, newly generated vulnerability data can be debugged)
9. Vulnerability details: Optimized the display data of the taint flow graph. By default, only the graph is displayed. Click the content on the graph to display the call data

****

**From July 05, 2021 to July 09, 2021 changelog**
1. Historical data processing: Language case inconsistency issues, unified handling as uppercase
2. Vulnerability status: Adding To be verified, verifying, confirmed, ignored
3. Vulnerability status: Adding To be verified, verifying, confirmed, ignored
4. Detection logic: Vulnerability verification is automatically triggered in data local mode, and only verified vulnerabilities are displayed by default; remote mode is good
5. Engine management: add running and not running label filter conditions
6. Organization management: add user password reset function
7. Organization management: Questionnaire survey data directly call webhook to create users and send emails

****

**June 19,2021 to July 2, 2021 changelog**
1. Vulnerability verification function is launched, including: single vulnerability verification, project vulnerability batch verification [need to enable `-Diast.server.mode=local` parameter to specify local mode to use]
2. POST request package display, taint(污点) location and taint value display [need to enable `-Diast.server.mode=local` parameter to specify local mode to use]
3. Fix the bug that the engine running status will not be updated
4. Fix the bug that the requested data package in the vulnerability details page will not be updated
5. Modify the default language to Java to solve the problem of inconsistent language case
6. The default status of the vulnerability is changed to "Pending"
7. Optimize the HTTP request acquisition method in Java Agent, optimize memory/CPU usage, and improve performance
8. Optimize the third-party components used in the Java Agent to reduce the size of the agent
9. IDEA plugin is officially open source

****

**From June 7,2021 to June 18,2021 changelog**

1. Project version function is launched
2. One-click start-stop function in the cloud is launched
3. Optimize the processing logic related to the configuration file in the agent to reduce performance loss. You can use the JVM parameter: `-Diast.engine.delay.time=600` to specify a delay of 10 minutes to start
4. Optimize the processing logic related to configuration files in the Agent to reduce performance loss
5. Deployment plan increased: docker-compose one-click deployment, k8s cluster one-click deployment
****

**From May 31,2021 to June 04,2021 changelog**

1. Vulnerability information adds functions such as viewing and editing of vulnerability status
2. Migrate the hook rules left on the Agent-end to the cloud
3. The "range" system increases the basic environment: keycloak13, gocd（from 17 version to 23 version), geoserver(from 2.12 version to 2.18 version), nifi(from 1.2 version to 1.12version), openapi-generator-online(from 3version to 5version); The basic environment can be used for vulnerability verification, vulnerability mining, etc. Welcome to use the “range”.
****

***From April 19,2021 to April 23,2021 changelog***
1. Modify cloud data to remove duplicate bugs and solve the problem of the same “range”. After a user scans the vulnerability, other users cannot detect the same vulnerability (appears in the openrasp “range”)
2. Vulnerability detection increased mode selection, including: hunter mode, normal mode, in hunter mode, the vulnerability detection rate is increased, and the false alarm rate is increased.Usage scenarios of hunter mode: code review. Usage scenarios of normal mode:Detect vulnerabilities within the enterprise. Hunter mode configuration: `-Diast.mode=hunter`
3. Data reporting increase mode selection, including local mode, remote mode, the remote mode uploads the hash of the taint, the local mode uploads the value of the taint (you can see the content and changes of the taint in detail); Local mode usage scenarios: code review, enterprise localization deployment. Local mode usage scenarios: code audit, enterprise localization deployment; The default is remote mode, local mode configuration:`-Diast.server.mode=local`
4. The agent supports configuration items, which can be automatically associated with the created project, and the newly created project can be automatically associated with the started agent. Configuration: `-Dproject.name=<project name>`
- User experience optimization
- The "range" increases the rapid positioning of the activated “range”
- Add hook rule
****

***March 17, 2021 changelog***

LingZhi IAST was renamed huoxian~ "DongTai IAST"
- Product update
- Hook rules support cloud configuration
****

***July 18,2020 changelog***

LingZhi IAST v0.3 version launched
- Fix bug: `ISSUES-1 Getting errors when fetching data`
- Optimize HOOK point processing logic, Add AGENT "close" function, Reduce performance loss caused by irrelevant methods hitting hooks
- Supplement the blacklist of HOOK points, Eliminate partially redundant hook points, improve response speed
- Supplement the missing rules in HQL injection and SSRF rules
****

**July 03,2020 changelog**
LingZhi IAST v0.2 version launched
- Fix the bug that the agent reported the vulnerability data error under the JDK
- Add a vulnerability detection rule for OGNL code execution
- Support windows system
****
***LingZhi IAST v0.1 community version launched***

LingZhi IAST v0.1 community version launched