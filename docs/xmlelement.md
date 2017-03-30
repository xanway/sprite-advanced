# XmlElement xml节点操作类

----------

XmlElement对象用于操作xml对象，注意该对象不能通过构造函数生成，必须通过XmlDocument类的createElementByString()或createElementByFile()方法才能产生。

使用时需要在js中引入 ：

```javascript
var xmlelement = require("XmlElement"); 
```

**注：** 该组件为外置功能组件，打包时候需要选择。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ Array getElements()  获取所有子节点 ](#ff_0)
> 
> [Array getElementsByTag(tagName)  获取指定Tag的所有子节点 ](#ff_1)
>
>[ String getTag()   获取Xml对象Tag名  ](#ff_2)
>
>[ Json getAttrs()  获取节点所有属性  ](#ff_3)
>
>[ String getAttr(attrName)  获取节点属性  ](#ff_4)
>
>[ bool hasAttr(attrName)  节点是否具有该属性  ](#ff_5)
>
>[ String getText()  获取节点文本内容  ](#ff_6)


<span id="ff_0">**Array getElements()**</span>  

<code>获取所有子节点</code>     

参数：无  

返回值：数组，数组成员为XmlElement对象，若查找失败则返回length为0的空数组




<span id="ff_1">**Array getElementsByTag(tagName)**</span>  

<code>获取指定Tag的所有子节点</code>   

参数：

tagName：节点tag名，字符串类型

返回值：数组，数组成员为XmlElement对象，若查找失败则返回length为0的空数组


<span id="ff_2">**String getTag()**</span>  

<code>获取Xml对象Tag名</code>  

参数：无

返回值：Xml对象Tag名，字符串类型


<span id="ff_3">**Json getAttrs()**</span>  

<code>获取节点所有属性</code>

参数：无 

返回值：获取节点所有属性，Json类型；


<span id="ff_4">**String getAttr(attrName)**</span>  

<code>获取节点属性</code>  

参数： 

attrName：需查询节点属性名，字符串，必选项类型； 

返回值：查询的节点属性值，字符串类型；


<span id="ff_5">**bool hasAttr(attrName)**</span>  

<code>节点是否具有该属性</code>   

参数： 

attrName：需查询节点名，字符串，必选项类型； 

返回值：节点是否具有该属性，bool型

> true：具有该属性；
> 
> false：不具有该属性


<span id="ff_6">**String getText()**</span>  

<code>获取节点文本内容</code>

参数：无

返回值：当前节点文本内容，字符串类型   