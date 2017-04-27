#  数据交互

----------

<h2  id="cid_0">数据共享</h2>

**内存数据共享**

<code>MemCache应用级存储</code>：

通过MemCache工具类来存储/获取所需数据,应用允许过程中可跨页面使用,支持对数字,字符串,数组,JSON类型的直接存入及读取,[详见MemCache类说明](https://gitdocument.exmobi.cn/sprite-advanced/memcache.html)；

示例：

```javascript

    //页面存入数据操作
    var memCache = require("MemCache");
    //存入数字
    memCache.setItem("key1",22.5);
    //存入字符串
    memCache.setItem("key2", "Sprite");
    //存入数组
    memCache.setItem("key3", [ "姓名", "电话", "日期" ]);
    //存入JSON
    memCache.setItem("key4", {
        "k1" : "v1",
        "k2" : "v2",
        "k3" : "v3",
        "k4" : "v4"
    });

    //应用中其他页面读取数据
    var memCache = require("MemCache");
    //读取数字 
    var num = memCache.getItem("key1");
    //读取字符串
    var str = memCache.getItem("key2");
    //读取数组
    var arr = memCache.getItem("key3");
    var value1 = arr[1];
   //读取JSON
    var jso = memCache.getItem("key4");
    var value2 = jso.k1;
```

<code>Clipboard系统剪切板</code>：

使用Clipboard系统剪切板工具类,可实现系统级对字符串数据存储,[详见Clipboard类说明](https://gitdocument.exmobi.cn/sprite-advanced/clipboard.html)。


<code>全局变量页面存储</code>：

使用JavaScript全局变量存取/设置数据,可实现页面内数据共享。

示例：

```javascript
var name;
//设置
function setName(){
  name = "张三";
}
//获取
function getName(){
  return "Sprite:" + name;
}
```

**文件数据共享** 

<code>DiskCache文件缓存</code>：


使用DiskCache工具类来存储/获取所需数据,应用退出后重新进入数据依然保存,[详见DiskCache类说明](https://gitdocument.exmobi.cn/sprite-advanced/diskcache.html)；

示例：

```javascript

//存入数据操作
    var diskCache = require("DiskCache");
    //存入数字
    diskCache.setItem("key1",22.5);
    //存入字符串
    diskCache.setItem("key2", "Sprite");
    //存入数组
    global.setMemory("key3", [ "姓名", "电话", "日期" ]);
    //存入JSON
    global.setMemory("key4", {
        "k1" : "v1",
        "k2" : "v2",
        "k3" : "v3",
        "k4" : "v4"
    });

    //读取数据
    var diskCache = require("DiskCache");
    //读取数字 
    var num = diskCache.getItem("key1");
    //读取字符串
    var str = diskCache.getItem("key2");
    //读取数组
    var arr = diskCache.getItem("key3");
    var value1 = arr[1];
   //读取JSON
    var jso = diskCache.getItem("key4");
    var value2 = jso.k1;
```

<code>标准文件存储</code>：

使用File工具类实现对文件读/写操作,可用于开发者保存所需格式数据,[详见File类说明](https://gitdocument.exmobi.cn/sprite-advanced/file.html)。

<code>数据库</code>：

使用Db数据库操作类实现对sqllite数据库操作,[详见Db类说明](https://gitdocument.exmobi.cn/sprite-advanced/ui.html)。


<code>加密数据库</code>：

使用DbCipher加密数据库操作类实现对sqllite加密数据库操作,[详见DbCipher类说明](https://gitdocument.exmobi.cn/sprite-advanced/dbcipher.html)。

<h2 id="cid_1">数据传递</h2>

**消息传递** 

通过on()订阅消息,fire()发送消息,off()退订消息实现数据消息传递,支持页面内消息传递及跨页面消息传递,[详见事件触发相关说明](https://gitdocument.exmobi.cn/sprite-advanced/jjcfjz.html)。


**页面数据传递**

支持开启/关闭页面中实现页面级数据传递,通过openPage() 和 closePage()实现数据交互。

<code>打开页面数据传递及获取</code>：

1：A页面打开B页面,通过Window对象openPage(jsonData)传递参数,该参数支持数字类型,字符串类型,数组类型,JSON类型格式；

2：B页面通过Window对象getData()方法获取传递参数；

<code>关闭页面数据传递及获取</code>：

1：A页面打开B页面；

2：B页面关闭时,通过Window对象closePage(jsonData)传递参数,该参数支持数字类型,字符串类型,数组类型,JSON类型格式；

3：A页面设置对系统事件 "result" 监听,可获取相关B页面关闭回传数据；



