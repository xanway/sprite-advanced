# Sprite注意事项及开发经验

----------



<h2 id="cid_0">布局相关</h2>  

1. 在flex布局中使用flex-wrap样式时，注意，该样式一般用于水平布局，如果布局容器是垂直布局，默认每个控件必须换行，不能用这个样式，否则可能造成页面无法滚动。  

2. 一定要注意在sprite中，最外层容器一定要指定容器大小（高和宽），一般设置全屏大小即可。  

3. 在sprite页面布局中，默认是垂直方向从上往下布局，如果不设置align-items，容器内控件默认会自动填充父容器的宽度（垂直布局填充宽度，水平布局填充高度）。如果设置了align-items除stretch外的其他值，容器内控件的大小将会取决于该控件内容的大小，注意这种情况下line、image、list等一些控件必须给出高和宽（不确定高宽的可以用flex:n来设置区域大小）。  

4. 只有容器自身大小确定后（一般情况下横向要指定宽度，纵向要指定高度），在容器内部才能使用flex:n进行区域分割。  

5. Sprite中的布局是有层的概念，虽然没有css3那种index-z样式来控制在Z轴层的位置，但是其默认是按照布局来来分层次，在布局方向上，最下面的控件在Z轴上就是最上层，如果有绝对定位控件，建议放在布局容器的最后面。  

6. 如果容器自身是绝对定位控件，那么其自身就不参与父容器的区域分割了，也就是说设置flex:n无效。  

7. 当控件为布局为绝对定位时，其位置相对于父容器的绝对位置。  

8. 布局为绝对定位时，如果没有直接给出width和height，其容器大小需要通过设定top、left、right和bottom来限制大小。  

9.  opacity设置的是整个控件的透明，如果控件是容器，那么容器内部所有的控件都会跟着一起变透明。如果想实现背景色透明，可以使用background-color:rgba(255, 0, 0, 0.5)来设置。  

10.  如果想设置文字为省略样式，首先必须固定文本区域大小，并制定文字固定的行数，如text样式singleline：true，并且text宽度应该小于等于父容器的宽度。  

11. 使用display样式显隐控件后，需要调用document.refresh()刷新布局，如果容器区域大小确定，可以对容器内部刷新 xxxdom.refresh()；  

12.  在使用显隐控制时，如果不涉及整个页面布局变动，建议用visibility来做显隐，这样就不要刷新布局，提高显隐效率。那么什么情况下是布局变动呢，比如隐藏一个控件后，这个控件下面的控件都会往上移动，这种情况下需要使用document.refresh()刷新页面布局。  

13.    getFrame()方法获取的是组件布局完毕后在父容器中的实际位置，与样式中的width和height是有区别的，比如style样式里面设置的是flex:1，该组件布局完成后就会有个实际的width、height、x和y值，但是样式是没有设置width和height样式属性的，所以只能通过v.getFrame().width来得到宽度，不能通过v.getStyle("width");得到宽度，如果没有定义width样式v.getStyle("width")会得到一个null值。  

14. 使用setFrame()方法设置控件的布局，是不需要进行document.refresh()刷新的，布局直接生效，建议用拖动控件动画的操作时，通过该方法进行页面控件拖动操作。  

15. 使用setFrame()方法设置frame， width，height设置至组件css样式中，x、y不会修改样式中的left和top属性，所以设置frame后，如果执行了document.refresh()，x和y就会还原，如果不希望还原可以在通过setStyle()手动设置对应样式left和top。  

16. 如果控件是相对定位布局，其top和left样式的值都是相对于其前一个控件的相对位置，如果自身在容器里面就是第一个控件那么top和left就相对父容器位置 ，一般情况下都是0。  

17. 如果控件是绝对定位布局，那么top和left就是相对父容器的位置。  

18. getAbsoluteFrame()用来获取组件在整个绘制窗口中的绝对位置，一般指手机的屏幕位置，如果内部组件通过js动态加载进行布局，在android上可能不能马上获取到该组件的getAbsoluteFrame的值，需要做一个定时处理来获取。  

19. 如果在页面加载的时候获取某一个组件的getAbsoluteFrame的值，在android上 在window的loaded事件里面可能获取不到，需要放在window的animator事件里面获取。  

