# line组件使用 

----------

line组件用于绘制直线，支持颜色，方向（横/竖），线型（实线，虚线）设置。  

<h2 id="cid_0">属性</h2> 



**公共属性**  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-begin/ggsx.html)，包括：id、style、class；



**direction**    

<code>线条绘制方向</code> 

线条绘制方向，【horizontal，vertical】 

> horizontal：横向；（默认）  
> 
> vertical：竖向； 


<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-begin/ggys.html)，包括：  
> 定位
> 
> 外边距


**line-color**  

<code>线条颜色</code>

默认值#333333； 


**line-size**  

<code>线条粗度</code>  

单位dp，默认为1dp 


**line-length**  

<code>线条长度</code>

对于横线来说，该值定义宽度，对于竖线来说，该值定义高度

注：在垂直布局中，交叉布局为stretch的时候，默认填充容器宽度。

<h2 id="cid_2">事件</h2>

无 


<h2 id="cid_3">js方法</h2>

**公共方法**  

[事件相关](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cid_0)，包括：

> [void on(messageName,function)   组件注册事件的触发函数](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#jjxg_1)   
> 
> [void fire(messageName,params)  组件事件的触发函数](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#jjxg_2)   
> 
> [void off(messageName,function)  组件移除事件的触发函数](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#jjxg_3)  
>  
> [Array getOn(messageName)  获取已绑定的事件的触发函数](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#jjxg_4)   

[动画相关](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cid_1)，包括： 
 
> [void startAnimation(jsonData,function)  启动UI组件动画](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#dhxg_1)   
> 
> [void startAnimator(jsonData,function)  启动UI组件属性动画](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#dhxg_2)   
> 
> [void startKeyFrameAnimator(jsonData,function)  启动UI组件关键帧动画](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#dhxg_3)  
>  
> [void  releaseAnimator()  结束控件动画](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#dhxg_4)   

[尺寸和位置](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cid_2)，包括：  

> [jsonData getFrame()  获取组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cchwz_1)   
> 
> [void setFrame(frame)  设置组件在父容器中的位置](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cchwz_2)   
> 
> [jsonData getCenter()  获取组件中心点在父容器中的位置](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cchwz_3)  
>
> [jsonData getAbsoluteFrame()  获取组件在绘制窗口中的位置](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cchwz_4)   


[普通Dom节点操作](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#cid_3)，包括：  

> [domObj getParent()  获取父节点](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_1)   
> 
> [domObj getNext()  获取同级下一个节点](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_2)   
> 
> [domObj getPrevious()  获取同级前一个节点](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_3)  
> 
> [void remove()  从父容器中移除自身](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_4)  
> 
 
> [void setAttr(attrName,attrValue)  设置节点属性](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_6)   
>
> [String getAttr(attrName)  获取节点属性](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_7) 
>
> [Json getAttrs()  获取节点所有属性](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_8) 
>
> [void removeAttr(attrName)  移除节点属性](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_9) 
>
> [bool hasAttr(attrName)  节点是否具有该属性](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_10) 
> 
> [void setStyle(styleName,styleValue)  设置节点样式值](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_13)  
>
> [String getStyle(styleName)  获取节点样式值](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_14)   
>
> [void clearStyle(styleName)  移除节点样式值](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_15)    
>
> [void setClassStyle(className，domobj)   设置节点对应Class样式](https://gitdocument.exmobi.cn/sprite-begin/ggff.htm#ptdom_16) 
>  
> [String getClassStyle()  获取节点已设置Class样式](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_17)  
>  
> [String getTag()  获取UI组件类型](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_18)  
>  
> [String getId()  获取UI组件Id标识](https://gitdocument.exmobi.cn/sprite-begin/ggff.html#ptdom_19) 


<h2 id="cid_4">示例</h2>  


示例代码1，测试line布局样式，参考演示应用示例：apps\yuanhongqian\spriteui\line.uixml，代码中用到了官方封装的模板titlebar，模板的使用可参考[https://gitdocument.exmobi.cn/sprite-official-ui/index.html](https://gitdocument.exmobi.cn/sprite-official-ui/index.html "https://gitdocument.exmobi.cn/sprite-official-ui/index.html") 

```html

<page>
    <script>
        <![CDATA[
        var index = 1;
        var window = require("Window");
        var document = require("Document");
        var ui = require("UI");
        require("titlebarUI");
        function alert(msg) {
            var json = {};
            json.title = "提示";
            json.content = msg;
            ui.toast(json);
        }

        window.on("loaded", function () {
            //titlebar关闭页面
            var title = document.getElement("title");
            title.on("liconClick", function (e) {
                var json = {};
                window.close(json);
            });
        });
    ]]>
    </script>
    <style>
        @import url("spriteLayout");
        @import url("spriteColor");
        .br {
            width: 100;
            height: 10;
        }
        
        text {
            singleline: false;
        }
    </style>
    <ui>
        <box class="full" id="box">
            <titlebar title="line组件" id="title" licon="res:yuanhongqian/image/icon.png" style="licon-width:24;licon-height:24" class="titlebar-hasstatus"
            />
            <scroll class="flex1">
                <box class="br" />
                <text>line-color:#dddddd;line-size:1;</text>
                <line />
                <box class="br" />
                <text>line-color:red;line-size:1;</text>
                <line style="line-color:red" />
                <box class="br" />
                <text>line-color:red;line-size:0.5;</text>
                <line style="line-color:red;line-size:0.5" />
                <box class="br" />
                <text>line-color:red;line-size:1;line-style:dashed</text>
                <line style="line-color:red;line-style:dashed" />
                <box class="br" />
                <text>line-color:blue;line-size:1;line-style:dotted</text>
                <line style="line-color:blue;line-style:dotted" />
                <box class="br" />
                <text>line-color:yellow;line-size:1;line-style:solid</text>
                <line style="line-color:yellow;line-style:solid" />
                <box class="br" />
                <text>line-color:red;line-size:10;line-style:dotted</text>
                <line style="line-color:red;line-style:dotted;line-size:10" />
                <box class="br" />
                <text>line-color:red;line-size:10;line-length:100</text>
                <line style="line-color:red;line-size:10;line-length:100" />
                <box class="br" />
                <text>line-color:red;line-size:10;line-length:100 属性direction=&quot;vertical&quot;</text>
                <line style="line-color:red;line-size:10;line-length:100" direction="vertical" />
                <box class="br" />
                <text>line-color:red;line-size:10;line-length:100;line-style:dotted 属性direction=&quot;vertical&quot;</text>
                <line style="line-color:red;line-size:10;line-length:200;line-style:dotted" direction="vertical" />
            </scroll>
        </box>
    </ui>
</page>

```

代码效果：

<img src="image/line_1.png" width="250"/>  
 


