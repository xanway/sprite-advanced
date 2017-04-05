# ImageUtil 电话操作类

----------

 ImageUtil 图片处理工具类，用于开发者对图片自定义处理。

使用时需要在js中引入 ：

```javascript
var imageutil = require("ImageUtil"); 
```

**注：** 该组件为内置功能组件。

<h2 id="cid_1">js方法</h2>  

本节目录：

>[ void scale(jsonData,callBackFun)   缩放图片并保存到目标文件 ](#ff_0)
> 
> [void scaleByRate(jsonData,callBackFun)  根据缩放比例缩放图片并保存到目标文件 ](#ff_1)
> 
> [void scaleByFileSize (jsonData,callBackFun)   根据缩放后文件大小缩放图片并保存到目标文件 ](#ff_2)
> 
> [void clip(jsonData,callBackFun)    启动图片裁剪界面 ](#ff_3)
> 
> [void screenShot(jsonData, callFunction)  启动截屏](#ff_4)


<span id="ff_0">**void scale(jsonData,callBackFun)**</span>  

<code>缩放图片并保存到目标文件</code>  

缩放图片并保存到目标文件，结果通过回调函数返回   

参数：  
jsonData，缩放传递参数，Json对象，定义如下：  

> source：需要裁剪原图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> target：生成压缩后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> width：缩放后图片的宽度，单位像素，缩放后图片高度等比缩放，数字，可选项；
> 
> compress：图片压缩后质量比，数字类型，取值[1~100]，若不设置则默认100质量不压缩，可选项，注：对png格式图片无效；

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下：  

> code：回应状态码，数字[0,-1]
> 
> -  0：压缩图片成功；
> 
> -  -1：压缩图片失败；
> 
> source：需要转换原图片路径，字符串类型；
> 
> target：生成压缩后图片路径，字符串类型；
> 
> width：缩放后图片的宽度，单位像素，数字类型
> 
> compress：图片压缩后质量比，数字类型，取值[1~100]；

返回值：无




<span id="ff_1">**void scaleByFileSize (jsonData,callBackFun)**</span>  

<code>根据缩放后文件大小缩放图片并保存到目标文件</code>   

参数：
jsonData，缩放传递参数，Json对象，定义如下：  

> source：需要转换原图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> target：生成压缩后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> size：压缩后图片尺寸，数字类型，单位kb，实际的尺寸不会很准确，可能略大于或略小于目标尺寸，必选项。

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下： 

> code：回应状态码，数字[0,-1]
> 
> - 0：压缩图片成功；
> 
> - -1：压缩图片失败；
> 
> source：需要转换原图片路径，字符串类型；
> 
> target：生成压缩后图片路径，字符串类型；
> 
> size：压缩后图片尺寸，数字类型，单位kb；

返回值：无



<span id="ff_2">**void clip(jsonData,callBackFun)**</span>  

<code>启动图片裁剪界面</code> 

参数： 

jsonData，图片裁剪传递参数，Json对象，定义如下：

> source：需要裁剪图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> target：裁剪后图片路径，支持res:，file:前缀的本地路径，字符串类型，必选项；
> 
> cropWidth：裁剪图片宽度，数字类型，单位px，必选项；

callBackFun，结果回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：裁剪图片成功；
> 
> - -1：裁剪图片失败；
> 
> source：需要裁剪图片路径，字符串类型；
> 
> target：裁剪后图片路径，字符串类型；

返回值：无


<span id="ff_3">**void getCallRecords(jsonData,callbackFun)**</span>  

<code>获取系统通话记录</code>  


参数: 

jsonData：获取系统通话记录传入参数，Json对象定位如下：  

> type：电话记录类型，数字，必选项，[0,1,2,3,4]
> 
> - 0：所有类型；
> 
> - 1：拨出未接通；
> 
> - 2：拨出已接通；
> 
> - 3：拨入已接通；
> 
> - 4：拨入未接通； 

callBackFun：操作回调函数，函数具有json类型入参，入参定义如下：

> code：回应状态码，数字[0,-1]
> 
> - 0：获取通话记录成功；
> 
> - -1：获取通话记录失败；
> 
> datas：数组类型，数组中每项为Json对象，定义如下：
> 
> - type：电话记录类型，数字，[0,1,2,3,4]
>   -  0：所有类型；
>   -  1：拨出未接通；
>   - 2：拨出已接通；
>   - 3：拨入已接通；
>   - 4：拨入未接通； 
> 
> - number：电话号码，字符串类型；
> 
> - name：电话号码对应的手机通讯录联系人名称，字符串类型；
> 
> - startTime：拨出或拨入开始时间 字符串，输出格式为yyyy-mm-dd hh:mm:ss；
> 
> - endTime：拨出或拨入结束时间，字符串类型，输出格式为yyyy-mm-dd hh:mm:ss；
> 
> - duration：通话时长，数字类型，单位秒

返回值：无  

**注：** 仅Android支持
