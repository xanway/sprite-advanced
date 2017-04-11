# textfield组件使用 

----------

textfield文本输入组件允许用户通过键盘输入文本的基本组件，单行输入，支持普通输入模式及密码输入模式。  


<h2 id="cid_0">属性</h2> 

本节目录：  

> [公共属性](#sx_1)
> 
>[ name  控件名称](#sx_2)
> 
>[ type  输入类型](#sx_3)
>  
> [keyboardType  弹出输入法键盘类型](#sx_4)
>   
> [capitalize  是否要自动将特定字符切换为大写](#sx_5)
>   
> [autoCorrect  是否进行拼写纠错](#sx_6)
>   
> [prompt  提示语](#sx_7)
>   
> [value  文本内容](#sx_8)
>   
> [maxLength  输入字符的最大长度](#sx_9)
>   
> [returnKeyType   设置弹出输入法return键显示样式](#sx_10)
>   
> [disabled  是否禁用该控件](#sx_11)
>   
>[ clearButtonMode  文本框右侧“清除”按钮显示模式 ](#sx_12) 



<span id="sx_1">**公共属性**</span>  

[参见公共属性章节](https://gitdocument.exmobi.cn/sprite-begin/ggsx.html)，包括：id、style、class；



<span id="sx_2">**name**</span>    

<code>控件名</code>  

用于表单提交，字符串类型
 
 

<span id="sx_3">**type**</span>  

<code>输入类型</code>   

字符串枚举型，【text，password】

> text：普通文本输入框；（默认） 
> 
> password：密码输入框；



<span id="sx_4">**keyboardType**</span>  

<code>弹出输入法键盘类型</code>    

字符串枚举型，【default，number, phone ,decimal,phone,email,url】  

> default：默认输入法键盘；（默认）
> 
> number：数字输入法键盘；
> 
> decimal：带小数点的浮点数字输入法键盘；
> 
> phone：电话输入法键盘；
> 
> email：电子邮件输入法键盘；
> 
> url：url输入法键盘；


<span id="sx_5">**capitalize**</span>  

<code>是否要自动将特定字符切换为大写</code>    

字符串枚举型，【none ,characters，words, sentences】 

> none：不自动切换；（默认）
> 
> words：单词首字母大写；
> 
> sentences：句子的首字母大写；
> 
> characters：所有字母都大写；


<span id="sx_6">**autoCorrect**</span>  

<code>是否进行拼写纠错</code>     

bool型，【true，false】  

> true：启用拼写纠正；
> 
> false：不启用拼写纠正；(默认)  


<span id="sx_7">**prompt**</span>  

<code>提示语</code>   

字符串类型，用户没有输入任何内容时，显示的字符串，用户点击输入时，自动置空。  


<span id="sx_8">**value**</span>  

<code>默认文本内容</code>    

字符串类型


<span id="sx_9">**maxLength**</span>  

<code>输入字符的最大长度</code>    

数字类型


<span id="sx_10">**returnKeyType**</span>  

<code>设置弹出输入法return键显示样式</code>    

return键显示样式，取值为【default，go，search，next，send】
  
> default：换行；（默认）
> 
> go：前往；
> 
> search：搜索；
> 
> next：下一项；
> 
> send： 发送

  
<span id="sx_11">**disabled**</span>  

<code>是否禁用该控件</code>     

是否禁用该控件，不可编辑【true，false】  

> true：控件为禁用状态；
> 
> fasle：控件为普通状态；（默认）



<span id="sx_12">**clearButtonMode**</span>  

<code>文本框右侧“清除”按钮显示模式</code>   

取值【never，whileEditing，unlessEditing，always】

> never：从不出现；（默认）
> 
> whileEditing：编辑状态时出现；
> 
> unlessEditing：除了编辑状态外都出现；
> 
> always：一直出现；

**注：** 仅iOS系统支持


<h2 id="cid_1">样式</h2>

**公共样式**  

[参见公共样式章节](https://gitdocument.exmobi.cn/sprite-begin/ggys.html)，包括：  
 
> 尺寸
> 
> 定位 
> 
> 内边距：padding:12 8 12 18
> 
> 外边距：border-radius默认为4
> 
> 背景
>
>文本样式 
> 
> flexbox布局：align-self，flex


**prompt-color**  

<code>提示文字颜色</code>

默认值：#aaaaaa
  


**border-color-focus**  

<code>编辑框激活状态下border边框色</code>  

默认值：#aaaaaa



<h2 id="cid_2">事件</h2>


**focus**  

<code>获取焦点，进入编辑状态时触发</code>    

进入编辑状态时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：focus；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型



**blur**  

<code>失去焦点，退出编辑状态时触发</code>    

退出编辑状态时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：blur；  
> 
> target：触发事件的目标组件，dom对象；  
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型


**textChanged**

<code>文本框激活状态下，输入值改变时触发</code>   

文本框激活状态下，输入值改变时触发，event事件对象包括：  

> type：事件类型，字符串类型，固定值：blur；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

value：改变后的输入值，字符串类型



**return**  

<code>点击输入法return键时触发</code>

vent事件对象包括：  

> type：事件类型，字符串类型，固定值：blur；
> 
> target：触发事件的目标组件，dom对象；
> 
> timestamp：事件触发的时间戳,单位毫秒，数字类型

returnKeyType：弹出输入法return键显示样式，取值为【default，go，search，next，send】


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


**void setFocus()**  

<code>设置当前编辑框获取焦点</code>  

参数：无   

返回：无


**bool isFocus()**  

<code>当前编辑框是否获取焦点</code>    

参数：无  

返回值：是否获取焦点，bool型  

> true：编辑框已获取焦点
> 
> false：编辑框未获取焦点



**void clear()**  

<code>清空输入框内容</code>    

参数：无  

返回值：无  




<h2 id="cid_4">示例</h2>  

示例代码，测试textfiled布局样式和功能，参考演示应用示例：apps\yuanhongqian\spriteui\textfield.uixml，代码中用到了官方封装的模板组件titlebar和button，模板的使用可参考[https://gitdocument.exmobi.cn/sprite-official-ui/index.html](https://gitdocument.exmobi.cn/sprite-official-ui/index.html "https://gitdocument.exmobi.cn/sprite-official-ui/index.html") 

```html

<page>
    <script>
        <![CDATA[

        var window = require("Window");
        var document = require("Document");
        var Time = require("Time");
        var ui = require("UI");
        require("titlebarUI");
        require("buttonUI");
        var console = require("Console");

        window.on("loaded", function () {
            var scroll = document.getElement("scroll");
            var rootBox = document.getElement("rootBox");
            rootBox.on("click", function (e, json) {
                window.hideSip();
            });

            var title = document.getElement("title");
            title.on("liconClick", function (e) {
                closePage();
            });


            var scroll = document.getElement("scroll");
            scroll.on("scrollToBottom", function (e) {
                //alert("滚动到底了");

            });
            var result = document.getElement("result");
            var fireEventTest = document.getElement("fireEventTest"); fireEventTest.on("textChanged", function (e, text) {
                result.setAttr("value", text);

            }); fireEventTest.on("focus", function (e) {
                console.log("text focus");

            }); fireEventTest.on("blur", function (e) {
                console.log("text blur");

            }); fireEventTest.on("return", function (e) {
                console.log("text return");

            });

            var btnClick = document.getElement("btnClick"); btnClick.on("click", function (e) {
                fireEventTest.setFocus();

            });
            var btnClick1 = document.getElement("btnClick1"); btnClick1.on("click", function (e) {
                fireEventTest.clear();

            });
        });

        function alert(msg) {
            var json = {};
            json.title = "提示";
            json.content = msg;
            json.buttonText = "确定";
            ui.alert(json);
        }

        function closePage() {
            var json = {};
            json.data = {};
            json.data.text = "页面关闭";
            json.animation = "slide_b2t";
            window.close(json);
        }
    ]]>
    </script>
    <style>
        @import url("spriteLayout");
        @import url("spriteColor");
        image {
            width: 100;
            height: 100;
            margin: 5 5 5 5;
        }
        
        button {
            width: 120;
            height: 50;
            margin: 5 5 5 5;
            color: #ffffff;
            background-color: #88D038;
            background-click-color: #669D2A;
        }
        
        text {
            color: red;
        }
        
        textfield {
            background-color: #AAAAAA;
        }
        
        .box {
            background-color: #A52A2A;
            width: fill_screen;
            height: 50;
        }
    </style>
    <ui>
        <box class="full" id="rootBox">
            <titlebar title="textfield组件" id="title" licon="res:yuanhongqian/image/icon.png" style="licon-width:24;licon-height:24" class="titlebar-hasstatus"
            />
            <scroll id="scroll" style="width:fill_screen;flex:1;background-color:#00F0FF">
                <box>
                    <textfield value="我是输入框" />
                    <text>颜色测试background-color:green;prompt-color:blue;color:red</text>
                    <textfield style="background-color:green;prompt-color:blue;color:red" prompt="请输入文字" />
                    <text>prompt</text>
                    <textfield prompt="请输入文字" />
                    <text>type:password</text>
                    <textfield type="password" value="123" />
                    <text>returnKeyType</text>
                    <textfield returnKeyType="search" />
                    <text>keyboardType:number</text>
                    <textfield keyboardType="number" />
                    <text>keyboardType:email</text>
                    <textfield keyboardType="email" />
                    <text>capitalize:characters</text>
                    <textfield capitalize="characters" />
                    <text>autoCorrect:true</text>
                    <textfield autoCorrect="true" />
                    <text>maxLength:5</text>
                    <textfield maxLength="5" />
                    <text>clearButtonMode:always</text>
                    <textfield clearButtonMode="always" value="555" />
                    <text>border-color:green;border-width:5;border-radius:20;border-color-focus:red</text>
                    <textfield style="border-color:green;border-width:5;border-radius:20;border-color-focus:red" />
                    <text>text-align:right</text>
                    <textfield style="text-align:right" value="123" />
                    <text>font-size:30dp;font-style:italic;font-weight:bold</text>
                    <textfield style="font-size:30dp;font-style:italic;font-weight:bold" />
                    <text>fireEventTest</text>
                    <textfield id="fireEventTest" />
                    <text>输出结果</text>
                    <textfield id="result" />
                    <button value="点击事件" id="btnClick" />
                    <button value="清空输入" id="btnClick1" />
                    <text style="margin:300 0 0 0">弹出框移动测试,移动scroll坐标，覆盖title</text>
                    <textfield returnKeyType="search" id="scrollSetFrame" />
                    <text>弹出框移动测试,移动scrol contentoffset,不覆盖title</text>
                    <textfield returnKeyType="search" id="scrollContextOffset" />
                </box>
            </scroll>
            <text class="box">测试占位2</text>
        </box>
    </ui>
</page>

```

代码效果：

<img src="image/textfield_1.png" width="250"/>  <img src="image/textfield_2.png" width="250"/>  
 


