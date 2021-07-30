#  IDEA Plugin — DongTai IAST instructions

<h2 id="1">一、DongTai IAST Plugin installation and configuration</h3>

###  1、IDEA install DongTai IAST plugin

- Download DongTai IAST plugin installation package. [Download Link](https://github.com/HXSecurity/DongTai-Plugin-IDEA/releases/download/v1.0/DongTai-Plugin-IDEA.zip)

- Open IDEA settings, choose to install Plugin from Disk, install DongTai IAST plugin installatino package **dongtai-idea-plugin.zip**
  
  ![plugin_download](../../doc/assets/features/plugin_download.png)

  ![plugin_download_disk](../../doc/assets/features/plugin_download_disk.png)
  
  ![plugin_install](../assets/features/plugin_installs.png)

- Restart IDEA , check the installed plugins, and check whether the DongTai IAST plugin is installed and enable successfully.

###  2、Configure "DongTai IAST Configuration Cloud"

- Click **DongTai IAST Configuration Cloud** in **Tools** on the top menu bar of IDEA, and an input box will pop up.
  
  ![plugin_url_configuration](../assets/features/plugin_url_configs.png)

- Fill in the `agentUrl`、`url`、`Token` parameters.
  
  `agentUrl、url`：automatically fill in the URL address of DongTai IAST, you can change it if you need it.
  
  `Token`：Log in to the [IAST Platform](https://iast.huoxian.cn/login), obtain **Token** in **the deployment of IAST**.
  
  ![plugin_login](../../doc/assets/features/plugin_login.png)
  
  ![plugin_token_step](../../doc/assets/features/plugin_token_step.png)
  
  ![plugin_token_success](../../doc/assets/features/plugin_token_success.png)

<h2 id="2">二、DongTai IAST plugin function</h3>

### 1、Quickly add HOOK rules

####  (1) Configure "Add HOOK Rules"

- Right-click on the method name to use the HOOK function, and select **Add HOOK Rule**

- Select the rule set, rule type, rule details, taint source, taint destination, and inheritance depth
    
    ![plugin_hook_action](../../doc/assets/features/plugin_hook_action.png)
    
    ![plugin_hook_config](../../doc/assets/features/plugin_hook_config.png)
    
    ![plugin_hook_commit](../../doc/assets/features/plugin_hook_commit.png)

####  (2) Examples of different results returned after the completion of "Add Hook Rule"  

- If the addition is completed successfully, `Event Log` will prompt that the request was sent successfully.
  
  ![plugin_hook_success](../../doc/assets/features/plugin_hook_success.png)
  
- If the Token filled is wrong, current dialog will exit and pop up a prompt.
  
  ![plugin_hook_failure](../../doc/assets/features/plugin_hook_failure.png)

####  (3) View the added HOOK rules  

 - Log in to the  [IAST Platform](https://iast.huoxian.cn/login), select custom rules in system configuration. 

  ![plugin_hook_result](../../doc/assets/features/plugin_hook_result.png)

[comment]: <> (<h4 id="2">二、One-Click configuration of local agent</h4>)

### 2、Run / Debug With IAST

####  (1) Function introduction

- Use the `Run/Debug With IAST` function to start your application, add One-Click IAST , debug and detect vulnerabilities.

##### (2) Startup project

- Task an open source project as an example, use `Run / Debug with IAST` to startup the project.

  ![plugin_agent_run](../../doc/assets/features/plugin_run_debug_app.png)
  
- The log printed on the console shows that the agent has been added.
  
  ![plugin_agent_running](../../doc/assets/features/plugin_agent_add.png)

### 3、View application vulnerabilities in real-time

- View vulnerability information in real-time in the pulgin.

  ![plugin_taint_details](../../doc/assets/features/plugin_taint_details.png)










  
