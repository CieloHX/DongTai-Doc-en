> Interactive Application Security Testing (Interactive Application Security Testing) is a new application security testing program proposed by Gartner in 2012. It collects and monitors the runtime functions of Web applications through agents, VPNs or deploying Agent programs on the server. Execution, data transmission, and real-time interaction with the scanner, efficiently and accurately identify security flaws and vulnerabilities, and accurately determine the code files, lines, functions, and parameters where the vulnerabilities are located. IAST is equivalent to a combination of DAST and SAST, an interrelated runtime security detection technology

In 2021, "LingZhi IAST" upgraded to "HuoXian~ DongTai IAST", providing better vulnerability detection capabilities, product experience and services, and simultaneously launching independent SaaS version products. Go [Quick start](en-us/doc/tutorial/quickstart) page to learn how to use it.

## IAST Categories
- Positive IAST
- Passive IAST

#### Positive IAST
Positive IAST deploys the agent in the application under test, and then uses an external scanner to trigger traffic to be captured by the agent to detect whether there are vulnerabilities.

#### Passive IAST
Passive IAST deploys the Agent in the application under test, then obtains the code context information and data flow of the program execution, combs the tainted links according to the data flow and the code context information of the program execution, and detect whether there are vulnerabilities.


## HuoXian~ DongTai IAST
1."HuoXian~ DongTai IAST"  is  passive IAST, which with the advantages of near real-time detection, high detection rate, low false alarm rate, low false alarm rate, etc.

2.“HuoXian~ DongTai IAST” don't need replace the data packets, could cover encryption , anti-replay , Verification code etc real Business scene.

3.“HuoXian~ DongTai IAST” don't produce "dirty data", don't interfere the work of test.

## The Differences between IAST and RASP
- Rasp is used in the production environment to hook taint input methods and dangerous methods, detect whether there are vulnerability and intercept; it is not responsible for the complete taint call chain, the detection methods are mainly value matching and some syntax analysis and semantic analysis
- Iast is used in the test environment, hooks the taint input method, the taint propagation method and the dangerous method, and judges whether there are vulnerabilities based on the value matching algorithm and the taint propagation algorithm
- In short, rasp is used to analyze whether there is attack data from external taints; iast is used to analyze whether there is an attack exploit chain from external taints.
- In SDLC, IAST is a tool in the development phase, and RASP is a tool after it goes online; the underlying technical principles of the two tools are the same, and the product focus and detection principles are different
