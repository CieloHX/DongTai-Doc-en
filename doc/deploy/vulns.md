> "Huoxian Platform" and the vulhub project jointly launched the vulhub-cli tool to simplify the deployment of the vulhub shooting range, it can quickly experience the "Huoxian ~ DongTai IAST"

#### Vulhub Shooting Range can quickly install the " Huoxian～DongTai IAST"

For the Vulhub shooting range, it uses docker-compose for management. In order to facilitate the convenience of community users, docker-compose is directly packaged to generate the `vulhub-cli` tool, which is convenient for community users to directly use "Huoxian~DongTai IAST".

[vulhub-cli official document](https://github.com/hxsecurity/vulhub-compose)
 
```shel
# Install vulhub-cli
$ pip install vulhub-cli

# Use vulhub-cli to start the shooting range environment and install the public DongTai IAST (vulnerability data is visible to everyone)
$ vulhub-cli remote start --app solr/ssrf_path --plugin dongtai

# Use vulhub-cli to start the shooting range environment and install the personal DongTai IAST (vulnerability data is only visible to individuals)
$ vulhub-cli remote start --app fastjson/1.2.24-rce --plugin dongtai --plugin-args "token=<dongtai iast token>"

# Use vulhub-cli to stop and destroy the shooting range
$ vulhub-cli remote stop --app fastjson/1.2.24-rce --plugin dongtai
```

There is a compatibility problem between the agent of "Huoxian ~ DongTai IAST" and the JDK of the apache solr shooting range in vulhub. The agent cannot be installed temporarily. You can go to the official website `apache solr` to download and deploy by yourself or contact [technical support](/doc/aboutus/support) ). 