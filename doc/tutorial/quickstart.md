> LingZhi IAST has been upgraded to "HuoXian~ DongTai IAST". At the same time, an independent SaaS version is provided, which supports third-party component management, general vulnerability detection, unauthorized vulnerability detection, and component-level vulnerability mining

DongTai IAST  SaaS Version：[https://iast.huoxian.cn/login](https://iast.huoxian.cn/login) 

## Login to IAST  Platform

### 1. Register

- Fill out the [questionnaire](https://jinshuju.net/f/I9PNmf) to register
  ![register_questionnaire](../../doc/assets/tutorial/register_questionnaire.png)
  
  Notice：Accounts will be created in 10 o'clock am.

- We will send you the user name and password to you after registration and generating the user.

### 2. Login

- Login Address：https://iast.huoxian.cn
  
  ![login_iast](../../doc/assets/tutorial/login_iast.png)


### 3. Modify  the password 

- After logging in to [IAST platform](https://iast.huoxian.cn/login), click on system configuration and select password modification in the left column to modify the password.

  ![password_change](../../doc/assets/tutorial/password_changes.png)

## Online Range- Quick Experience of IAST

- Currently, the online range provides openrasp test environment, BenchMark test environment, etc. You can quickly start the cloud environment through the online range to experience the use process of IAST. The following takes the range mirroring openrasp shooting range environment as an example to demonstrate. ####

#### Configurations of Online Range IAST token

- Login to [IAST platform](https://iast.huoxian.cn/login)
- Access the "Deploy IAST" feature
- Select the **development language** used by the target application  (Java) 
- Select the corresponding operating system and version (choose 1.8 for JDK 1.8 and below, choose 1.9 for JDK 1.8 and above)
- Copy the TOKEN 

  ![find_token](../../doc/assets/tutorial/find_tokenn.png)

- Log in to [Range](https://labs.iast.huoxian.cn), the range account is the same as the IAST account
- Click System Settings, enter the token configuration page, paste the previously copied token, click Modify to save

  ![config_token_setting](../../doc/assets/tutorial/config_token_setting.png)


#### 2.Download the shooting range mirror (take the mirror openrasp1-3-6 as an example)

- Take the mirror openrasp1-3-6 as an example, click mirror management, click download after the corresponding mirror, and a prompt box will pop up to start downloading the range

  ![vulfocus_download](../../doc/assets/tutorial/vulfocus_downloadd.png)

- After the download is successful, check whether there is an access path for the current range description item (for example, the access path for openrasp1-3-6 is /wxpay-xxe and /vulns), if so, please copy it, click to enter the range, and paste the access path to access the project

  ![vulfocus_downloadd_success](../../doc/assets/tutorial/vulfocus_downloadd_success.png)

  ![visit_route](../../doc/assets/tutorial/visit_route.png)

- After the project is successfully launched, enter [IAST platform](https://iast.huoxian.cn/login), you can see the newly launched application on the engine management page in the system configuration
  
  ![agentManage](../../doc/assets/tutorial/agentManage.png)

#### 3、Create project
- Enter the **Project Configuration** page, click **New Project**

![create project](../../doc/assets/tutorial/project_new.png)

- Create a new project, fill in the basic settings and save

![create project](../../doc/assets/tutorial/project_edit.png)

#### 4、Detect vulnerabilities
After the project is created, you can access the application normally and trigger the API to detect vulnerabilities; the detected vulnerabilities can be seen on the **Project Details** page or on the **Application Vulnerabilities** page.

![project_detail](../../doc/assets/tutorial/project_detail.png)
![project_detail_list](../../doc/assets/tutorial/project_detail_list.png)

## Local application-install IAST
#### 1、Download Agent
- Login to [IAST platform](https://iast.huoxian.cn/login)
- Access the "Deploy IAST" feature
- Select the **development language** (Java) used by the target application
- Select the corresponding operating system and version (choose 1.8 for JDK 1.8 and below, choose 1.9 for JDK 1.8 and above)
- Enter the download and configuration page, follow the steps to complete the download and configuration

![get_iast_token](../../doc/assets/tutorial/download_agent.gif)

#### 2、Configure the agent and start the application ( SpringBoot as example)
SpringBoot is packaged as `jar` by default and started by the method of `java -jar app.jar`; when installing the agent on this type of SpringBoot, you only need to add a parameter to the startup command:

```shell
java -javaagent:/path/to/agent.jar -Dproject.name=<project name> -jar app.jar
```
Note: `-Dproject.name=<project name>` is an optional parameter, `<project name>` is consistent with the name of the created project, and the agent will be automatically associated with the project; if you do not configure this parameter, you need to enter the project management Perform manual binding.


After the application is started, you can see the newly launched agent on the Engine Management page in the **System Configuration**. If `-Dproject.name=<project name>` is not specified, the project name defaults to `Demo Project` .

![agent_system_manage](../../doc/assets/tutorial/agent_system_manage.png)

#### 3、Create project

Enter the **Project Configuration** page, if you use the `-Dproject.name=<project name>` parameter, the agent will be automatically associated with it. If you want to associate with other agents, you can configure it independently in the settings.

![project_new_auto](../../doc/assets/tutorial/project_new_auto.png)

![project_edit_auto](../../doc/assets/tutorial/project_edit_auto.png)

#### 4、Detect vulnerabilities
After the project is created, you can access the application normally and trigger the API to detect vulnerabilities; the detected vulnerabilities can be seen on the **Project Details** page or on the **Application Vulnerabilities** page.

![project vul](../../doc/assets/tutorial/project_vul.png)

![project vul list](../../doc/assets/tutorial/project_vul_list.png)