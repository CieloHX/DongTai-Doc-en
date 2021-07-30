#### Manual installation

##### 1. Install Agent.jar

Log in to [IAST platform](https://iast.huoxian.cn/login) and download the IAST Agent in the **Deploy IAST**, and put the agent.jar file on the machine where the WEB server (middleware) is located, Ensure that the content where the agent.jar file is located has writable permissions, such as `/tmp/`

#### 2. Configure the WebSphere server
Enter the management background of the WebSphere WEB side, in the navigation bar on the left side of the console, select `Servers -> Server Types -> WebSphere Application Server` to enter the application list interface:

![app.png](https://hxsecurity.github.io/DongTai-Doc/doc/assets/deploy/websphere/app.png)
 
Select the application that needs to install the agent (take server1 as an example), and click to enter the management page. Scroll down on the new page, find `Server Infrastructure -> Process definition`, and click to enter:

![server1.png](https://hxsecurity.github.io/DongTai-Doc/doc/assets/deploy/websphere/server1.png)

Click `Additional Properties -> Java Virtual Machine` to enter the JVM startup parameter editing interface

![jvmarg.png](https://hxsecurity.github.io/DongTai-Doc/doc/assets/deploy/websphere/jvmarg.png)

Find the `Generic JVM arguments` option, start editing and fill in the following content and save `-javaagent:/path/to/agent.jar -Dproject.name=<project name>`

Note that `-Dproject.name=<project name>` is an optional parameter, `<project name>` should be consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management for manual binding.

Restart the corresponding modified server application
