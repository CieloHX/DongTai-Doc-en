### Data collection

- Agent heartbeat data
- Error log data 
- Method pool data
- Third-party component data
 
#### **Agent** heartbeat data

Heartbeat data includes information such as `network`, `memory`, `cpu`, `disk`, etc. which is used to determine the load of the application and automatically start and stop.

```json
{
  "type":"0x01",
  "detail":{
    "agent":"win-hostname-ip-key",
    "language":"Java",
    "pid":"18721",
    "hostname":"hostname",
    "network":{
"name":"",
"ip":"" },
    "memory":{
      "total":"1 GB",
      "use":"0.5 GB",
      "rate":"10%"
}, "cpu":{
      "total":"0.13 GB",
      "use":"0.03 GB",
      "rate":"3.21%"
}, "disk":{
      "total":"10 GB",
      "use":"0.5GB",
      "rate":"5%"
    },
    "req_count":100,
    "server_name":"tomcat",
    "server_version":"9.x",
    "server_path":"/opt/apache-tomcat",
    "server_hostname":"ecs-beijing-001",
    "server_ip":"10.12.10.13",
    "server_port":"80"
     } 
}
```



#### Error log data

Record the server address and log information. The data about the user in the log is coded and can be closed.

```json
{
  "type":"0x51",
  "detail":{
    "agent":"win-hostname-ip-key",
    "language":"Java",
    "app_name":"OWASP Benchmark",
    "server_path":"/opt/apache-tomcat",
    "log":"java.lang.Main()\njava.lang.Exec()"
	} 
}
```



#### Method pool data

- Frame classed and JDK classed are recorded as they are，and the class names are hidden for the classes developed by the user.
- Tainted data, using the unified unique identification algorithm to calculate the stain, the stain does not transmit data, only transmit the identifier identification corresponding to the stain.
- Call stack data, call stack data is processed according to the first rule, but the related calling sequence will be saved.

```json
{
  "type":"0x22",
  "agent":"win-hostname-ip-key",
  "version":"1.1.3 RELEASE",
  "app_name":"OWASP Benchmark",
  "server_name":"tomcat",
  "server_path":"/opt/apache-tomcat",
  "taint_value":"20192031",
  "taint_position":"QueryString",
  "taint_param_name":"name",
  "http_url":"",
  "http_uri":"",
  "http_client_ip":"",
  "http_header":"",
  "method_pool":[
    {"invokeId":1,"class":"java.","method_name":"getParameter","taint_in":"name", "taint_out":"20192031", "stack":[]}, 
    
    {"invokeId":1,"class":"java.lang.Base64","method_name":"decode","taint_in":"20192031", "taint_out":"20192032", "stack":[]},
    
    {"invokeId":1,"class":"xxx.xxx.xxx","method_name":"getValueOfString","taint_in":"20192032", "taint_out":"20192033", "stack":[]},
    
    {"invokeId":1,"class":"xxx.xxx.xxx","method_name":"nomarlize","taint_in":"20192033", "taint_out":"20192034", "stack":[]},
    
    {"invokeId":1,"class":"java.lang.Runtime","method_name":"exec","taint_in":"20192034", "taint_out":"20192035", "stack":[]},
    
    {"invokeId":1,"class":"java.lang.Runtime","method_name":"exec","taint_in":"20192035", "taint_out":"20192036", "stack":[]}
  ] 
}
```



#### Third-party component data

The third-party component data records the hash value, path, and the name of the third-party component, which is used to sort out the third-party component and analyze the vulnerabilities.

```json
{
  "type":"0x02",
  "detail":{
    "agent":"win-hostname-ip-key",
    "language":"Java",
    "sca_path":"/opt/apache-tomcat/bin/tomcat.jar",
    "sca_name":"struts2-core",
    "sca_signature":"83f745d2ebeaaffea24b3a4d486d1b5517e7f574",
    "algorithm":"SHA-1"
  }
}
```

### **Hook** method type 

- Entry method for `HTTP` request processing.
- Related methods of `Request` object to obtain external parameters.
- Related methods of `Response` set returning data.
- Methods related to taint propagation: string operations(string splicing, string interceptionm string reversal, etc.), Java collection type operations, Java IO operations(file IO/network IO), encryption and decryption methods(Base64 encryption and decryption, AES/DES encryption and decryption, RSA encryption and decryption, etc.)
- Methods related to triggering vulnerabilities: SMTP operation, sending HTTP requests, XML decoding,executing system commands, executing LDAP queries,  executing XPATH queries, file operations, JSON reverse Serializtion, etc.
- Framwork layer XSS, SQL injection and other related filtering methods.

#### Data processing 

According to the unique identification of the taint, the propagation process of the taint is completely marked to form a taint method pool, and then the taint identification method is abstracted and sent to the IAST cloud for subsequent vulnerability analysis.

**Importantly**, the unique identifier is composed of numbers and  does not contain task data, nor can it be used to reversely analyze the corresponding data. the methods will be abstracted to a certain degree to ensure that the vulnerability can be restored normally and hidden Customer-related name at the same time.

### **IAST** Cloud

The cloud accepts the method pool reported by the **Agent**, calculates the method call graph based on the unique identification of the method are related taints, and then uses the built-in vulnerability strategy(or custom vulnerability strategy) to match the corresponding vulnerability chain from the method call graph. If there is a chain, the vulnerability exists, If there is no chain, the vulnerability does not exist,

**As shown in the picture below**

![method_flow_chart](../assets/features/method_flow_charts.png)

**Strategy**

Method of specifying source point and sink point : getParameter() -> ProcessImpl.start()

**Vulnerability Chain**

getParameter() -> decode() -> exec() -> exec() -> ProcessBuilder.<init> -> ProcessBuilder.start -> ProcessImpl.start()

**Result**

Therefore, it is determined that there is a vulnerability.
