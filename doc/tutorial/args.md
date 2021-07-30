# Agent args

### debug

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | Restart the application, add “-Ddebug=”  when starting an application                          |
| Parameter Type | Boolean                                                      |
|   Source   | Command line arguments                                                   |
| Optional Parameter | true｜false                                                  |
|  Default Value  | false                                                        |
| Parameter Meaning | <div style="width: 300pt">After this function is enabled, check whether the core detection engine exists in the local temporary directory, load the local detection engine, and start it. |

### project.name

|   Attribute   | Value                                        |
| :------: | :---------------------------------------- |
| Effective Way | Restart the application, add “-Dproject.name=” when starting an application |
| Parameter Type | String                                    |
|   Source   | Configuration file                                  |
| Optional Parameter | Any String                                |
|  Default Value  | Demo Project                              |
| Parameter Meaning | <div style="width: 300pt">Project name.                                  |

### iast.mode

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.mode=” when starting an application                       |
| Parameter Type | String                                                       |
|   Source   | Configuration file                                                     |
| Optional Parameter | hunter, normal                                               |
|  Default Value  | normal                                                       |
| Parameter Meaning | <div style="width: 300pt">Patterns of vulnerability testing |

### iast.server.mode

|   Attribute   | Value                                                           |
| :------: | :----------------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.server.mode=” when starting an application                |
| Parameter Type | String                                                       |
|   Source   | Configuration file                                                     |
| Optional Parameter | local, remote                                                |
|  Default Value  | remote                                                       |
| Parameter Meaning | <div style="width: 300pt">The local mode supports single vulnerability verification, project vulnerability batch verification, POST request package display, and stain location and stain display |

### iast.proxy.enable

|   Attribute   | Value                                             |
| :------: | :--------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.proxy.enable=” when starting an application |
| Parameter Type | Boolean                                        |
|   Source   | Configuration file                                       |
| Optional Parameter | true, false                                    |
|  Default Value  | false                                          |
| Parameter Meaning | <div style="width: 300pt">Whether the HTTP proxy mode is enabled                           |

### iast.proxy.host

|   Attribute   | Value                                           |
| :------: | :------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.proxy.host=” when starting an application |
| Parameter Type | String                                       |
|   Source   | Configuration file                                     |
| Optional Parameter |                                              |
|  Default Value  | false                                        |
| Parameter Meaning | <div style="width: 300pt">Domain name of the HTTP proxy                           |

### iast.proxy.port

|   Attribute   | Value                                           |
| :------: | :------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.proxy.port=” when starting an application |
| Parameter Type | String                                       |
|   Source   | Configuration file                                     |
| Optional Parameter |                                              |
|  Default Value  | 80                                           |
| Parameter Meaning | <div style="width: 300pt">Port of the HTTP proxy                            |

### iast.service.report.interval

|   Attribute   | Value                                                        |
| :------: | :-------------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.service.report.interval=” when starting an application |
| Parameter Type | Integer                                                  |
|   Source   | Configuration file                                                  |
| Optional Parameter | Any integer number                                              |
|  Default Value  | 60000                                                     |
| Parameter Meaning | <div style="width: 300pt">The interval between sending reports                          |

### iast.service.replay.interval

|   Attribute   | Value                                                        |
| :------: | :-------------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.service.replay.interval=” when starting an application |
| Parameter Type | Integer                                                  |
|   Source   | Configuration file                                                  |
| Optional Parameter | Any integer number                                              |
|  Default Value  | 300000                                                    |
| Parameter Meaning | <div style="width: 300pt">The time interval between playback                               |

### iast.engine.delay.time

|   Attribute   | Value                                                  |
| :------: | :-------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.engine.delay.time=” when starting an application |
| Parameter Type | Integer                                            |
|   Source   | Configuration file                                            |
| Optional Parameter | Any integer number                                        |
|  Default Value  | 10                                                  |
| Parameter Meaning | <div style="width: 300pt">Delayed start function                              |

