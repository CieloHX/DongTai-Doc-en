## 1.Download Agent

- Log in to [IAST platform](https://iast.huoxian.cn/login) and download the agent of IAST in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

## 2.Deployment

### 2.1 SpringBoot

- If you use the war package to deploy, the agent installation method is the specific middleware installation method

- If you use `java -jar app.jar` to deploy, add the startup parameter `-javaagent:/path/to/agent.jar` to the startup command, such as
```shell
java -javaagent:/path/to/agent.jar -Dproject.name=<project name> -jar app.jar
```

-Note: `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

### 2.2 Tomcat

1. Enter the content where `tomcat` is located

2. Edit the `catalina.sh` file under the `tomcat/bin` content and add parameters:
```shell
CATALINA_OPTS=-javaagent:/path/to/server/agent.jar" "-Dproject.name=<project name>
```

![tomact_config_catalina.png](../assets/deploy/manual/tomcat_config_catalina.png)

- Note: `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

### 2.3 JBoss/Wildfly

#### 2.3.1 JBossAS 6

- Enter the main content of the JBoss container, find the line where `# Setup JBoss specific properties` is located in the `bin/run.sh` file, and insert the following line below the line:

  ```shell
  JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
  ```
- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

#### 2.3.2 JBossAS 7、JBossWildfly

- Enter the home content of the JBoss container and modify the corresponding configuration file according to the startup type of the current server: standalone, domain

- **Standalone mode**

  Open the `bin/standalone.sh` file, locate the line where `# Display our environment` is located, and insert the custom configuration above it, as follows:

  ```shell
  JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
  ```
- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.


- **domain mode**

  The current version is the community version, it is not recommended to install Agent in domain mode

### 2.4 Resin

1. Enter the main content of Resin,

2. Open the `conf/cluster-default.xml` file and locate the line where `<server-default>` is located,

3. Insert below the line
  ```shell
  <jvm-arg>-javaagent:/opt/Resin/iast/agent.jar</jvm-arg>
  <jvm-arg>-Dproject.name=<project name></jvm-arg>
  ```
- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

4. Restart Resin

### 2.5 Jetty

1. Enter the main content of jetty

2. Open the `bin/jetty.sh` file and find the line of `Add jetty properties to Java VM options.`

3. Insert `JAVA_OPTIONS+=( "-javaagent:/path/to/agent.jar --Dproject.name=<project name>")` under the changed line

- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

4. Restart the jetty server

### 2.6 WebLogic

#### 2.6.1、通过WebLogic的console控制台

Visit weblogic's console, for example:

1. Find "Server" under "Environment", and then click on the server that needs to install agent in the server list, such as AdminServer

![adminserver.png](../assets/deploy/weblogic/adminserver.png)

2. Enter the server details, click "Server Start", and fill in the parameters of javaagent in the parameter column below
```shell
JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
```
- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.


![adminserver.png](../assets/deploy/weblogic/boot.png)

3. Restart the server to make the configuration take effect

![adminserver.png](../assets/deploy/weblogic/restart.png)
#### 2.6.2、通过修改weblogic的config.xml文件

- Find the `config.xml` file in the `/u01/oracle/weblogic/user_projects/domains/base_domain/config` content, locate the `<arguments>` tag under the `<server-start>` tag, and add it in the tag Configure as follows:
`-javaagent:/path/to/agent.jar -Dproject.name=<project name>`

- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

### 2.7 WebSphere

- Enter the management background of the WebSphere WEB side, in the navigation bar on the left side of the console, select `Servers -> Server Types -> WebSphere Application Server` to enter the application list interface:

  ![app.png](../assets/deploy/websphere/app.png)

- Select the application that needs to install the agent (take server1 as an example), and click to enter the management page. Scroll down on the new page, find `Server Infrastructure -> Process definition`, and click to enter:

  ![server1.png](../assets/deploy/websphere/server1.png)

- Click `Additional Properties -> Java Virtual Machine` to enter the JVM startup parameter editing interface

  ![jvmarg.png](../assets/deploy/websphere/jvmarg.png)

- Find the `Generic JVM arguments` option, start editing and fill in the following content and save `-javaagent:/path/to/agent.jar -Dproject.name=<project name>`

- Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

- Restart the corresponding modified server application

