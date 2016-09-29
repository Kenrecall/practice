###屏幕尺寸
####window.screen.width/height
- 含义: 用户屏幕总大小
- 度量: 设备像素
- 兼容性: IE7/IE8以CSS像素来度量

`window.screen.width/height`返回的是屏幕的宽高,它们的值并不会因为浏览器的缩放而改变.它们是显示器的特性,而不是浏览器.

![desktop_screen](viewportimg/desktop_screen.jpg)

按照道理应该这样,但各大浏览器并没有好好的实现这一规则.chrome浏览器(版本号53.0.2785.116),不论浏览器是否缩放,返回的都是不变的屏幕宽高;Firefox(版本号47.0.1)在缩放80%的时候,才正常返回屏幕宽高;IE和Edge都是在缩放100%的时候,才能正常返回屏幕宽高

####参考
- [https://developer.mozilla.org/zh-CN/docs/Web/API/Screen/width](https://developer.mozilla.org/zh-CN/docs/Web/API/Screen/width)

- [http://www.w3cplus.com/css/viewports.html](http://www.w3cplus.com/css/viewports.html)

- [http://www.quirksmode.org/mobile/viewports.html](http://www.quirksmode.org/mobile/viewports.html)

###浏览器内部尺寸
####window.innerWidth/Height
- 浏览器视口(viewport),如果存在滚动条则包括滚动条
- 度量: 单位：像素
- 兼容性: 如下图

![兼容性](viewportimg/inner-size-basic-support.jpg)

返回值为浏览器窗口大小.支持此事件的浏览器受缩放影响

![desktop_inner](viewportimg/desktop_inner.jpg)

![desktop_inner_zoomed](viewportimg/desktop_inner_zoomed.jpg)

####参考
- [https://developer.mozilla.org/zh-CN/docs/Web/API/Window/innerWidth](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/innerWidth)

- [http://www.w3cplus.com/css/viewports.html](http://www.w3cplus.com/css/viewports.html)

- [http://www.quirksmode.org/mobile/viewports.html](http://www.quirksmode.org/mobile/viewports.html)

###浏览器外部尺寸
####window.outerWidth/Height
- 整个浏览器的宽高(包括了浏览器的工具条等)
- 度量: 单位：像素
- 兼容性: 如下图

![兼容性](viewportimg/outer-size-basic-support.jpg)

Window.outerWidth/Height获取浏览器窗口外部的宽高.表示整个浏览器窗口的宽高,包括侧边栏(如果存在)/窗口镶边(window chrome)和调正窗口大小的边框

![desktop_outer](viewportimg/desktop_outer.png)

####参考
- [https://developer.mozilla.org/zh-CN/docs/Web/API/Window/outerWidth](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/outerWidth)

###浏览器可用最大尺寸
###window.availWidth/Height
- 浏览器能占据屏幕的最大宽高
- 度量: 单位：像素

返回浏览器窗口在屏幕上可占用的最大横宽或竖宽空间，即最大宽高度

![desktop_avail1](viewportimg/desktop_avail1.png)

![desktop_avail2](viewportimg/desktop_avail2.png)

####参考
- [https://developer.mozilla.org/zh-CN/docs/Web/API/Screen/availHeight](https://developer.mozilla.org/zh-CN/docs/Web/API/Screen/availHeight)

###滚动移位
####window.pageX/YOffset == window.scrollX/Y
- 页面的移位(滚动条的移位)
- 度量: 单位：像素
- 兼容性: 为了兼容性更好,建议使用window.pageX/YOffset IE8及以下两个属性都不支持
    - 兼容方式
    
        ```
        var x = (window.pageXOffset !== undefined) ? window.pageXOffset : (document.documentElement || document.body.parentNode || document.body).scrollLeft;
        ```

        ```
        var y = (window.pageYOffset !== undefined) ? window.pageYOffset : (document.documentElement || document.body.parentNode || document.body).scrollTop;
        ```

这两对方法定义了页面(document)的相对于窗口原点的水平/垂直位移.因此能够定位用户滚动了多少的滚动条距离.

![desktop_page.jpg](viewportimg/desktop_page.jpg)

####参考
- [https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollX](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollX)

- [http://www.w3cplus.com/css/viewports.html](http://www.w3cplus.com/css/viewports.html)

- [http://www.quirksmode.org/mobile/viewports.html](http://www.quirksmode.org/mobile/viewports.html)


