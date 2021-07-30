### Manual installation-Linux

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the agent of IAST in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

##### 2. Deploy the Agent
 
1. Enter the content where `tomcat` is located

2. Edit the `catalina.sh` file under the `tomcat/bin` content and add parameters:
```shell
CATALINA_OPTS=-javaagent:/path/to/server/agent.jar" "-Dproject.name=<project name>
```

![tomact_config_catalina.png](https://hxsecurity.github.io/DongTai-Doc/doc/assets/deploy/manual/tomcat_config_catalina.png)

-Note: `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