20. remove()该方法可以移除控件自身，不过控件对象并没有销毁，只是该控件的view被移除，比如移除后，可以继续使用appendChild(domObj:IElement): void这类方法，把该控件的view添加到其他容器中。  

21.  setAttr()用于设置节点的属性，不一定是组件本就具备的属性，也可以是自定义的属性名称和属性值，方便开发者通过属性绑定一些数据。  

22. setStyle()用于修改样式，如果有修改布局的样式，需要对布局进行刷新方可生效，一般影响布局的样式有width、height，flex等，如果只是修改颜色，不需要刷新。  

23. 每个控件都有自己的refresh()刷新方法，建议控件内部刷新，都使用局部刷新，但是要保证控件自身区域大小固定，该刷新只会影响控件内部，外部布局不会变动。注意，局部刷新只刷控件内部，不刷新控件自身。  

24. 尽可能少用全局刷新document.refresh(), 该刷新在android上会有效率问题。除非发生页面整体布局变动。  

25. setClassStyle该法设置class后，以前的通过class设置的样式会全部清除，不过style设置的不会清除。  

26. 由于style的优先级要高于class，如果class设置的样式里面，包含之前style设置的样式，还是以style中的样式为优先。  

27. 在通过getStyle获取color的时候，（如：#ff0000），在android上由于css引擎的差异性，通过getStyle("color")获取的颜色值是rgb(255,0,0)这种形式，通过js设置的颜色值则没有影响。  

28. appendChild()用于向容器中添加节点对象，执行该方法，需要刷新容器布局方可生效。  

29. 通过appendChild()向容器添加节点的时候，如果该容器正在监听touch系列事件，会造成事件中断，比如正在监听一个容器的touchMove拖动事件，在拖动的过程中，向该容器内部添加节点，会照成touchMove事件中断。  

30. box的background-image只支持本地图片，如果想支持网络图片或者.9图片，可以使用image控件，然后在box内部进行绝对定位布局。  

31.  text的maxlines属性设置后，会空出最大行数的位置。  

32.  image图片组件支持加载点九图,固定采用拉伸模式，图片以 .9.png为后缀，如border.9.png，Android系统支持直接加载点九图，iOS系统需要通过point9area设置点九图四边不拉伸区域范围。  

33.  image控件必须指定高和宽后才能显示，如果想动态算出image的高宽进行布局，可以监听loaded事件，该事件会返回图片的高和宽，然后在动态修改image的style，如果页面内部有多张图片，可以利用事件冒泡机制，可在外层容器上监听loaded事件。  

34.  使用scroll时需要设置其区域大小，一般情形下要设置高宽，也可以用flex来分割区域，如果不设置区域大小，其内容无非显示。  

35. refresh虽然为独立控件，但是在list控件内部，属于list内部子控件，对于子控件，是不能单独封装成模板组件的，如果要封装，也只能封装refresh内部的布局控件。  

36. 如果scroll和list内部数据动态加载，如果想在加载完成后马上自动滚动到某一区域，这需要通过定时器延迟下，在执行滚动操作，因为刷新布局会消耗时间，如果刷新后立即执行滚动在android上可能没有效果。  

37. refresh的reset()复位方法一定要延迟执行才有效果，因为里面有一个刷新动画，一般情况下都是发起网络请求后才执行reset()方法，自然不用关心，如果做演示数据，需要人为的加一下定时器。  

38. 使用list时需要设置其区域大小，一般情形下要设置高宽，也可以用flex来分割区域，如果不设置区域大小，其内容无非显示。  

39. 在list的cell内部不能做有关dom的容器操作，比如动态的添加一个dom或者隐藏一个dom（不过可以使用visibility来做控件的隐藏），总之在cell内部不允许有修改区域大小的操作。    

40. ListAdapter适配器是专门用于list控件的数据绑定的，其内部会做数据缓存处理可以支持超大数据量的列表数据，建议大数量列表用list来完成。  

41. 在使用 ListAdapter的时候， 如果使用notifyItemRangexxxx系列的局部刷新（删除，修改，添加），要保证数据源对应进行删除，修改，添加操作，否则会出错。  

42. 使用grid时需要设置其宽度，也可以用flex来分割区域，如果不设置宽度，其内容无法显示。  

43. iconfont文字图组件用于文字图展示，支持通过css样式font-family设置需要加载字体库后使用，格式为\uxxxx，如：\ue674 。如果在js里面写，需要写\\\\ue674。  

