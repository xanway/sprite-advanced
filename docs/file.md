# File 文件操作类

----------

 File 文件操作类，主要用于对文件的操作，比如读取文件，写入文件，创建文件目的，删除文件等操作。


使用时需要在js中引入 ：

```javascript
var file = require("File"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ bool isDir(path)   判断指定路径文件是否为文件夹 ](#ff_0)
> 
> [bool fileExist(path)   判断指定路径文件是否存在 ](#ff_1)
>
>[ bool dirExist(path)   判断指定路径目录是否存在  ](#ff_2)
>
> [bool makeDir(path)  创建指定文件夹 ](#ff_3)
> 
>[int getFileSize(path)   获取指定文件大小 ](#ff_4)
> 
> [Json getFileInfo(path)   获取文件相关信息 ](#ff_5)
>
>[ String readTextFile(path)   读取文本类型文件（同步方式）  ](#ff_6)
>
> [void readTextFileAsyn(path,callFunction)  读取文本类型文件（异步方式） ](#ff_7)
>
>[ bool writeTextFile(jsonData, text)   将字符串写入文本类型文件(同步方式) ](#ff_8)
> 
> [void writeTextFileAsyn(jsonData, text,callFunction)  将字符串写入文本类型文件（异步方式） ](#ff_9)
>
>[ bool copyFile(jsonData)   拷贝文件（同步方式）  ](#ff_10)
>
> [void copyFileAsyn(jsonData,callFunction)  拷贝文件（异步方式） ](#ff_11)
> 
>[bool deleteFile(jsonData)   删除文件（同步方式） ](#ff_12)
> 
> [void deleteFileAsyn(jsonData,callFunction)  删除文件（异步方式） ](#ff_13)
>
>[ bool moveFile(jsonData)   移动文件（同步方式 ） ](#ff_14)
>
> [void moveFileAsyn(jsonData,callFunction)   移动文件（异步方式） ](#ff_15)
> 
> [void copyDirAsyn(jsonData,callFunction)   拷贝文件夹（异步方式） ](#ff_16)
> 
> [void deleteDirAsyn(jsonData,callFunction)   删除文件夹（异步方式） ](#ff_17)
> 
> [void moveDirAsyn(jsonData,callFunction)   移动文件夹（异步方式） ](#ff_18)
> 
> [Array listFiles(jsonData)   返回文件夹下的子文件（同步方式） ](#ff_19)
> 
> [Array listFilesAsyn(jsonData, callFunction)   返回文件夹下的子文件（异步方式）](#ff_20)
> 
> [String md5(path)  返回文件md5值 ](#ff_21)
> 
> [void zip(jsonData, callFunction)  压缩文件/文件夹至指定目录](#ff_22)
> 
> [void unZip(jsonData, callFunction)   解压文件至指定路径 ](#ff_23) 
> 
> [String getAbsolutePath(path)  获取res:开头的本地url地址对应的绝对路径 ](#ff_24) 


<span id="ff_0">**bool isDir(path)**</span>  

<code>判断指定路径文件是否为文件夹</code>    

参数：  

path：本地文件名，res: file: 前缀

返回值：是否为文件夹，bool型 

> true：文件夹类型；
> 
> false：文件类型；





<span id="ff_1">**bool fileExist(path);**</span>  

<code>判断指定路径文件是否存在</code>

参数：  

path：本地文件名，res: file: 前缀

返回值：指定路径文件是否存在，bool型 

> true：文件存在；
> 
> false：文件不存在；




<span id="ff_2">**bool dirExist(path)**</span>  

<code>判断指定路径目录是否存在</code>   

参数：  

path：本地目录名，res: file: 前缀

返回值：指定路径目录是否存在，bool型

> true：文件存在；
> 
> false：文件不存在；



<span id="ff_3">**bool makeDir(path)**</span>  

<code>创建指定文件夹</code>  

参数：  

path：需要创建目录名，res: file: 前缀

返回值：文件夹是否创建成功，bool型

> true：文件存在；
> 
> false：文件不存在；


<span id="ff_4">**int getFileSize(path)**</span>  

<code>获取指定文件大小</code>  

参数：  

path：本地文件名，res: file: 前缀

返回值：指定文件大小，数字类型，单位字节；



<span id="ff_5">**Json getFileInfo(path)**</span>  

<code>获取文件相关信息</code>  

参数：  

path：本地文件名，res: file: 前缀

返回值：文件相关属性，Json对象，定义如下：  

> size：文件大小，数字类型，单位字节；
> 
> name：文件名，字符串类型；
> 
> absoultePath：文件绝对路径，字符串类型；
> 
> lastModified：文件上次修改时间，数字类型，单位：毫秒，从1970年1月1日开始算 

**注：** 若文件不存在则返回null


<span id="ff_6">**String readTextFile(path)**</span>  

<code>读取文本类型文件（同步方式）</code>  

适用于小文件场景

参数：  

path：本地文件名，res: file: 前缀

返回值：读取文件文本，字符串类型，若读取失败则返回null


<span id="ff_7">**void readTextFileAsyn(path,callFunction)**</span>  

<code>读取文本类型文件（异步方式）</code>  

适用于大文件场景

参数：  

path：本地文件名，res: file: 前缀  

callFunction：读取完毕回调函数

>参数为字符串，标识读取内容，若读取失败则该参数为null

返回值：无



<span id="ff_8">**bool writeTextFile(jsonData, text)**</span>  

<code>将字符串写入文本类型文件（同步方式）</code>  

适用于小文件场景

参数：  

jsonData：写入参数设置，json类型，定义如下：  

>    path：写入目标文件路径，res: file:前缀，字符串类型，必选项；  
> 
>    append：是否追加方式写入文件，bool型，可选项 
>    
> -   true：追加模式；
>    
> -  false：覆盖模式(默认)，；

text：需要写入文本，字符串类型，必选项；

返回值：写入文件是否成功，bool型

> true：写入成功；
> 
> false：写入失败；




<span id="ff_9">**void writeTextFileAsyn(jsonData, text,callFunction)**</span>  

<code>将字符串写入文本类型文件（异步方式）</code>  

适用于大文件场景

参数：  

jsonData：写入参数设置，json类型，定义如下：  

>    path：写入目标文件路径，res: file:前缀，字符串类型，必选项；  
> 
>    append：是否追加方式写入文件，bool型，可选项 
>    
> -   true：追加模式；
>    
> -  false：覆盖模式(默认)，；

text：需要写入文本，字符串类型，必选项；

callFunction：写入完毕回调函数，参数为数字，标识写入是否成功，[0,-1]

> 0：写入文件成功；
> 
> -1：写入文件失败

返回值：无 



<span id="ff_10">**bool copyFile(jsonData)**</span>  

<code>拷贝文件（同步方式）</code>  

适用于小文件场景

参数：  

jsonData：拷贝文件参数，Json对象，定义如下：  

>   srcPath：原始文件路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：目的文件路径，res: file:前缀，字符串类型，必选项；  

返回值：拷贝文件是否成功，bool型

> true：拷贝成功；
> 
> false：拷贝失败；


<span id="ff_11">**void copyFileAsyn(jsonData,callFunction)**</span>  

<code>拷贝文件（异步方式）</code>  

适用于大文件场景

参数：  

jsonData：拷贝文件参数，Json对象，定义如下：  

>   srcPath：原始文件路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：目的文件路径，res: file:前缀，字符串类型，必选项；  

callFunction：拷贝文件回调函数，存在数字类型入参标识拷贝是否成功，[0,-1]

> 0：拷贝成功；
> 
> -1：拷贝失败；  


返回值：无 


<span id="ff_12">**bool deleteFile(jsonData)**</span>  

<code>删除文件（同步方式）</code>  

适用于小文件场景

参数：
jsonData：删除文件参数，Json对象，定义如下： 

>   srcPath：需删除文件路径，res: file:前缀，字符串类型，必选项； 


返回值：文件是否删除成功，bool

> true：删除成功；
> 
> false：删除失败；



<span id="ff_13">**void deleteFileAsyn(jsonData,callFunction)**</span>  

<code>删除文件（异步方式）</code>  

适用于大文件场景

参数：  

jsonData：删除文件参数，Json对象，定义如下： 

>   srcPath：需删除文件路径，res: file:前缀，字符串类型，必选项； 


callFunction：删除文件回调函数，存在数字类型入参标识删除是否成功，[0,-1]

> 0：删除成功；
> 
> -1：删除失败； 

返回值：无  


<span id="ff_14">**bool moveFile(jsonData)**</span>  

<code>移动文件（同步方式）</code>  


参数： 

jsonData：拷贝文件参数，Json对象，定义如下：  

>   srcPath：原始文件路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：目的文件路径，res: file:前缀，字符串类型，必选项；  

返回值：移动文件是否成功，bool型

> true：移动成功；
> 
> false：移动失败




<span id="ff_15">**void moveFileAsyn(jsonData,callFunction)**</span>  

<code>移动文件（异步方式）</code>  


参数： 

jsonData：拷贝文件参数，Json对象，定义如下：  

>   srcPath：原始文件路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：目的文件路径，res: file:前缀，字符串类型，必选项；  

callFunction：移动文件回调函数，参数为数字，标识移动是否成功，[0,-1]  

> 0：移动成功；
> 
> -1：移动失败；  


返回值：无 


<span id="ff_16">**void copyDirAsyn(jsonData,callFunction)**</span>  

<code>拷贝文件夹（异步方式）</code>   

参数： 

jsonData：拷贝文件夹参数，Json对象，定义如下：  

>   srcPath：原始文件夹路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：目的文件夹路径，res: file:前缀，字符串类型，必选项； 

callFunction：拷贝文件夹回调函数，参数为数字，标识拷贝是否成功，[0,-1]

> 0：拷贝成功；
> 
> -1：拷贝失败；  

返回值：无 


<span id="ff_17">**void deleteDirAsyn(jsonData,callFunction)**</span>  

<code>删除文件夹（异步方式）</code>   


参数： 

jsonData：删除文件夹参数，Json对象，定义如下：  

>  srcPath：需删除文件夹路径，res: file:前缀，字符串类型，必选项； 

callFunction：删除文件夹回调函数，参数为数字，标识删除是否成功，[0,-1]

> 0：删除成功；
> 
> -1：删除失败；  

返回值：无 


<span id="ff_18">**void moveDirAsyn(jsonData,callFunction)**</span>  

<code>移动文件夹（异步方式）</code>   

参数： 

jsonData：移动文件夹参数，Json对象，定义如下： 

>   srcPath：原始文件夹路径，res: file:前缀，字符串类型，必选项； 
> 
>   dstPath：目的文件夹路径，res: file:前缀，字符串类型，必选项；

callFunction：移动文件夹回调函数，参数为数字，标识移动是否成功，[0,-1]

>  0：移动成功；
>     
>   -1：移动失败；  

返回值：无   

**注：** 原始文件夹与目的文件夹非同级  


<span id="ff_19">**Array listFiles(jsonData)**</span>  

<code>返回文件夹下的子文件（同步方式）</code>  

参数：  

jsonData：查询参数，Json对象，定义如下：  

>   path：需要遍历文件夹路径，res: file:前缀，字符串类型，必选项；  
>   
>    filter：查询正则表达式，字符串类型，可选项；  
>    
>    type：返回类型，数字类型，可选项，[0,1,2]
>    
>  -  0：全部返回（默认）；
>  
>  -  1：返回文件类型；
>  
>  -  2：返回文件夹类型；

返回值：文件夹下的子文件全路径，字符串数组，若查询失败返回空数组 



<span id="ff_20">**Array listFilesAsyn(jsonData, callFunction)**</span>  

<code>返回文件夹下的子文件（异步方式）</code>  

 参数：  

jsonData：查询参数，Json对象，定义如下：  

>   path：需要遍历文件夹路径，res: file:前缀，字符串类型，必选项；  
>   
>    filter：查询正则表达式，字符串类型，可选项；  
>    
>    type：返回类型，数字类型，可选项，[0,1,2]
>    
>  -  0：全部返回（默认）；
>  
>  -  1：返回文件类型；
>  
>  -  2：返回文件夹类型；

callFunction：返回子文件回调函数

> 参数为字符串数组，标识文件夹下的子文件全路径，若查询失败返回空数组  


返回值：无 


<span id="ff_21">**Array listFilesAsyn(jsonData, callFunction)**</span>  

<code>返回文件md5值</code>    

参数：  

path：本地文件路径，res: file: 前缀

返回值：文件md5值，字符串类型，字母小写


<span id="ff_22">** zip(jsonData, callFunction)**</span>  

<code>压缩文件/文件夹至指定目录</code>  

 参数：  

jsonData：压缩参数，Json对象，定义如下：  

>   srcPath：需要压缩文件/文件夹路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：压缩后zip文件路径，res: file:前缀，字符串类型，必选项；
>   
>   password：压缩密码，字符串类型，可选项，默认无密码；

callFunction：压缩回调函数，入参Json对象，定义如下：  

>    code：是否压缩成功，数字类型，【0,-1】
>    
> -   0：压缩成功；
> 
> -  -1：压缩失败；
>    
>    dstPath：压缩成功后文件全路径，字符串类型；


<span id="ff_23">**void unZip(jsonData, callFunction)**</span>  

<code>解压文件至指定路径</code>  

参数：  

jsonData：压缩参数，Json对象，定义如下：  

>   srcPath：需要解压文件路径，res: file:前缀，字符串类型，必选项；
>   
>   dstPath：解压后文件夹路径，res: file:前缀，字符串类型，必选项；
>   
>   password：解压缩密码，字符串类型，可选项，默认无密码；

callFunction：解压回调函数，入参Json对象，定义如下：  

>  code：是否解压成功，数字类型，[0,-1]
> 
> - 0：解压成功；
> 
> - -1：解压失败；
> 
>  dstPath：解压成功后文件全路径，字符串类型；


<span id="ff_24">**String getAbsolutePath(path)**</span>  

<code>获取res:开头的本地url地址对应的绝对路径</code>  

参数： 

path：需要转换的url地址，res:前缀路径，字符串类型 

返回值：绝对路径，字符串类型
