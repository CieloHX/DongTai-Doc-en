> Resin 4

#### Manual modification

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the agent of IAST in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`
 
##### 2. Deploy agent
1. Enter the main content of Resin,

2. Open the `conf/cluster-default.xml` file and locate the line where `<server-default>` is located,

3. Insert below the line
```shell
<jvm-arg>-javaagent:/opt/Resin/iast/agent.jar</jvm-arg>
<jvm-arg>-Dproject.name=<project name></jvm-arg>
```
Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

4. Restart Resin