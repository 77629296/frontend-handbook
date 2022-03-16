![调试1](images/调试1.png)

[whistle](https://wproxy.org/whistle/)是基于Node实现的跨平台web调试代理工具，类似的工具有windows平台上的`Fiddler`、mac平台上的`Charles`。针对web页用过各种调试方式，比如`Android+Chrome://inspect`、`IOS+Safari`。这些只针对特定的平台，必须连接数据线，完成同样的工作，`whistle+weinre`就够了。今天重点说下`whistle的配置`



## 安装与使用

```bash
npm install -g whistle
w2 start
```

![image-20220314071823582](https://tva1.sinaimg.cn/large/e6c9d24ely1h092upo6wmj20vm0aatbd.jpg)

访问这个链接 进入`whistle`配置页面 `http://127.0.0.1:8899/`

现在代理服务已经启动了，我们需要配置下代理，这样请求才能经过代理服务



## 配置电脑代理（mac)

`http`、`https`代理服务器配置为本地的8899端口 然后应用

![image-20220312144549276](https://tva1.sinaimg.cn/large/e6c9d24ely1h092utysx9j20vt0u0goa.jpg)

访问`https://goobe.io` 发现提示不是私密连接，这是因为针对`https`的请求需要配置证书，现在找一个`http`的网站都困难，所以证书还是需要配置的

![image-20220313232714331](https://tva1.sinaimg.cn/large/e6c9d24ely1h092v2hayyj21vy0u0n17.jpg)



### 配置证书

参考下图 点击`https` 然后下载ca

![image-20220312152410045](https://tva1.sinaimg.cn/large/e6c9d24ely1h092uw8wwqj20zx0u0q5u.jpg)

打开下载的证书，选择系统-添加

![image-20220312145521918](https://tva1.sinaimg.cn/large/e6c9d24ely1h092v6pdsaj20tq0h6dhb.jpg)

新添加的证书**默认是不受信任的**，需要**手动修改为始终信任**

![image-20220312145957356](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vayir7j21cc0ten27.jpg)

![image-20220312150031843](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vcu43ej21cs0l4tco.jpg)

再次访问 就能看到所有的资源请求了

![image-20220312150629615](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vfn6p4j21ov0u0qe6.jpg)

**如果还是显示tunnel to，点击https 记得勾选Capture TUNNEL CONNECTS 再试下**

![image-20220314090127626](https://tva1.sinaimg.cn/large/e6c9d24ely1h094tqwznkj21ax0u0n2a.jpg)



### chrome插件

填写代理服务器及端口，这个过程有点麻烦，关闭代理再打开需要重新填写，有没有什么方式能够灵活切换呢？

既然这么说了，肯定有。`Proxy SwitchyOmega` 轻松实现代理切换，搜索并从应用商店安装

![image-20220312151610249](https://tva1.sinaimg.cn/large/e6c9d24ely1h092viap0vj220g0isju6.jpg)

安装后，浏览器右上角会有个圆按钮，点击选项-新建情景模式

![image-20220312151939330](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vk62wmj21vx0u00yx.jpg)

我这里为方便区分，命名为`本地whistle`，切换到`本地whistle`，效果和之前手动配置的效果一样，如果不用了可以选择`直接连接`，是不是很方便？

![image-20220312152126288](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vo1wlhj22v60tiwpi.jpg)



## 配置手机代理

> 作为前端开发，不同型号真机的兼容是必须的，然而模拟器和真机是有差异的，这就需要用到真机调试了，前提是先配置好代理

### 代理设置

需要注意的是，因为`whistle`服务在电脑上启动，手机需要和电脑在同一局域网，换句话说就是**连接同一个无线网**

设置主机名/服务器和端口号

![proxy](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vpxexvj21410u0q5j.jpg)

### 证书

如需代理https请求，需要下载证书，设置代理后，用系统自带浏览器访问 http://rootca.pro 根据提示下载

证书安装时，安卓和ios有点区别，参考图示操作

#### 安卓

![android-ca](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vtnp39j21410u0myz.jpg)

#### IOS

![ios-ca](https://tva1.sinaimg.cn/large/e6c9d24ely1h092vv3eemj20ym0u042o.jpg)



至此，准备工作都已经做好了，接下来看看具体怎么使用吧