### iast.dump.class.enable

|   Attribute   | Value                                                  |
| :------: | :-------------------------------------------------- |
| Effective Way | Restart the application, add “-Diast.dump.class.enable=” when starting an application |
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

### iast.name

|   Attribute   | Value                       |
| :------: | :----------------------- |
| Effective Way | Restart the application                 |
| Parameter Type | String                   |
|   Source   | Configuration file                 |
| Optional Parameter | lingzhi-Enterprise 1.0.0 |
|  Default Value  | lingzhi-Enterprise 1.0.0 |
| Parameter Meaning | <div style="width: 300pt">iast name                |

### iast.version

|   Attribute   | Value           |
| :------: | :----------- |
| Effective Way | Restart the application     |
| Parameter Type | String       |
|   Source   | Configuration file     |
| Optional Parameter | 1.0.0        |
|  Default Value  | 1.0.0        |
| Parameter Meaning | <div style="width: 300pt">iast version |

### iast.response.name

|   Attribute   | Value                 |
| :------: | :----------------- |
| Effective Way | Restart the application           |
| Parameter Type | String             |
|   Source   | Configuration file           |
| Optional Parameter | lingzhi            |
|  Default Value  | lingzhi            |
| Parameter Meaning | <div style="width: 300pt">iast response name |

### iast.response.value

|   Attribute   | Value                 |
| :------: | :----------------- |
| Effective Way | Restart the application           |
| Parameter Type | String             |
|   Source   | Configuration file           |
| Optional Parameter | lingzhi            |
|  Default Value  | lingzhi            |
| Parameter Meaning | <div style="width: 300pt">iast response name |

### iast.server.url

|   Attribute   | Value                                  |
| :------: | :---------------------------------- |
| Effective Way | Restart the application                            |
| Parameter Type | String                              |
|   Source   | Configuration file                            |
| Optional Parameter |                                     |
|  Default Value  | http://openapi.iast.huoxian.cn:8000 |
| Parameter Meaning | <div style="width: 300pt">server url                          |

### iast.server.token

|   Attribute   | Value         |
| :------: | :--------- |
| Effective Way | Restart the application   |
| Parameter Type | String     |
|   Source   | Configuration file   |
| Optional Parameter |            |
|  Default Value  |            |
| Parameter Meaning | <div style="width: 300pt">User's Token |

### iast.allhook.enable

|   Attribute   | Value       |
| :------: | :------- |
| Effective Way | Restart the application |
| Parameter Type | Boolean  |
|   Source   | Configuration file |
| Optional Parameter |          |
|  Default Value  | false    |
| Parameter Meaning | <div style="width: 300pt">         |

### app.name

|   Attribute   | Value       |
| :------: | :------- |
| Effective Way | Restart the application |
| Parameter Type | String   |
|   Source   | Configuration file |
| Optional Parameter |          |
|  Default Value  | LingZhi  |
| Parameter Meaning | <div style="width: 300pt">app name |

### engine.status

|   Attribute   | Value       |
| :------: | :------- |
| Effective Way | Restart the application |
| Parameter Type | String   |
|   Source   | Configuration file |
| Optional Parameter |          |
|  Default Value  |          |
| Parameter Meaning | <div style="width: 300pt">engine status |

### engine.name

|   Attribute   | Value       |
| :------: | :------- |
| Effective Way | Restart the application |
| Parameter Type | String   |
|   Source   | Configuration file |
| Optional Parameter |          |
|  Default Value  |          |
| Parameter Meaning | <div style="width: 300pt">engine name |

### jdk.version

|   Attribute   | Value       |
| :------: | :------- |
| Effective Way | Restart the application |
| Parameter Type | String   |
|   Source   | Configuration file |
| Optional Parameter |          |
|  Default Value  |          |
| Parameter Meaning | <div style="width: 300pt">jdk version  |
