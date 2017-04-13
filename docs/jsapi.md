# js功能组件概述


----------

Sprite采用CommonJS规范，通过require("模块标识")来实现对系统api对象引用，如使用Device对象方法。

```javascript
     var device = require("Device"); 
     var version = device.getVersion();
```


<h2 id="cid_1">js组件类别</h2>   

**基础类**  

> [App：应用信息获取类](https://gitdocument.exmobi.cn/sprite-advanced/app.html)
> 
> Window：页面操作相关类
> 
> Document：页面Dom操作类
> 
> Device：设备信息获取类
> 
> Native：原生程序相关操作类
> 
> Encryption：编/解码工具类
> 
> Time：定时器类


**数据存储**  

> File：文件操作类
> 
> Db：数据库操作类
> 
> DbCipher：加密数据库操作类
> 
> MemCache：内存缓存存取类
> 
> DiskCache：磁盘缓存存取类
> 
> Clipboard：系统剪切板类


**网络相关**  

> Http：Http网络操作类
> 
> Socket：Socket网络操作类
> 
> NetInfo：网络信息相关类


**界面相关**   

> UI：界面相关操作类
> - 包括：alert，toast，confirm，selectFile，selectImage，selectTime，selectDate等

**多媒体**  

> Audio：音频操作相关类
> 
> - 包括：startRecord开始录音，stopRecord停止录音， playAudio播放音频，stopAudio停止播放音频等
> 
> Video：视频操作相关类
> 
> - 包括：recordShortVideo小视频录制，playVideo视频播放等

**扫描拍照**  

> Scan：条码/二维码扫描类 
> 
> Camera：拍照，摄像操作类 


**电话相关**  

> Phone：电话，短信，邮件操作类  
> 
> Contact：通讯录操作类


**定位相关**  

> Location：标准定位类 
> 
> BaiduLocation：百度定位类


**地图相关**  

> MapUtil：地图工具类
> 
> - 包括：坐标转换，百度地图兴趣点检索，启动导航等   


**硬件相关**  

> MotionSensor：运动传感器类 
> 
> Compass：罗盘类
> 
> MovementDetect：移动检测类 
> 
> Bluetooth：蓝牙通信类 
> 
> Nfc：近场通信类 
> 
> 3dTouch：iOS 3Dtouch类；


**图片处理**  

> Image：图片处理相关类 
> 
> openDrawingBoard打开画图板操作界面等；


**支付相关**  


> AliPay：支付宝操作类 
> 
> WxPay：微信支付操作类 
> 
> UpPay：银联支付操作类 
> 
> IapPay：苹果虚拟支付工具类


**VPN相关**  

> Sangfor：深信服vpn类 

**分享相关**  

> Qq：QQ分享操作类 
> 
> WeiBo：微博分享操作类 
> 
> WeiXin：微信分享操作类 
> 
> ShareUtil：综合分享工具类，提供如一键分享等方法


**推送push**  

> LocationPush：本地通知相关类
> 
> FhPush：烽火Push操作类 
> 
> BaiduPush：百度Push操作类 
> 
> GeTuiPush：个推Push操作类 
> 
> AjPush：极光Push操作类


**IM聊天**  

> FhIm：烽火Im操作类 
> 
> RlyIm：容联云操作类


**客服系统**  

> MeChat：美洽客服类


**统计相关**  

> UmengMtj：友盟日志统计
> 
> BaiduMtj：百度日志统计


**身份证识别**  

> HwCard：汉王身份证

**语音合成**  

> BaiduTts：百度语音合成
> 
> BaiduVoice：百度语音识别

**短信验证码发送**

> Mob：mob免费短信工具类  

**打车**  

> Didi：滴滴打车


**ExMobi服务器对接**  

> AccessAuth：ExMobi服务器鉴权组件类 


<h2 id="cid_2">js组件打包功能分类</h2>

考虑到实际应用需求，Sprite功能组件分为内置功能组件及外置功能组件，如下表所示：  

> 内置功能组件：Sprite基础包预制功能组件；
> 
> 外置功能组件：构建应用需求选择性添加功能组件；

**内置功能组件**  

> App  
> Window  
> Document  
> Device  
> Native  
> Encryption  
> Time  
> Http  
> NetInfo  
> File  
> UI  
> MemCache  
> DiskCache  
> Camera  
> Console  
> Pixel  
> ImageUtil  
> Location  


**外置功能组件**  

> Db  
> DbCipher  
> Barcode  
> XmlDocument  
> XmlElement  
> AccessAuth  
> VideoUtil  
> Phone  
> Sms  
> Contact  
> AudioPlay  
> AudioRecord  
> MapUtil  
> IapPay  
> WeiXin  
> Qq  
> WeiBo  
> BaiduLocation  
> AliPay  
> BaiduVoice  
> BaiduTts  
> SanforVpn  
> ExMobiPush  
