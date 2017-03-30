# Console 拍照，摄像操作类

----------

Console日志输出类，主要用于程序调试用。

输出格式：  

Log类：time    [leave]    msg            
          
> time： 格式YYYY-MM-DD   hh:mm:ss:ms  系统自动生成  
> 
> leave：  输出日志级别，debug/log/info/warn/error  
> 
> msg：   需要输出消息即具体需打印信息，开发人员设置

使用时需要在js中引入 ：

```javascript
var console = require("Console"); 
```


**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  


本节目录：

>[ void setFilePath(filePath)  设置日志文件保存路径 ](#ff_0)
> 
> [String getFilePath()  获取日志文件保存路径 ](#ff_1)
>
>[ void debug(log)   调试日志输出  ](#ff_2)
>
>[ void log(log)   标准日志输出  ](#ff_3)
>
>[ void info(log)   信息日志输出  ](#ff_4)
>
>[ void warn(log)   告警日志输出  ](#ff_5)  
>
>[ void error(log)  错误日志输出  ](#ff_6)  


<span id="ff_0">**void setFilePath(filePath)**</span>  

<code>启动系统拍照/设置日志文件保存路径</code>    

参数：  

filePath：日志输出路径，支持res: file：前缀，字符串类型，必选项 

返回值：无 

**注：**  需要设置日志文件保存路径后日志方可正常输出


<span id="ff_1">**String getFilePath()**</span>  

<code>获取日志文件保存路径</code>   

参数：无 

返回值：日志保存路径，字符串类型，若未设置则返回null


<span id="ff_2">**void debug(log)**</span>  

<code>调试日志输出</code> 

参数：

log：需要输出日志，字符串类型，必选项

返回值：无  


<span id="ff_3">**void log(log)**</span>  

<code>标准日志输出</code> 

参数： 

log：需要输出日志，字符串类型，必选项  

返回值：无


<span id="ff_4">**void info(log)**</span>  

<code>信息日志输出</code> 

参数： 

log：需要输出日志，字符串类型，必选项  

返回值：无


<span id="ff_5">**void warn(log)**</span>  

<code>告警日志输出</code> 

参数： 

log：需要输出日志，字符串类型，必选项  

返回值：无


<span id="ff_6">**void error(log)**</span>  

<code>错误日志输出</code> 

参数： 

log：需要输出日志，字符串类型，必选项  

返回值：无