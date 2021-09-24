##  DongTai IAST Plugin for IntelliJ IDEA

The DongTai IAST plugin for IntelliJ IDEA integrates with the development environment. It is a lightweight plugin option for developers, which works in conjunction with DongTai IAST to add software security testing and remediation functionality from the plugin. During the development stage, it enables developers to have an actionable and easily understands report including vulnerability type, code location, and implement appropriate solutions. 

DongTai IAST for IntelliJ IDEA can detect:

- Dangerous uses of functions and APIs

- Third-party component security vulnerabilities identified

DongTai IAST plugin for IntelliJ IDEA also enables the creation of custom rules and personalizes threat coverage strategies according to specific enterprises and industry's needs. For example, developers might need to implement proprietary security guidelines or analyze custom libraries that are not yet covered by DongTai IAST knowledge base of rulepack.

## Requirement

DongTai IAST Plugin requires the software packages listed below:

- Operating Systems: `Windows, Linux and macOS`

- IntelliJ IDEA: `Versions 20.1 to 21.1`

- Hardware: `minimum Dual Core CPU Processors, 4GB RAM`

## Installing DongTai IAST Plugin for IntelliJ IDEA

#### A. Download and Install

- Download DongTai IAST plugin for IntelliJ IDEA installation package. [Download Link](https://github.com/HXSecurity/DongTai-Plugin-IDEA/releases/download/v1.0/DongTai-Plugin-IDEA.zip)

- Open IntelliJ IDEA and navigate to `Preferences/Plugin`. Selected `Install Plugin from Disk` and then install DongTai IAST IntelliJ IDEA plugin.
  
  ![plugin_download](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_download.png)

  ![plugin_download_disk](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_download_disk.png)
  
  ![plugin_install](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_installs.png)

- Restart IntelliJ IDEA after the installation to enable the plugin.

#### B. Settings

- Navigate to `Tools\DongTaiIAST\Configuration Cloud`on the menu bar.

  ![plugin_url_configuration](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_url_configs.png)

- Fill in the `agentURL`, `URL`, `TOKEN` parameter in the settings window.
  
  `agentURL`：Fill in `DongTai IAST OpenApi Service URL`

  `URL`：Fill in `DongTai IAST Web Service URL`
  
  `TOKEN`：Log in to the `DongTai IAST Web Service` to obtain the token from `Add Agent\Java` on the menu
  
  ![plugin_login](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_login_page.png)
  
  ![plugin_token_step](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_add-agent.png)
  
  ![plugin_token_success](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_java-token.png)


## Using the DongTai IAST Plugin for IntelliJ IDEA

#### A. Actionable Feedbacks 

- View security bugs in real time during development stage

There have shortcut buttons of `Run` and `Debug` with DongTai IAST on the upper menu of UI. It can help developers find and fix security vulnerabilities during code development.

a. We use a Spring Boot Application containing `Command Injection` as a demo. Open the application with IntelliJ IDEA and `Run/Debug` with DongTai IAST.

  ![demo_plugin_springboot](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Demo_plugin-springboot.png)

b. Access the application with the following URL `http://localhost:8080/demo/cmdi?var1=l&var2=s`. While the vulnerability was triggered, it will be shown on the vulnerabilities list.

Developer also can review the futher information about the vulnerability from `Details`.

  ![demo_plugin_springboot](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Demo_plugin-vul-list.png)


- API Sitemap

Unlike swagger, DongTai IAST plugin will auto list API Sitemap of the application without any configuration.

- Third-party component security vulnerabilities identified

DongTai IAST plugin also can indentify known vulnerabilities of third-party component. It reducing the risk of using potentially insecure and unstable libraries.

#### B. Customize Rules

- Add a customize HOOK rules

a. Right-click on the method name and select `Add HOOK Rule`.

b. Set the `rule set`, `rule type`, `rule details`, `source`, `stain target`, and `inheritance depth`.
    
  ![plugin_hook_action](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_action.png)
    
  ![plugin_hook_config](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_config.png)
    
  ![plugin_hook_commit](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_commit.png)

c. The DongTai IAST event log will return a success message if the rule of Hook was added; 
  ![plugin_hook_success](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_success.png)

Otherwise, it will prompt an error message windows. Please check the token and try again.
  ![plugin_hook_failure](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_failure.png)

d. You can review and modify the custom rule on `Settings/Custom Rule` in `DongTai IAST Web Service`.
  ![plugin_hook_result](https://hxsecurity.github.io/DongTai-Doc/doc/assets/features/plugin_hook_result.png)


## Get a Demo Account

- Registration: https://dongtai.io
- DongTai IAST Demo Site：https://demo.iast.io

### Contact Us

DongTai IAST Officialy WeChat Account
<div style="text-align:left">
<img width="100" height="100" alt="dongtai_QRCode.jpg" data-origin="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg" src="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg">
</div>









  
