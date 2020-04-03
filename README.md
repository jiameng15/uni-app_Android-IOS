# uni-app_Android-IOS
使用uni-app开发移动端app过程中,遇到的问题和解决方案

当前使用的HBuilderX版本号为2.6.8

Q1:
如何改变手机顶端的状态栏颜色
A1:
记得先配置[pages.json]( https://uniapp.dcloud.io/collocation/pages?id=globalstyle ),[示例](pages.json)
改变app状态栏颜色

Q2:页面中如何使用下拉刷新

A2:

首先在[pages.json](pages.json)中对应页面中配置 enablePullDownRefresh为true

在[页面生命周期](https://uniapp.dcloud.io/frame?id=%e9%a1%b5%e9%9d%a2%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f)中使用onPullDownRefresh监听下拉

同理上拉加载可使用页面触底 backgroundColorBottom 来监听

Q3:app-plus和条件编译

A3:app-plus是写在page.json里,配置在app中实现特殊样式的配置项  

Q4:使用nvue开发和vue开发时有什区别

A4:新手一定要阅读一遍[nvue开发与vue开发的常见区别](https://uniapp.dcloud.io/use-weex?id=nvue%e5%bc%80%e5%8f%91%e4%b8%8evue%e5%bc%80%e5%8f%91%e7%9a%84%e5%b8%b8%e8%a7%81%e5%8c%ba%e5%88%ab),并多多实践,在实际应用中加深理解

Q5:使用nvue时,如height,border-radius,font-size,使用rpx单位是报错

A5:在使用nvue为模板语言时,其样式标准基于weex,只能使用px作为单位.

Q6:使用nvue时,border无效

A6:将border分解为border-width,border-style,border-color即可,代码如下

```css
/* 错误 */
.class {
    border: 1px red solid;
}

/* 正确 */
.class {
    border-width: 1px;
    border-style: solid;
    border-color: red;
}
```

Q7:使用nvue时,动态绑定class和style需要注意什么

A7:

目前nvue针对class的动态绑定及style的动态绑定,紧支持数组语法

官方原话:

>  非H5端不支持 [Vue官方文档：Class 与 Style 绑定](https://cn.vuejs.org/v2/guide/class-and-style.html) 中的 `classObject` 和 `styleObject` 语法。 

实际测试:

```vue
/* 有效 */
<text 
      class="car_info_expiretext" 
      :style="{color:item.expiresState==='过期'?'red':''}">{{item.expiresStateName}}</text>
```

Q8:使用nvue时,如何禁止页面滚动

A8:在pages.json中配置单个页面的配置项  [style](https://uniapp.dcloud.io/collocation/pages?id=style) ,中设置 disableScroll 的值.

`实际测试中disableScroll值在JSLiet中报错,但仍有效果`

需要注意的是页面中配置项会覆盖  [globalStyle](https://uniapp.dcloud.io/collocation/pages?id=globalstyle)   中相同的配置项

Q9:自定义导航栏的方法有哪些

A9:实践中有四种方法,分别为,[页面属性节点navigation-bar](https://uniapp.dcloud.io/component/navigation-bar)[uni-ui扩展组件uni-nav-bar](https://ext.dcloud.net.cn/plugin?id=52), [titleNView](https://uniapp.dcloud.io/collocation/pages?id=app-titlenview) , [subNVue](https://uniapp.dcloud.io/collocation/pages?id=app-subnvues) .

请先阅读[自定义导航栏使用注意](https://uniapp.dcloud.io/collocation/pages?id=customnav)