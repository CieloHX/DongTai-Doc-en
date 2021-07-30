> The version, function, technical architecture and deployment scenario of the DongTai IAST

## Introduction
DongTai IAST includes front-end projects and back-end APIs. The front-end projects are developed based on `Vue`、`TypeScript`, and the back-end projects are developed based on `Django`、`Django Rest Framework`. including: strategy search、project list、project details、creat project、export project vulnerabilities、application vulnerability management、third-party component management、agent management、Hook rule management、user management and other functions。

#### Architecture diagram
![a](https://hxsecurity.github.io/DongTai-Doc/doc/assets/deploy/framework.png)

## Version
There are two versions of DongTai IAST: 

- SaaS version
- Localized deployment version

### SaaS version
SaaS version URL address：[https://iast.huoxian.cn](https://iast.huoxian.cn)

### Localized deployment version [Open source for companies which Joint development]
The open source version needs to be applied for by yourself, please refer to the application method. [Below](doc/tutorial/versions?id=申请方式)

#### Stand-alone deployment

- [x] [docker-compose One-Click deployment](https://github.com/HXSecurity/DongTai/tree/main/deploy/docker-compose)
- [x] [Source code One-Click deployment](https://github.com/HXSecurity/DongTai#%E4%B8%80%E9%94%AE%E6%BA%90%E7%A0%81%E9%83%A8%E7%BD%B2docker%E7%8E%AF%E5%A2%83)
- [ ] Docker One-Click deployment plan to be updated

#### Cluster deployment

- [x] [Kubernetes version One-Click deployment](https://github.com/HXSecurity/DongTai/blob/main/deploy/kubernetes)

#### How to apply
the Partner program of DongTai — Joint development, [Registration URL address](https://jinshuju.net/f/PKPl99)
