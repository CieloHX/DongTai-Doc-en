> quick start

Huoxian～DongTai IAST’ provides the taint chain of popular Java projects in github. You can directly search for sink point to find vulnerabilities. The following will introduce how to directly use IAST to detect this vulnerability by the example of remote command Spring Security OAuth2 to execute vulnerability.

### Conditions for code auit discovery 0 Day
- Application Environment

- Know how to trigger the vulnerability(sink point)

- Take time to analyze the taint chain

- Find a way to bypass some limitations of the framework and the system(may could skip this step)

In order to improve the efficiency of digging vulnerabilities and to dig vulnerabilities faster, open the following functions specially:
- Build a Java project which has the stars more than 2k in github to give programmers to test and avoid repeated setting up of the environment

- Automatically crawl the interfaces in the above projects, trigger traffic, and generate tainted call chains

- Open search function, and support to search the stain call chain of the above-mentioned all items. If find a sink point, we could search all items directly and view all hit vulnerabilities

Now, the programmers could focus on code audits and easily discover vulnerabilities.

### Vulnerability search
**DongTai IAST** search function: [***\*https://iast.huoxian.cn/taint/search\****](https://iast.huoxian.cn/taint/search)

1. Specify the vulnerability sink method, such as: org.springframework.expression.Expression.getValue, then search and we could find the HTTP request where the tainted call chain of the sink method is located
![spring-el](../../doc/assets/bugbountry/search_result.png)

2. After finding the relevant HTTP request, according to the name of agent to judge current HTTP belongs to which open source project

3. View the details of the tainted call chain and the details of the HTTP request
![taint_link_detail](../../doc/assets/bugbountry/taint_link_detail.png)

Then according to the prompt of the node, find the specific process of the taint propagation and the upper call of the each method, which could be used to quickly verify and reproduce whether there are other restrictions on the vulnerability.

### Vulnerability detection for self-built projects
Before the code audit, you can install the agent of DongTai IAST in the project. During the code audit and continuous debugging, more sink points and vulnerabilities could be found.
