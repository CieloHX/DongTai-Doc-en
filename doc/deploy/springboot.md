> How to start the Jar package

#### Manual installation

##### 1. Install Agent

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the agent of IAST in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`
 
##### 2. Configure Agent

-If you use the war package to deploy, the agent installation method is the specific middleware installation method
  
-If you use `java -jar app.jar` to deploy, add the startup parameter `-javaagent:/path/to/agent.jar` to the startup command, such as
```shell
java -javaagent:/path/to/agent.jar -Dproject.name=<project name> -jar app.jar
```

-Note: `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.