44. 在使用webview的时候，需要注意，uixml相对html来说是窗口的概念，html页面内部跳转都将在窗口内部跳转，如果窗口关闭则整个html页面全部关闭。  

45. handsign手写签名组件不要在可滑动的容器中使用该控件，比如scroll，slider等。  

46. 所有的dom相关操作必须放在window的loaded事件之后才能执行。    

47.  list中cell里面的dom对象比较特殊，运行时手机只会加载一屏幕的数据在内存中，只能在ListAdapter中的getView中获取。尽量不要有dom布局改动的操作。最好使用visibility来做显隐，或者定义多个不同的cell用来显示不同布局的列表内容。如果避免不了有dom的修改，修改后必须使用adapter的notifyItemRangeChanged方法刷新当前局部的列表数据。

48.  在sprite基础控件布局中，除了box，text，scroll，grid 这几个控件在不设置高宽的时候能被内部控件撑开（text的高宽会自动根据文字大小撑开），其余的基础控件都必须设置规定高宽才能显示。

49.  在sprite中，slider和list两个控件比较特殊（list靠adepter进行刷新），两个控件都有自己的refresh()，其内部布局变化必须使用自己的刷新才能改变内部布局，外层document.refrehs()，不会影响到这两个控件的内部刷新。

50.  grid控件比较特殊，该控件一般不需要指定高度（纵向布局的时候要指定宽度），控件高度会根据内部网格的高宽比例进行调节。如果grid里面的内容动态加载，需要刷新dom才可以生效。

51.  使用slider的时候一定要指定高度和宽度。

52. flex:n 这样的用法，只能用其父容器区域大小固定的容器中。




<h2  id="cid_1">事件相关</h2>

1.  在Sprite平台中，所有事件均具备向上冒泡机制，所以我们有时候可以利用改机制监听最外层容器，然后通过even对象的target来判断内部是那个组件触发了该事件。

2.  当某个控件同时有click和touchMove事件时，当touchMove事件触发后，click事件就会失效，这个特点可以用来做那种点上去如果反悔了可以移动手指让点击事件失效的效果。

3. 在使用off移除函数的时候，若不指定移除函数，则移除组件所有注册 "事件名" 的触发函数；

4. getOn用来获取已经注册的事件，若消息事件未绑定触发函数则返回空数组

5. 当快速点击时事件的执行顺序为touchDown->touchUp->click

6. 当长按时事件的执行顺序为touchDown->longTouch->touchUp

7. 当按住并移动时事件的执行顺序为touchDown->touchMove->touchUp (touchCancel)

8. 当长按并移动时事件的执行顺序为touchDown->longTouch->touchMove->touchUp (touchCancel)

9. android在执行touchDown后基本上会马上执行touchMove（对移动事件监听比较灵敏）。

10. 只要有按下去的动作touchDown一定会触发，一般用于做UI组件点击下去的效果。

11. 对应android，只要touchDown触发，基本上touchMove也会触发。

13.  当长时间移动触发touchMove后，就不会触发click事件了。

14. 如果box在滚动容器里，当容器滚动的时候就不会触发该box的touchUp了，这时会触发touchCancel事件。

15. 如果要做组件点击抬起的效果，建议在touchUp和touchCancel里面都执行抬起的效果代码。

16. slider的pageSelected 事件在页面animator完成的时候进行监听，如果slider控件是动态加载的，该事件会在执行sliderdom.refresh()后自动监听一次。

17. App应用信息操作类是应用级的，如果在某个页面使用App做事件监听，只要这个页面没有被关闭，就会影响整个应用，所以开发者在使用这个App类的时候，如果只希望当前页面受到事件监听的影响，可以通过window类来isTop()方法判断当前页面窗口是否是置顶窗口。 比如我们监听back返回键时，事件里面做了当前窗口关闭，如果不做判断，那么所有页面只要是监听了返回事件的都会触发，所有页面就全部关闭了。



<h2  id="cid_2">动画相关</h2>

1.  startAnimation动画方法中 pivotX，pivotY 设置的是位置比例，比如pivotX=0;pivotY=0 表示的控件左上角顶点位置；pivotX=0;pivotY=0.5 表示控件左侧Y轴中间位置；pivotX=0.5;pivotY=0.5标示控件中心点位置（默认就是该位置）；  

