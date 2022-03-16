![调试2](images/调试2.png)

> 上篇文章我们代理已经配置好了，接下来就看下如何利用whistle调试，示例只是demo，可以结合自己的实际场景替换配置

## 资源

### 场景1 线上资源修改

比如https://goobe.io 有个index.css 通过代理我们把背景色改为skyblue

点击values-create 创建一个资源

![image-20220312173816546](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8o67i0lj22y00jktcc.jpg)

配置代理规则 访问goobe.io查看效果

![image-20220312173917951](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8o7g0ddj21ne0u07aw.jpg)



### 场景2 线上资源替换

还是这个index.css 我们把它替换为当前文档

![image-20220312174143194](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8o99knej21lb0u0ah1.jpg)



## 移动端调试

pc端调试还是比较方便的，但是微信公众号/企业微信/支付宝服务窗的h5，是在app容器内，以前针对安卓/IOS平台采用特殊的调试方法，现在使用whistle可以在不同平台，使用同一种调试方法

### whistle+vconsole

开发环境我们代码里可以开启vconsole，生产环境呢？

百度应该做了处理，不能显示vConsole了 我们换个网站玩耍

先增加个[vConsole](https://lf26-cdn-tos.bytecdntp.com/cdn/expire-1-M/vConsole/3.4.0/vconsole.min.js)资源 具体代码从静态资源库获取就行

![image-20220312173355300](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8odvvu4j22xq0kowob.jpg)



访问验证下

![image-20220312173427994](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8og7s0zj22n50u0ajd.jpg)



### whistle+weinre

仅替换资源是不能满足移动端场景的，有时我们需要调试真机中h5的样式

这里为方便演示，是用pc浏览器操作的，真机内访问一样的

![image-20220312174747608](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8oi6jwrj21fu0u0dll.jpg)

![image-20220312174837415](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8oluqj9j21920u0787.jpg)

![image-20220312174952643](https://tva1.sinaimg.cn/large/e6c9d24ely1h0a8otyuzcj22470u0ajl.jpg)