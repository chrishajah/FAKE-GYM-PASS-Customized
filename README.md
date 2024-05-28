# FAKE GYM PASS

**本项目仅供学习交流，严禁用于造假及非法用途。**

本项目是仿照中山大学体育场馆管理与预订系统制作的一套前端页面，实现了自定义调整预定人信息以及最新一条体育场馆预定订单的内容

有什么想要改进的地方欢迎在issue中提出

## 部署教程

*熟悉web服务器部署的同学可以跳过，项目是开箱即用的。

本项目的部署方式有两种：

1.   部署在个人笔记本电脑上，项目的作用范围仅限于局域网内，门槛较低，在之后会介绍如何部署
2.   部署在服务器上，只要能够连接服务器的地方都可以使用，以校内的网络环境可以部署在学校实验室**连接有线网络**的服务器电脑上，这样只要连接到无线校园网的移动设备都可以访问。（如果是windows服务器的话，应该也适用1中的部署方法）

### 个人笔记本电脑部署

由于本人只有windows电脑，因此使用mac电脑的同学请自行搜索如何搭建web服务器的教程

个人笔记本电脑部署本项目后，只能在电脑与移动设备处于同一局域网内时才能正常使用（因为没有公网ip）。换句话说，只有当电脑和手机连接到同一WiFi下才能正常使用，无论是**电脑开热点连手机**或者**手机开热点连电脑**都可以，在家里**连接同一个WiFi**也可以

但是**中大校园网SYSU_SECURE由于网络设置的原因无法正常使用**。

个人笔记本电脑部署分为两步：

1.   使用Windows IIS搭建web服务
2.   关闭防火墙对端口的拦截

#### 第一步：使用Windows IIS搭建web服务

首先需要打开 **启用或关闭Windows功能** 页面。Win11用户可以直接在开始菜单中搜索

![image-20240529023453239](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529023453239.png)

其他windows版本的用户可以在控制面板中搜索到这一项

![image-20240529023853125](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529023853125.png)

在打开的窗口中如图将**Internet Information Services**条目下这些项目勾选。注意下面的**Internet Information Services可承载的Web核心**不用勾选，点击确定。

![image-20240529024310577](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529024310577.png)

等待系统安装完成后，进入控制面板，进入**管理工具**（在我电脑上叫**Windows工具**）

![image-20240529025057587](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529025057587.png)

选择**Internet Information Services (ISS)管理器**

![image-20240529025154315](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529025154315.png)

在左侧的**网站**，右键选择**添加网站**

![image-20240529025348581](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529025348581.png)

在弹出的 *添加网站* 页面，可以进行设置。“网站名称”可以自己随意命名，“应用程序池”选择“DefaultAppPool”，“物理路径”选择存放该项目的文件夹，“端口”可以写自己电脑不用的端口，比如我写的是8080，然后点击确定即可。

![image-20240529025745088](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529025745088.png)

接着回到管理器中，选择新建的网页，在右边找到**身份验证**选项，双击

![image-20240529025913624](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529025913624.png)

在**身份验证**页面中，点击**匿名身份验证**，在右侧点击“编辑”，选择“应用程序池标识”，然后确定

![image-20240529030110743](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529030110743.png)

再次点击左侧新建的网页回到管理器主页，选择**目录浏览**选项，双击，在目录浏览页面中选择启用。

![image-20240529030338231](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529030338231.png)

最后确认在管理器中，新建的网站属于启动状态

![image-20240529030444200](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529030444200.png)

然后打开电脑浏览器输入http://127.0.0.1:8080(这里的8080改成刚才在上面设置过的端口)，正常情况下就可以看到如图页面，项目打开成功。

![image-20240529030634044](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529030634044.png)

#### 第二步：关闭防火墙对端口的拦截

打开控制面板，选择**Windows Defender 防火墙**（Win11可以直接在开始菜单中搜索）

![image-20240529030930248](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529030930248.png)

在左侧导航栏中选择“高级设置”，在弹出的窗口中点击“入站规则”，在右侧面板中点击“新建规则”

![image-20240529031054918](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031054918.png)

![image-20240529031130310](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031130310.png)

在弹出窗口中选择**端口**-->**下一页**-->**TCP**->**特定本地端口 8080(替换成刚才上面设置的端口)**-->**一直下一页到最后一步**

![image-20240529031347963](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031347963.png)

![image-20240529031355334](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031355334.png)

![image-20240529031444517](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031444517.png)

最后一页的名称可以自己随便写，点击“完成”即可。

完成这一步之后，与电脑连接到同一WIFI的移动设备应该就可以通过浏览器打开项目页面了。

#### 附录：移动端打开项目页面

要在移动端打开项目页面，首先需要查询电脑的局域网ip是什么。**首先让电脑和手机处于同一局域网（开热点什么的都可以）**，然后win11用户可以右键开始图标，选择“终端”，其他版本用户可以自行搜索“如何打开cmd”。

![image-20240529031956288](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529031956288.png)

在弹出的窗口中输入`ipconfig`，回车

![image-20240529032048180](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529032048180.png)

查看其中**无线局域网适配器 WLAN**相关的信息（有的系统中这一项可能是英文的，可以直接找带“WLAN”的字眼）

![image-20240529032333782](D:\WORKSPACE\html\zsdx-physics\readme.assets\image-20240529032333782.png)

可以看到对应的IPv4地址为192.168.3.13，那么此时可以打开手机，在浏览器输入http://192.168.3.13:8080 (8080改为上面设置的端口)进行访问，应该就可以打开项目页面了。为了逼真，可以在企业微信中找一个联系人发消息，消息内容就为这个网址。消息发送后这个网址可以点击进入。

![1212de332b09fc8e8927c72a2672862](D:\WORKSPACE\html\zsdx-physics\readme.assets\1212de332b09fc8e8927c72a2672862.jpg)

部署完成。之后电脑关机重启或者是需要重新打开该项目**均无需重新部署**，电脑开机自动启动该网页的运行，只需要开机后电脑手机连接热点，手机即可直接访问网页。如遇打开失败，可能是电脑ip发生了变化，按照 **附录：移动端打开项目页面** 的教程重新查看一次电脑的IPv4地址即可。

这种部署方式的缺点在于需要保持手机与电脑之间的热点或者WIFI连接才能持续访问。在实际应用中可以在宿舍完成部署，用手机打开网页后填好信息，一路打开至订单详细页面，然后保持这个页面不要关掉或者防止被杀后台，即可让手机离开电脑。只要不发生页面跳转或者需要重新进入页面的情况，那网页是可以一直保留的。

## TODO

1.   将预订系统的体育场馆全部提前录入项目中，这样在使用的时候就只需点选，无需手动输入
2.   将订单金额匹配上所预订的体育场馆
3.   将下订单的时间与预定的时间进行匹配，尽量在同一天，避免因为预定时间与下订单时间差距太大
4.   支持高级自定义，允许用户自定义修改包括历史订单和订单号在内的所有订单信息