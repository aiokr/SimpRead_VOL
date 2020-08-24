\> 本文由 \[简悦 SimpRead\](http://ksria.com/simpread/) 转码， 原文地址 \[www.bilibili.com\](https://www.bilibili.com/read/cv1236103/)

本文围绕三个部分来讲：弹幕插件，礼物答谢插件，多平台推流工具

![](http://i0.hdslb.com/bfs/article/4adb9255ada5b97061e610b682b8636764fe50ed.png)

**弹幕插件篇**
=========

**1\. 小葫芦弹幕助手 5.0 系列  
**

（下载地址：http://www.obsapp.com/apps/danmupro/）

![](http://i0.hdslb.com/bfs/article/8836426341046aeaa62cd4961f8193fc20451b91.png@1320w_720h.webp)

设置很简单，多样性也很丰富，普通用户首选小葫芦，官网有详细的教程。

**2\. 智播 OBS 云插件**

找到弹幕插件

![](http://i0.hdslb.com/bfs/article/5ec6ac90cab105deba3368dbf33501ebd205fdf7.png@1320w_602h.webp)

进入设置界面

![](http://i0.hdslb.com/bfs/article/f4fe9e2fcf8f64ad630dfaae5f49387e97ffd312.png@1320w_2044h.webp)

按照提示设置，设置完毕记得保存配置

然后，打开 OBS，添加浏览器源，将设置上方的链接粘贴到 OBS 浏览器源设置的 URL 栏

根据显示区域自行调整宽高

![](http://i0.hdslb.com/bfs/article/7f85786f9b2cd84448792fe5153cc96d5e2a1c74.png@1320w_1110h.webp)

URL 是静态链接，下次使用不必修改，该插件的好处是不必另外安装软件，使用方便，支持多源添加（后面多平台推流会用到）。但多样性不够强。

多弹幕源添加，则可以再在智播设置里添加一个直播间，生成第二个 URL，添加进 OBS，注意命名加以区分

![](http://i0.hdslb.com/bfs/article/db1897fba06f0821f5c6f7b58c0f64e2d54f915d.png@632w_312h.webp)![](http://i0.hdslb.com/bfs/article/c872481096677d2c3c30d24bfc468ff564027bfb.png@342w_194h.webp)

多弹幕源效果如下

![](http://i0.hdslb.com/bfs/article/35807056dca407221cd0554bbbffa1627638cb16.png@654w_514h.webp)![](http://i0.hdslb.com/bfs/article/4adb9255ada5b97061e610b682b8636764fe50ed.png)

礼物答谢插件
======

主要是用到智播 OBS 插件

![](http://i0.hdslb.com/bfs/article/0f93ae876b4786a1b17ffb8eedb473d929bf98e8.png@1320w_604h.webp)

使用方法同上弹幕插件。

![](http://i0.hdslb.com/bfs/article/4adb9255ada5b97061e610b682b8636764fe50ed.png)

**多平台推流工具**
===========

主要讲两个工具，一个是 Nginx，一个是 Restream。建议准备梯子。

**1.Nginx**

载点：https://github.com/miaulightouch/nginx-rtmp-win32/releases/download/v0.2/nginx-rtmp-win32-v0.2.7z

①设置推流目标路径

打开【option.txt】

![](http://i0.hdslb.com/bfs/article/542748a34c02e00d92d4723ea335456404f4e0ee.png@1320w_962h.webp)

填入即将推流的所有平台的 rtmp 串流地址和串流码

![](http://i0.hdslb.com/bfs/article/b276925952d50b1d9bb05610d43ddfabaac8378b.png@1320w_136h.webp)

注意事项：一行设定一个分流，每行 push 开头、空格、串流地址 / 串流码、最后以; 结尾

**以上所有标点全部是英文状态**

然后保存

打开【啟動 nginx 服務. bat】，如不能正常打开，请检查 option.txt 是否填写正确。

②设置 OBS

在流选项内，将 URL 设为 rtmp://127.0.0.1:1935/live

此为静态链接，不需要后续修改

流名称不必填

![](http://i0.hdslb.com/bfs/article/6c8d2cd8a214011a68f5f3fbfabef092d67106b1.png@1320w_1042h.webp)

之后就可以推流到你填入的所有平台上了。

直播结束打开【結束 nginx 服務】方可正常关闭多平台推流通道。

每次直播前都要更新你的【option.txt】内容

**2.Restream**

restream 是一个中间人推流媒介，你的 OBS 信号发送到 restream，再负责将其传输到你设置的各个平台上，不是常规的直播平台，但同样具有它自己的 rtmp 地址和串流码。

服务网址：https://restream.io/

①设置推流目标路径

注册账号，登录，添加你的所有 Channels

![](http://i0.hdslb.com/bfs/article/01eea224f93dd534bf11fd32019cfa1e7155c283.png@1320w_574h.webp)

设置内填入你所有推流平台的 rtmp 地址和串流码

②设置 OBS

在频道设置右侧，找到 Resteam 的的 rtmp 地址和串流码，将其粘贴到 OBS 流设置中

![](http://i0.hdslb.com/bfs/article/52e79cf3033108edf1819b4dab464b159666ea52.png@694w_474h.webp)![](http://i0.hdslb.com/bfs/article/8d2b885192d401f5ff772c4c487e318358dc630a.png@1320w_1042h.webp)

要注意的是 Restream 的 rtmp 地址和串流码和直播平台一样是动态的，每次开播都需要重新获取。换句话说，双平台直播需要输三次 rtmp 地址和串流码，而使用 Nginx 只需要输入两次