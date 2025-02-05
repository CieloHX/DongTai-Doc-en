# Agent args

## Parameter Table

### debug

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Ddebug=<true or false>`  when starting an application                          |
| Parameter Type | Boolean                                                      |
|   Source   | Command line arguments                                                   |
| Optional Parameter | true｜false                                                  |
|  Default Value  | false                                                        |
| Parameter Meaning | <div style="width: 300pt">After this function is enabled, check whether the core detection engine exists in the local temporary directory, load the local detection engine, and start it. |

### project.name

|   Attribute   | Value                                        |
| :------: | :---------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Dproject.name=<Demo>` when starting an application |
| Parameter Type | String                                    |
|   Source   | Configuration file                                  |
| Optional Parameter | Any String                                |
|  Default Value  | Demo Project                              |
| Parameter Meaning | <div style="width: 300pt">Project name.                                  |

### iast.mode

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.mode=<hunter or normal>` when starting an application                       |
| Parameter Type | String                                                       |
|   Source   | Configuration file                                                     |
| Optional Parameter | hunter, normal                                               |
|  Default Value  | normal                                                       |
| Parameter Meaning | <div style="width: 300pt">Patterns of vulnerability testing |

### iast.server.mode

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.server.mode=<local or remote>` when starting an application                |
| Parameter Type | String                                                       |
|   Source   | Configuration file                                                     |
| Optional Parameter | local, remote                                                |
|  Default Value  | remote                                                       |
| Parameter Meaning | <div style="width: 300pt">The local mode supports single vulnerability verification, project vulnerability batch verification, POST request package display, and stain location and stain display |

### iast.proxy.enable

|   Attribute   | Value                                             |
| :------: | :--------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.proxy.enable=<true or false>` when starting an application |
| Parameter Type | Boolean                                        |
|   Source   | Configuration file                                       |
| Optional Parameter | true, false                                    |
|  Default Value  | false                                          |
| Parameter Meaning | <div style="width: 300pt">Whether the HTTP proxy mode is enabled                           |

### iast.proxy.host

|   Attribute   | Value                                           |
| :------: | :------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.proxy.host=<ip>` when starting an application |
| Parameter Type | String                                       |
|   Source   | Configuration file                                     |
| Optional Parameter |                                              |
|  Default Value  | false                                        |
| Parameter Meaning | <div style="width: 300pt">Domain name of the HTTP proxy                           |

### iast.proxy.port

|   Attribute   | Value                                           |
| :------: | :------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.proxy.port=<port>` when starting an application |
| Parameter Type | String                                       |
|   Source   | Configuration file                                     |
| Optional Parameter |                                              |
|  Default Value  | 80                                           |
| Parameter Meaning | <div style="width: 300pt">Port of the HTTP proxy                            |

### iast.service.report.interval

|   Attribute   | Value                                                        |
| :------: | :-------------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.service.report.interval=<60000>` when starting an application |
| Parameter Type | Integer                                                  |
|   Source   | Configuration file                                                  |
| Optional Parameter | Any integer number                                              |
|  Default Value  | 60000                                                     |
| Parameter Meaning | <div style="width: 300pt">The interval between sending reports                          |

### iast.service.replay.interval

|   Attribute   | Value                                                        |
| :------: | :-------------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.service.replay.interval=<300000>` when starting an application |
| Parameter Type | Integer                                                  |
|   Source   | Configuration file                                                  |
| Optional Parameter | Any integer number                                              |
|  Default Value  | 300000                                                    |
| Parameter Meaning | <div style="width: 300pt">The time interval between playback                               |

### iast.engine.delay.time

|   Attribute   | Value                                                  |
| :------: | :-------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.engine.delay.time=<10>` when starting an application |
| Parameter Type | Integer                                            |
|   Source   | Configuration file                                            |
| Optional Parameter | Any integer number                                        |
|  Default Value  | 10                                                  |
| Parameter Meaning | <div style="width: 300pt">Delayed start function                              |

### iast.dump.class.enable

|   Attribute   | Value                                                  |
| :------: | :-------------------------------------------------- |
| Effective Way | <div style="width: 300pt">Restart the application, add `-Diast.dump.class.enable=<true or false>` when starting an application |
| Parameter Type | Boolean                                             |
|   Source   | Configuration file                                            |
| Optional Parameter | true, false                                         |
|  Default Value  | false                                               |
| Parameter Meaning | <div style="width: 300pt">Whether to dump modified bytecode                            |

### iast.dump.class.path

|   Attribute   | Value                    |
| :------: | :-------------------- |
| Effective Way | Restart the application              |
| Parameter Type | String                |
|   Source   | Configuration file              |
| Optional Parameter | Any path with permission        |
|  Default Value  | /tmp/iast-class-dump/ |
| Parameter Meaning | <div style="width: 300pt">Path to dump bytecode     |

### iast.server.url

|   Attribute   | Value                                  |
| :------: | :---------------------------------- |
| Effective Way | Restart the application                            |
| Parameter Type | String                              |
|   Source   | Configuration file                            |
| Optional Parameter |                                     |
|  Default Value  | http://openapi.iast.huoxian.cn:8000 |
| Parameter Meaning | <div style="width: 300pt">server url                          |

## Test Case

> Take the test project spring demo as an example.

### 1. When you need to bind your application to the cloud project SpringDemo:

```
java -javaagent:/path/to/agent.jar -Dproject.name=SpringDemo -jar SpringDemo.jar
```

### 2. Local debugging is required when you need to troubleshoot agent errors or secondary development of the agent:

```
java -javaagent:/path/to/agent.jar -Ddebug.name=true -jar SpringDemo.jar
```

### 3. If starting the Agent affects the running of applications, you need to set the delay for starting the Agent. For example, 15 seconds:
```
java -javaagent:/path/to/agent.jar -Diast.engine.delay.time=15 -jar SpringDemo.jar
```

### 4. When checking agent exceptions or studying the principle of bytecode conversion, check the converted bytecode file in the /tmp/class:
```
java -javaagent:/path/to/agent.jar -Diast.dump.class.enable=true -jar SpringDemo.jar
```

### 5. The current network is unable to access [DongTai](https://iast.huoxian.cn). You need to set the HTTP proxy. For example, set the proxy to 10.100.100.1:80: 

```
java -javaagent:/path/to/agent.jar -Diast.proxy.enable=true -Diast.proxy.host=127.0.0.1 -Diast.proxy.host=80 -jar SpringDemo.jar
```

### 6. When set the detection capability to Hunter /normal:
- hunter: code audit
- normal: Internal detection vulnerabilities
```
java -javaagent:/path/to/agent.jar -Diast.mode=hunter -jar SpringDemo.jar
```