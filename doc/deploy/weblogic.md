#### Manual modification
> Non-cluster mode

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the IAST Agent in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

##### 2. Deploy the Agent

Enter the `WebLogic` content, open the `bin/startWebLogic.sh` file, find the line where `JAVA_OPTIONS="${SAVE_JAVA_OPTIONS}"` is located, and add a line below the line
```shell
JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
```
Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

 
> Cluster Mode

#### Method one, through the WebLogic console

Visit weblogic's console, for example:

1. Find "Server" under "Environment", and then click on the server that needs to install agent in the server list, such as AdminServer

![adminserver.png](../assets/deploy/weblogic/adminserver.png)

2. Enter the server details, click "Server Start", and fill in the parameters of javaagent in the parameter column below
```shell
JAVA_OPTS="$JAVA_OPTS "-javaagent:/opt/jboss/iast/agent.jar" "-Dproject.name=<project name>
```
Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.


![adminserver.png](../assets/deploy/weblogic/boot.png)

3. Restart the server to make the configuration take effect

![adminserver.png](../assets/deploy/weblogic/restart.png)

#### Method two, by modifying weblogic's config.xml file

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the IAST Agent in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

##### Deploy Agent
Find the `config.xml` file in the `/u01/oracle/weblogic/user_projects/domains/base_domain/config` content, locate the `<arguments>` tag under the `<server-start>` tag, and add it in the tag Configure as follows:
`-javaagent:/path/to/agent.jar -Dproject.name=<project name>`

Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.