2.  startAnimation方法仅做动画效果，并不涉及UI组件真实属性变化，如果不设置fillAfter=1，那么该方法做完动画后，直接还原。  

3. startAnimator动画方法中，animators组数中动画会按照数组顺序依次执行， 如果需要组合动画同时执行，都设置在props里面即可。  

4. startAnimator方法调用会引起UI组件真实属性变化，不过如果动画结束后调用releaseAnimator()方法释放动画，并执行document.refresh()，位移动画会全部还原。 如果希望后续有document.refresh()操作继续刷新组件，有不希望组件动画还原，可以在动画结束的回调函数里面通过setStyle方式，修改其style真实样式，这样控件就永远固定在动画结束位置了。  

5. 属性动画开始后，组件会受到动画的保护，如果在没有releaseAnimator()释放动画前，组件是不会被document.refresh()刷新的。  

6. startAnimator动画方法的translationX和translationY是相对于控件原始位置的相对位移距离，比如控件在Y轴上向下移动80距离，那么设置translationY=80，如果不释放动画，这个时候在移动之前的位置，需要设置translationY=0，而不是-80。  

7. startKeyFrameAnimator帧动画本质上也是属性动画，其值修改后，组件真实属性也会变化，与属性动画不同的时，可以自己控制，在某个时间段上的动画效果的值。  

8. startKeyFrameAnimator帧动画执行后需要调用releaseAnimator()方法释放动画，效果和属性动画一样。  

9. 组件UI动画可以设置组件从一个状态到另外一个状态的动画效果，使用时建议先把控件位置固定在动画结束的位置，然后在从冒个位置移到自身原本位置即可。可以先刷新控件dom，位置变动后马上执行ui动画。

10. 做属性动画的带有缩放效果的时候，如果想把一个控件从一个状态变成另外一种状态，需要先通过动画把它设置成初始状态，然后在做还原动画即可。比如一个按钮从小变大到正常状态，要先通过属性动画变现小，然后在还原。如果一开始不想看到变小的效果，可以在控件hidden的时候，就开始做动画。


<h2  id="cid_3">组件模板开发相关</h2>

1. 在模板组件封装中，Iid,style,class 这个3个属性是不会自动压在封装组件内部的。

2. 由于默认情况下组件名和组件文件名一致，所以同一个应用中尽量保证模板组件名必须唯一，而且路径也必须唯一，比如buttom.component模板文件，对应的组件标签是button，那么在整个应用中就最好只有一个button组件的文件，如果有其他相同组件最好另起名字比如buttonFH。

3. 在模板内部构建模板布局的时候不能在created方法里面执行document.refresh()布局刷新操作，如非要执行可以使用定时，因为模板构建的时候整个界面都在布局中，如果执行了document.refresh() 可能会影响其他控件布局展示。

4. 在模板内部使用相对路径时，其路径是基于模板文件的相对路径。这样有利于模板资源的封装。

5. 在模板内部动态创建标签时如果想受到模板内部样式的影响 在创建控件的方法里面需要添加第二个参数this。

6. 模板外部的样式都会自动压入模板内部的第一个布局标签上面，比如button组件的样式会自动作用到button.component里面的最外层的box上，属性不压入模板内部第一个标签。

7. 模板内部最外层布局标签在view层上等同于外部组件本身，但是属于不同的dom对象，如果在模板内部对外层布局标签做事件监听操作，同时外部组件有同样的事件，都会监听到。

8. 模板和外部uixml属于同一个js环境，如果在uixml里面传入一个变量到模板内部，在模板内部修改后，外部变量也会受到影响。

9. 模板和模板之间可以嵌套使用，比如在一个模板里面引入了另外一个模板。

10. 模板内部组件相对外部uixml是封闭的，如果想在uixml里面得到模板内部控件或者某个对象，需要模板开发者暴露方法。

11. 在封装模板组件的时候定义方法和事件的时候，避免使用sprite已有的方法和事件名称，比如refresh方法，sprite平台已经有这个方法，如果自己定义成相同的方法名，可能会引起冲突。

12. 由于模板使用基础控件进行封装，除自定义属性、样式、方法、事件外，模板组件具备基础组件的所有属性、样式、方法和事件。如模板组件最外层用box封装，那么模板组件本身就具备box的所有属性、样式、方法和事件。只不过模板组件封装后有特定的使用场景，有些属性、样式、方法和事件可能不太适合直接用，开发者需要在组件文档中做特殊说明。

