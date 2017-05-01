# 升级机制

----------

Sprite中升级包括应用资源升级和应用升级,现分别予以说明。

<h2 id="cid_0">应用资源升级</h2>

应用资源升级即本地资源包升级，升级流程由应用开发者通过js代码或封装js模板来实现,应用插件升级流程如下：

1：客户端及服务端协商应用插件升级接口，一般需要升级请求接口 和 应用插件zip包下载接口；
 
 2：客户端启动后获取本地应用资源版本号，通过[Http.ajax()](https://gitdocument.exmobi.cn/sprite-advanced/http.html#ff_0)发送升级请求接口至服务端，关于应用资源的版本号开发者可以在app.json入口文件自行配制；

 3：服务端比较应用插件版本号,若有新版本,则回应告知客户端获取，或者直接把版本号给到客户端，然后客户端做判断；
 
 4：客户端通过[Http.download()](https://gitdocument.exmobi.cn/sprite-advanced/http.html#ff_2)下载新版本应用插件升级zip包，下载到通过[File.unZip()](https://gitdocument.exmobi.cn/sprite-advanced/file.html#ff_23)本地解压或根据文件md5值差量文件更新 即可；

示例可见封装组件pluginupdate组件


<h2 id="cid_1">应用升级</h2>


应用升级即Apk或者Ipa原生安装包升级，升级流程由应用开发者通过js代码或封装js模板来实现，应用升级流程如下：

1：客户端及服务端协商应用升级接口，一般需要升级请求接口 和 应用安装包下载接口；

2：客户端启动后获取本地应用版本号,通过[Http.ajax()](https://gitdocument.exmobi.cn/sprite-advanced/http.html#ff_0)发送升级请求接口至服务端；

3：服务端比较应用版本号，若有新版本,则回应告知客户端获取；

4-1：Android客户端通过[Http.download()](https://gitdocument.exmobi.cn/sprite-advanced/http.html#ff_2)应用安装包下载接口下载最新apk包,然后调用[Native.installApk()](https://gitdocument.exmobi.cn/sprite-advanced/native.html#ff_4)进行安装；

4-2：iOS客户端若为企业服务器自部署应用,则调用[Native.browser](https://gitdocument.exmobi.cn/sprite-advanced/native.html#ff_2)("itms-services://?action=download-manifest&url=https://miap.cc:8317/commonDownload.action/cn.com.fiberhome.mobilearkdemoeleven.plist");

4-3：iOS客户端若为appstore应用,则调用[Native.browser](https://gitdocument.exmobi.cn/sprite-advanced/native.html#ff_2)("itms-apps ://itunes.apple.com/gb/app/yi-dong-cai-bian/id391945719?mt=8");
