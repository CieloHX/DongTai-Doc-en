# DongTai IAST v1.0.3 Deployment Guide

# Deploy

### Preparing to Deploy DongTai IAST

DongTai IAST Lastest Version: v1.0.3

System Requirement: Linux or Mac OS

Notice: 
Ensure `Docker` and `docker-compose` have been installed in the system environment.

Execute the following command `docker -v` and `docker-compose -v` to check if Docker exists in the system. If not, please install `Docker` and `docker-compose` before the deployment.

![checkdockerinstall](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_check-docker-docker-compose-install-exist.png)

* For Window Server users, please submit your request on the “Install & Deploy” category in our [discussion forum](https://github.com/HXSecurity/DongTai/discussions/categories/install-deploy).

### Deployment

1. Clone the deployment package from GitHub

Please access to [DongTai Official Github](https://github.com/HXSecurity/DongTai) to clone the deployment package.

![clonefromgithub](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_clone-from-github-1.0.3.png)

And the other way, you also can follow the command below to download the git repository and switch to the latest version branches via Shell Command:

```shell
#clone the the git repositoty
git clone git@github.com:HXSecurity/DongTai.git
cd

cd DongTai
git pull

# You can switch to other version branches by needs:
git checkout release-1.0.3
```

2. One-Click Deployment

Executing the `build_with_docker_compose.sh` file to deploy DongTai IAST

```shell
chmod u+x build_with_docker_compose.sh
./build_with_docker_compose.sh
```

Notice:
a. DongTai IAST will need an export port for `DongTai-Web` and `DongTai-OpenApi` services, the default port will be `80` and `8000`. Please check the following port is available. You can modify it during the development or keep the argument blank as default.

b. It took 2 – 3 minutes to initial the settings after running the `build_with_docker_compose.sh`.

![executingshellfile](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_executing-shell-file.png)

3. Access to DongTai IAST

You can access to DongTai IAST by http://localhost after development, the following page as below:

![loginpage](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_login_page.png)

Notice:
a. Both default account name and password is `admin`. You `MUST` change the password during the first time log in. Password can be changed at `Settings/Account`.  After that, you can log in again.

![apiservicepage](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_account_page.png)

b. The verification code will show after the database finish the initial settings. If it didn’t show out more than 10 minutes, please report to us in our official QQ or WeChat group.

c. Navigating to `Settings/Service Registration` to set up the `DongTai-OpenAPI` URL first after log in into the platform. Please use public IP and `AVOID` using `localhost` or `127.0.0.1`.

![apiservicepage](https://hxsecurity.github.io/DongTai-Doc/doc/assets/en_us/Deploy_api_page.png)

DongTai IAST already finished deploy and set up. You can install the agent to start the security testing via `Add Agent`.
For any futher information can reach us at out Official WeChat Account.

### Contact Us

Follow our Official WeChat Account for futher information.

DongTai IAST Officialy WeChat Account
<div style="text-align:left">
<img width="100" height="100" alt="dongtai_QRCode.jpg" data-origin="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg" src="https://hxsecurity.github.io/DongTai-Doc/doc/assets/aboutus/dongtai_wx.jpg">
</div>
