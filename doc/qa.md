
#### 1. How do I compile and use a local Java Agent?

> Through debugging, I found that it is useless to compile core and inject. His agent will download these two jar packages from the official website and put them in the temp directory. I don’t know if it is a deliberate or written bug, because if you download it from the official website Uploading and downloading is just downloading the agent, and dynamically downloading core and inject during runtime. It should be the first plan to try it out. Didn't plan to open source?                                      -- Author: Su 18

**DongTai IAST-Java data collection Analysis**

The agent part of the cave state DongTai IAST is composed of three parts: `agent.jar`, `iast-core.jar` and `iast-inject.jar`：
- `agent.jar` is used to store configuration, regularly pull cloud information, download and load core detection engines `iast-core.jar` and `iast-inject.jar`
- `iast-core.jar` is used to inject into `BootStrap ClassLoader`, and subsequently call the data collection method in iast-core.jar in the target application
- `iast-core.jar` is the core jar package, which stores data collection, data preprocessing, data reporting and other functions

When the data collection starts, the current startup mode is detected by `agent.jar`, the rules are as follows:
- The debug mode is false, and the detection engine is downloaded from the cloud and started
- The debug mode is true, check whether there is a core detection engine in the local temporary directory
  - Exist, load local detection engine and start
  - Does not exist, download the detection engine from the cloud and start

Overall, if you want to try the agent compiled by yourself, you need to specify the startup mode as `-Ddebug=true` and copy `iast-core.jar` and `iast-inject.jar` to the temporary directory.

**Compilation and Configuration**

It only takes four steps to modify the `Agent` code and use the cloud environment:
1. Pull code: `git clone https://github.com/HXSecurity/DongTai-agent-java.git`
2. Modify the code in agent-java according to requirements
3. Compile Agent
    3.1 Log in to the**huoxian--DongTaiIAST**cloud, go to the deployment page to obtain the **Token** and cloud service address
    3.2 Write the Token and cloud service address into`iast-agent/src/main/resources/iast.properties` file
    3.3 Run`maven clean package`to compile agent
4. Copy the detection engine to a temporary directory
5. Run the application (take SpringBoot application as an example):`java -javaagent:/path/to/iast-home/release/iast-agent.jar -Ddebug=true -jar app.jar`

#### 2. About application identification/differentiation

> How does the detection engine distinguish between applications？                                                                         -- Author: Su 18

The distinction between detection engine and application can be divided into two types: automatic recognition and distinction and manual configuration for distinction. At the beginning, we studied the automatic recognition of the application name, but later found that the accuracy is difficult to guarantee, so we finally chose manual configuration plan.

1. **DongTai IAST** supports two ways to configure the application name:
- Method 1: Through the **Deploy IAST** page, enter the **project name**, when the application starts, the data collection will be automatically bound to the corresponding project
  ![image-20210519091515254](https://huoxian-zone.oss-cn-beijing.aliyuncs.com/imagesimage-20210519091515254.png)
- Method 2:When starting the application, specify the JVM parameter`-Dproject.name=<project.name>`, as follows:
  ```
  java -Dproject.name=<project.name> -jar app.jar
  ```

2. **[Discussion]** IAST Alternatives for IAST to automatically identify project names.
  - ContextPath
  - The physical path of the current Request

#### 3. The philosophy of SCA

> An excellent IAST must have SCA-like functions. The simple implementation is to collect customer segment component information, send it to the cloud through matching CPE, and link to the corresponding CVE/CWE/CNNVD, etc.                                                                                -- Author: Su 18

The realization of the SCA function of **DongTai IAST** is mainly divided into three parts:
- Collect and report third-party components used in `JavaWEB` applications
- Match with the official `Maven` component library to obtain accurate version information
- Docking with the vulnerability database to sort out vulnerabilities (the vulnerability database data comes from high-quality SCA vulnerability data publicly available at home and abroad, and has not been processed by cpe)

1. Scheme for collecting third-party components in `JavaWEB` According to the class loading mechanism in Java, the JVM will load the third-party component classes referenced in the class while loading the application code class. According to this feature, obtain the jar package location where the third-party component class is located in `IAST`, count it as `path1`, and then read all the jar packages in the `path1` directory; finally use the `SHA-1` algorithm to calculate the hash value of the Jar package and report it To the cloud
2. The cloud matches the `Maven` official component library. The cloud matches the `Maven` component library according to the `SHA-1` hash value to obtain the corresponding `groupId`, `artifactId` and version information
3. Cloud and vulnerability library docking After getting the version information of the component, docking with the vulnerability library to determine whether there is a cve vulnerability

**[Discussion]** Is there a better way to collect SCA?

#### 4. How to acquire token?

1. Log in to the IAST official website. Official website: https://iast.huoxian.cn/
2. Click "Deploy IAST" in the upper right corner, and click "Next" until the third step
3. Find the parameter Token in "Automatic Download"
   
#### 5. If multiple projects share the same agent, how will the vulnerability information collected by the background be displayed?

- If multiple projects share the same Agent, you need to add startup parameters `Dproject.name=project name` when starting the project, then create a new project on the official website of DongTai IAST. The project name is consistent with the "project name" in the parameter `-Dproject.name=project name` to automatically bind the agent, and the vulnerability information will be displayed in each project.
  
#### 6. How does a project bind multiple versions? What about vulnerability data presentation?

1. When creating a new project on the DongTai IAST official website, there is an input box to fill in the version, and fill in the current application version. When the application is updated with a new version, first enter the details of the previously built project, edit the version in the "version" section, add a new version and switch to the new version, and then start the new version application.
2. The vulnerability data of different versions will be displayed in the corresponding version of the project.
   
#### 7. Are project components loaded once they start, or are they tested in succession based on application access?

- It depends on application access, and the data is uploaded back at a certain interval.
  
#### 8. No module named 'dongtai_models' error message is displayed during manual deployment. How to solve this problem?

- To execute pip install https://huoqi-public.oss-cn-beijing.aliyuncs.com/iast/dongtai-0.1.0.tar.gz.
  
#### 9. How to setup the engine and apiserver service addresses in single-node deployment?

- Engine specifies the Intranet address of the dongtai-engine service.
  
#### 10. Which database sql files are executed during local deployment?

1. To execute the db.sql first.
2. Execute update.sql based on date order.
   
#### 11. Why is there no data collection detected on IAST website after starting the project?

1. Check the startup command of your own application. Take springBoot project as an example:`java -javaagent:/path/to/agent.jar -Dproject.name= -jar app.jar.` Note that you compile -java agent before -jar.
2. Check whether the network connection of the application is good.
   
#### 12. What should I do if an error message is displayed after starting the project using agent?

- Errors may occur during the detection of the Agent. In general, errors are normal. If the application is affected, save the error logs and contact our technician.
  
#### 13. Why did the image ghost or code fail to be pulled during deployment?

1. Check whether the network can access AliCloud.
2. Check whether the network can access Github.

#### 14. What are the server resource requirements for a local installation?

1. 4 core and 8GB server.
2. Install docker.

#### 15. The DongTai IAST website cannot be accessed?

1. Check whether other websites can be accessed.
2. Change aliyun DNS.


