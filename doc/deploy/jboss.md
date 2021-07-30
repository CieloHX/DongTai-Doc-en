> JBossAS 6

#### Linux-Manual modification

##### 1. Install agent.jar

 [IAST platform](https://iast.huoxian.cn/login) Download the agent of the DongTai IAST in **Deploy IAST**, put the agent.jar file on the machine where the WEB server (middleware) is located, and ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

##### 2. Deployment
Enter the main content of the JBoss container, find the line where `# Setup JBoss specific properties` is located in the `bin/run.sh` file, and insert the following line below the line:

```shell
JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
```
Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

> JBossAS 7, JBossWildfly

#### Linux-Manual modification

##### 1. Install agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the IAST Agent in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

##### 2. Deployment

Enter the home content of the JBoss container and modify the corresponding configuration file according to the startup type of the current server: standalone, domain

**Standalone mode**
Open the `bin/standalone.sh` file, locate the line where `# Display our environment` is located, and insert the custom configuration above it, as follows:

```shell
JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
```
Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.


**domain mode**

The current version is the community version, it is not recommended to install Agent in domain mode
