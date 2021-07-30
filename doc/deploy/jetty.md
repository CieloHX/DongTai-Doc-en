
#### Manual modification

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the Agent of IAST in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`
 
##### 2. Deployment
1. Enter the main content of jetty

2. Open the `bin/jetty.sh` file and find the line of `Add jetty properties to Java VM options.`

3. Insert `JAVA_OPTIONS+=( "-javaagent:/path/to/agent.jar --Dproject.name=<project name>")` under the changed line

Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

4. Restart the jetty server