> Interactive Application Security Testing (Interactive Application Security Testing) is a new application security testing program proposed by Gartner in 2012. It uses an agent deployed on the web server of the tested application to monitor traffic sent during runtime and analyzes traffic flow to identify security vulnerabilities in real-time. IAST delivers speed by providing test results directly and clearly, and it includes the type of vulnerability and exact location in the source code of the application.IAST is equivalent to a combination of DAST and SAST, an interrelated runtime security detection technology.

In 2021, "LingZhi IAST" upgraded to "DongTai IAST", improving vulnerability detection capabilities, product experience and services. At the same time, the SaaS version of the IAST products is launching. For details, see the [Quick start](en-us/doc/tutorial/quickstart).

## IAST Categories
- Active IAST
- Passive IAST

#### Active IAST
Active IAST is the approach of combines a DAST solution (web scanner) with an agent that works inside the application server. The agent will validate an existing vulnerability from the value provided by web scanner.

#### Passive IAST
Passive IAST also requires the instrumentation of the application with an agent in the security testing environment. It will leverage any form of functional testing (input, request, database,.etc.) to collect data and deliver accurate security findings, so it doesn’t require actively running a dedicated test attack.


## DongTai IAST
1."DongTai IAST" is passive IAST, it has the advantage of high accuracy detection and the speed of real-time actionable results.

2."DongTai IAST" does not require to sending specifically designed traffic to conduct the security test.

3."DongTai IAST" does not run dedicated tests attacks, it will not interfere with business operations.

## The Differences between IAST and RASP
Although IAST and RASP use similar technologies. Both of them run on the webserver and hook into an application's runtime to detect vulnerabilities with high accuracy. Yet, they still have some differences.

#### Purpose
-IAST, uses as a security testing tool to detect security vulnerabilities and remediation.
-RASP, uses as a security testing tool to protect the entire application and reports on or blocks attacks.

#### Approach
-IAST, executes a suite of tests against an application and repots detected vulnerabilities.
-RASP, integrate with an application to analyze traffic and end-user behavior patterns to prevent security attacks.

#### Scenarios
-IAST, runs in test environments. It is often a part of a broader security testing program.
-RASP, runs in the production environment.