13. Sprite组件机制中，css样式有2层，一层是外部组件的css样式，另外一层是组件内部根节点的css样式，由于模板组件具有封装的特点，所以外层样式的优先级高于内部根节点的样式。

14. 组件虽然可以帮助我们解决代码重复问题，但是不建议在一个页面里面大量使用，尽量保证一个页面里面不要超过20个封装的组件，否则在android上页面打开会有效率问题。比如在页面里面放30个button组件（在list控件里面无所谓），页面打开可能就会比较慢。简单的场景下需要重复使用某一个布局时，尽量用box进行布局，如果实在不行，可以考虑动态布局，需要用的时候在加载，不要一次性都写在页面里面。

15. 在组件的created方法里面，是不能获取组件的frame布局样式的，因为这个时候页面还没有完成布局。


16. 当组件里面使用image的setFrameAnimation(jsonData:Object)方法时，android不能放在created里面执行，需要在created以后执行，所以建议android和ios 都放在created之后执行。

17.  当模板组件外层有样式和属性的时候，模板组件会在created方法之后自动调用styleChange和attrChange，不过需要注意的是模板属性和样式的调用先后顺序不能控制，如果需要控制，需要自己在created方法里面排列好调用顺序。

<h2  id="cid_3">开发调试相关</h2>

1. 在mbuilder中保存代码，会自动同步，下次重新打开该页面即可生效，如果是修改模板组件代码，android客户端需要退出程序重新进入模板组件才会生效，因为android的模板是在程序启动的时候预加载的。ios客户端正常重新进入页面即可。

2. 如果在布局开发的时候，发现有些控件不出来，可以尝试用打日志的方式，把控件对象打印出来，如：console.log(document.getElement("objid")), 会在控制台“输出”里面输出该dom的布局参数，我们只需关系frame的参数是否正确即可，比如width和heigth如果都是0，控件就不会显示。

3. 由于控件默认背景都是透明色，如果想看一下这个控件所占据的区域，可以给控件加上背景色进行调试。

4. sprite中有很多方法都是带回调方法的，回调都是异步执行的，所以在用回调方法的时候，后续方法需要放在回调里面执行，否则回调还没有结束，可能有些值是取不到的。

5. 建议开发过程中，js和css还有模板，都全部放在程序入口的requrie.json里面进行配置，这样程序会在启动的时候预先加载这些文件路径，这样可以提高程序内部页面打开的速度，在android上特别明显。

6. 为了有良好的代码提示，建议js和css都单独放在js和css文件中。

7. mbuilder在同步代码到手机端的时候，同步的是out目录下的代码，如果发现代码不生效，需要注意检查下out目录的代码是否正常。

8. 由于android端，requrie.json文件里面配置的路径，会在程序启动的时候预加载，所以一旦配置了这些文件路径，在修改后，android端必须退出应用重新进入，为了方便开发调试，可以在页面编写开始阶段，先把js,css直接写在uixml页面，后续调试完成后，在把代码分别放入对应的独立文件。

9. 和第8项类似，android中的模板也是在应用启动的时候预加载的，如果修改了模板文件，应用必须退出后重新进入才可以生效，ios不需要这样做。

10.  当有耗时逻辑需要执行的时候，可以考虑使用定时器延时执行，让界面先显示出来。

11.  当一个dom是动态加载的时候，加载完是需要刷新dom的，如果这个时候立即执行刚加载的dom的动画，可能动画没有效果，需要用定时器延迟一下，在执行动画。（注，这个不是所有手机都这样，主要看手机性能）

12.  list中的cell在list里面是复用的，在给cell里面的控件赋值的时候，一定要保证正确情况和错误情况都有值，比如里面有个image控件，在给src赋值的时候，如果图片地址存在就赋值一个正确的图片路径，如果图片不存在，也需要赋值一个图片路径来标示图片加载异常。

13.  android中在style样式标签里面如果引用方式和直接写样式混合使用，引用外部样式路径的方式必须写在最前面

14. 在做手势动画的时候，如果遇到比较复杂的缩放位移效果，可以用动画来实现，动画时间可以设置成0.1毫秒，然后通过动画来计算位置。







 


