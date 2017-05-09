# 数据模板分离MVVM模型

----------

烽火官方封装了mvvm模型框架，框架的使用说明可以参考[Agile VM移动前端框架](https://gitdocument.exmobi.cn/agile-vm/index.html)

本节组要提供示例讲解。


Agile VM移动前端框架是一个数据视图双向绑定的框架，帮助开发者将数据层和视图层分离更彻底，所以我们在开发的时候就可以实现数据和视图相分离。

请看下面示例：

在uixml页面的布局里面是关系视图层，如：

```html

<ui>
        <box class="rootBox" id="rootBox" v-on:click="rootBoxClick">
            <titlebar v-bind:title="title" licon="image/detail_topbar_icon_back.png" v-on:liconClick="doBack" />
            <line />
            <box class="headerBox">
                <box class="qdBox">
                    <textfield class="qdCode" prompt="扫描或输入签到码" returnKeyType="search" v-on:return="searchReturn" v-model="smresult" />
                    <image src="image/navibar_icon_qr.png" class="smimage" v-on:click="startdecode" />
                </box>
            </box>
            <scroll id="scroll">
                <text class="hytitle" v-text="hytitle"></text>
                <box v-if="isDisplay">
                    <textfield class="hytitle_textfile" id="hytitle" returnKeyType="next" v-on:return="textfieldReturn" v-model="hytitle" prompt="会议标题"
                    />
                </box>
                <line style="line-color:#ffffff" />
                <box class="hyqkBox" id="hyqkBox">
                    <text class="hyqk">参加人员共计</text>
                    <text class="hyqk bjrenshu">{{gj}}</text>
                    <text class="hyqk">人，已签到</text>
                    <text class="hyqk bjrenshu">{{yqd}}</text>
                    <text class="hyqk">人</text>
                </box>
                <box style="height: 20" />
                <button value="查看全部人员名单" v-on:click="searchAll2" />

                <!-- <button value="查看全部人员名单" v-on:click="searchAll" />-->

                <button value="参会人员设置" v-on:click="setrenyuan" />
                <!--   <button id="sethuiyi " v-on:click="sethuiyi" v-bind:value="sethuiyitext" />-->
                <button id="sethuiyi " v-on:click="sethuiyi" v-like="textfield" v-model="sethuiyitext" />

            </scroll>
        </box>
</ui>
```

该示例里面用到了 v-text 、v-on、v-like、v-model、v-bind，v-if 还有给文本赋值的另外种写法{{key}}

布局准备好后，我们只需要关系数据即可，只要数据变动，那么就会影响布局

那么该布局对应的js代码如下：

```javascript
var dodata = {
        "smresult": "",
        "title": "签到",
        "hytitle": "2017南京软件开发者大会",
        "isDisplay": false,
        "sethuiyitext": "会议名称设置",
        "gj": "0",
        "yqd": "0",
        doBack: function (e) {
            $.ui.closeWindow();
        },
        rootBoxClick: function (e) {
            window.hideSip();
            //这里刷新主要是为了让文字自适应
            $.ui.refreshDom('#scroll');
        },
        sethuiyi: function (e) {

            if (!dodata.isDisplay) {
                dodata.isDisplay = true;
                dodata.sethuiyitext = "保存名称设置";
                $("#hytitle")[0].setFocus();
            }
            else {
                dodata.isDisplay = false;
                dodata.sethuiyitext = "会议名称设置";
            }

            $.ui.refreshDom('#scroll');
        },
        //监听键盘的return点击
        textfieldReturn: function (e) {
            dodata.sethuiyi(e);
        },
        //监听点击扫描图片
        startdecode: function (e) {
            //启动扫描，这里传一个function过去 
            sm.startdecode(function (resultjson) {
                console.log(JSON.stringify(resultjson));
                dodata.smresult = resultjson.result.replace(/\s/g, "");
                //验证扫描结果，如果正确直接在数据库中记录
                var contentjson = mydb.smqdreq(dodata.smresult);
                opennextpage(contentjson);

            });
        },
        //监听设置会议人员点击按钮
        setrenyuan: function (e) {
            var json = {};
            json.url = "res:myapp/setting.uixml";
            json.target = "_blank";
            json.statusBarColor = "#f9f9f9";
            json.openAnimation = "push_r2l";
            json.closeAnimation = "push_l2r";
            json.statusBar = "transparent";
            window.open(json);

        },
        //监听键盘return,手动输入扫描用
        searchReturn: function (e) {
            window.hideSip();
            dodata.smresult = dodata.smresult.replace(/\s/g, "");
            var contentjson = mydb.smqdreq(dodata.smresult);
            opennextpage(contentjson);

        },
        //监听查看所有人员按钮
        searchAll: function (e) {
            var json = {};
            json.url = "res:myapp/qbmd.uixml";
            json.target = "_blank";
            json.statusBarColor = "#f9f9f9";
            json.openAnimation = "push_r2l";
            json.closeAnimation = "push_l2r";
            json.statusBar = "transparent";
            //这里传参
            json.data = {};
            json.data.gj = dodata.gj;
            json.data.yqd = dodata.yqd;
            window.open(json);

        },
        searchAll2: function (e) {
            var json = {};
            json.url = "res:myapp/qbmd2.uixml";
            json.target = "_blank";
            json.statusBarColor = "#f9f9f9";
            json.openAnimation = "push_r2l";
            json.closeAnimation = "push_l2r";
            json.statusBar = "transparent";
            //这里传参
            json.data = {};
            json.data.gj = dodata.gj;
            json.data.yqd = dodata.yqd;
            window.open(json);

        }

};

//注意改方法需要放在window的loaded事件中或者之后执行
$("#rootBox").render(dodata);
 //注入完毕如果涉及的布局变动的地方，需要刷新当前变动区域的容器
$.ui.refreshDom('#scroll');

```

在上述代码中render方法会根据数据内容，来渲染视图，并且会根据设置的属性来绑定数据，如v-model就是数据视图双向绑定。

在Agile VM框架中对Sprite中的list组件的数据绑定也进行了封装，用过list组件的同学，应该会发现list虽然强大，但是要对ListAdapter适配写很多代码，通过Agile VM框架可以大大减少我们的代码编写量。

示例如下：

list组件视图：

```html
<ui>
        <box style="flex:1" id="boxid">
            <list id="list" scrollToTop="true" style="flex:1;background-color:#ffffff;" v-on:itemClick="itemClick">
                <header style="height: 44;justify-content: center;align-items: center;">
                    <text id="headertext">正在加载...</text>
                </header>
                <cell id="cell" v-for="cell in datas">
                    <box class="cellBox" id="cellBox">
                        <text class="cellNameText" v-text="cell.username"></text>
                        <box class="cellCompanyBox">
                            <text class="cellCompanyText" v-text="cell.company"></text>
                            <text class="cellCompanyText" style="color:#50CB65;font-size:13" v-text="'签到时间：'+cell.qiandaotime"></text>
                        </box>
                        <image src="image/review_tick.png" class="cellImage" />
                    </box>
                    <line style="line-color:#909090" />
                </cell>
                <cell id="cell2" v-for="cell in datas">
                    <box class="cellBox" id="cellBox">
                        <text class="cellNameText" v-text="cell.username"></text>
                        <box class="cellCompanyBox">
                            <text class="cellCompanyText" v-text="cell.company"></text>
                        </box>
                    </box>
                    <line style="line-color:#909090" />
                </cell>
            </list>

        </box>
    </ui>
```
在cell节点中用v-for代表数据需要循环。

对应js代码关键部分如下：

```javascript
this.dodata = {
                title: "222222",
                datas: [],
                itemClick: function (e, position) {
                    // $.ui.toast(position, 0);
          }
 };
```

组装datas数据,并渲染list：

```javascript
var j = 0, k = 0;
for (i = 0; i < len; i++) {
    var cellobj = {};
    cellobj.username = arr[i].username;
    cellobj.company = arr[i].company;
    cellobj.qiandaotime = arr[i].qiandaotime;
    cellobj.type = "cell2";
    this.dodata.datas[i] = cellobj;
}


if (this.dodata.datas.length == 0) {
    this.getElement("headertext").setText("暂无数据！");
}
else {
    this.getElement("list").hideHeader();
}

var boxid = $(this.getElement("boxid"));
boxid.render(this.dodata);
$.ui.refreshDom(this.getElement("list"));
```

上述代码由于在模板里面使用，所以用到了this。

不过需要注意的是如果只是简单的列表数据展示，用Agile VM框架这种写法可以大大减少代码编写量，是个不错的选择，不过由于ListAdapter被封装了,可能做不了太复杂的操作。如果需要提高列表的展示性能，并做在ListAdapter的相关事件里面做复杂的操作，还是需要用基础的list方式来写代码。比如list进行局部刷新和局部插入用ListAdapter提供的局部刷新方法，可以大大提高列表的性能问题。

上述两个示例基本上涵盖了Agile VM框架的主要核心用法，完整示例下载：




 


