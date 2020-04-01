# uni-app_Android-IOS
使用uni-app开发移动端app过程中,遇到的问题和解决方案

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
