# 一键脚本搭建科学上网Trojan梯子(自建VPN)详细教程


## Trojan简介

简单理解为就是v2ray+ws+TLS的lite版吧，也是走https，安全稳定性比较高。在某些设备上表现比v2ray+ws+TLS好一些。

## 购买VPS

Ok，正式进入教程，首先第一步，你还是得有个vps，我现在用的[vultr](https://www.vultr.com/?ref=8944093-8H)，首要原因可以随时删除服务器重建服务器，以达到换ip的效果，其次这是我见过有日本节点的最便宜的一家（日本节点谁用谁知道，特别是上海小伙伴们），然后就是可以支付宝付款，很方便了。

## 如何购买性价比高的墙外服务器？

在搭建之前需要一台境外的云服务器，而 [vultr](https://www.vultr.com/?ref=8944093-8H) 服务商比较稳定，安全，相当于境内的阿里云。

值得说的一点是， [vultr](https://www.vultr.com/?ref=8944093-8H) 给新用户的福利相当给力，充值 10 美元就可以获取 100 美元，你可以点击 [vultr 专属赠送新用户 100 美元](https://www.vultr.com/?ref=8944093-8H) 进去抢先注册。

右上角有注册按钮，你也可以切换成中文界面：

<img width="1446" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119019442-be0cc500-b98c-11eb-895b-0d6300dce93d.png">

![](https://user-images.githubusercontent.com/84239400/119019760-0d52f580-b98d-11eb-9837-aba0990f1dfb.png)

接着使用邮箱和密码就可以注册了。

![](https://user-images.githubusercontent.com/84239400/119020042-4ee3a080-b98d-11eb-8341-bfc30f4b103c.png)

进去之后你可以看到这个页面，说明你已经通过 [vultr 专属优惠链接](https://www.vultr.com/?ref=8872890-6G) 获得了 100 美元赠送的资格：

![](https://user-images.githubusercontent.com/84239400/119020173-733f7d00-b98d-11eb-8ecc-a1afeb556fe6.png)

现在你只要选择支付宝充值 10 美元以上，就可以获得额外赠送的 100 美元。

![](https://user-images.githubusercontent.com/84239400/119020280-966a2c80-b98d-11eb-9113-8f5f0b75c5ea.png)

接下来就可以在这个平台选购云服务器了。

点击页面左边菜单栏的 「Products」进入服务器选购页面。

### Choose Server 选择服务器

选择 Cloud Compute 即可：

![](https://user-images.githubusercontent.com/84239400/119020373-af72dd80-b98d-11eb-8478-02d735b82709.png)

### Server Location

服务器的位置，可以选择美国地区，比如纽约：

![](https://user-images.githubusercontent.com/84239400/119020467-cadde880-b98d-11eb-8927-d3d837bbc20c.png)

### Server Type

服务器类型，选：centos 7 x64 系统：

<img width="1297" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/144575029-080f1a8c-4733-43d1-a000-c3d884f17378.png">

### Server Size

内存，选择最便宜的完全够用，而且性价比高，注意不要选择IPv6 ONLY的，要不然无法搭建使用。

<img width="1240" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/144575352-989d7239-99fb-4b81-a416-c50623ac25ff.png">

选择完了之后，下面的其它东西都不需要填，直接点击右下角 Deploy Now 就可以了：

![](https://user-images.githubusercontent.com/84239400/144575658-70cf1056-aff3-4972-a0f8-06f551157821.png)

这时候你就拥有了自己的一台云服务器了：

<img width="1261" alt="VPN搭建教程" src="https://user-images.githubusercontent.com/84239400/119021075-86068180-b98e-11eb-82a9-71edb9934f23.png">

## 购买域名

Trojan和v2ray+ws+TLS一样，也是走https，所以也需要有一个自己的域名为我们做掩护。

买域名的地方也很多，国内主要是腾讯云和阿里云，域名不需要在国外供应商买，哪里买都一样。腾讯阿里都有新人优惠，第一次购买域名，像.club, .xyz之类的小众域名基本只要1块一年，很便宜了。我用的是腾讯云，这里也以腾讯云为例，其他平台的流程也基本一致。

首先进入腾讯云主页, 先点右上角的免费注册，注册登陆之后再产品这里选域名注册，热门里就有。

![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664581-18396d6d-e07d-454d-936c-75bc3692a390.png)

之后可以直接搜自己想要的域名，也可以直接点下面的1元域名优惠抢，首次注册都可以1块钱购买一年。（这里就不放图了，都是中文，应该很好操作了）

购买之后点右上角进入控制台，搜索云解析，进入这样一个界面。点击你自己的域名，或者点击右边域名对应的解析。（可以看到这里腾讯要求在国内开展网站需要备案，我们其实也相当于建立了一个网站，但是我的经验因为我们用国外的服务器所以不备案也没关系。）

![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664597-3fa279bc-1f2b-4a64-8841-45b690e1de3b.png)

之后直接点击快速添加网站/邮箱解析，选择网站解析。之后输入刚才购买的vps的ip地址就好了，解析大概需要十分钟以内。

![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664598-89eb929b-3410-4c09-9904-432b2b2aa604.png)

到这里域名购买解析部分就结束了，可以进行下一步，也是核心的一步，在vps上用脚本安装Trojan服务端。

## 脚本安装v2ray服务端

首先下载一个ssh软件，比如putty，打开软件是酱婶儿的。填进去你的ip然后open。

putty下载: 
https://rachel.heartango.com/putty-64bit-0.73-installer.msi

![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664600-18bc56ad-79d0-42af-9130-bdcbd2306785.png)

然后用root账号登陆（注意login as 后面是填写用户名的，不是密码，先填用户名root回车再写密码，虽然好像很罗嗦，我之前也没想过这里也需要讲，但是真的有许多人卡在这一步），密码就是刚才记下的密码，输进去，敲回车。（注意这里可以直接把密码复制过去，但是一定注意第一不要复制到了空格，第二鼠标在putty里敲右键就是粘贴了，不要再ctrl+v，密码也是不会显示的，输进去直接回车就好）

进入命令行后，直接复制输入以下代码进行脚本安装。

```
curl -O https://raw.githubusercontent.com/luyiming1016/ladderbackup/master/trojan_centos7.sh && chmod +x trojan_centos7.sh && ./trojan_centos7.sh
```


之后选1，回车，等待一下。过程中会提示需要输入域名，输入解析到本VPS的域名，然后回车。
等待之后，会出现安装完成的信息，是一个指向你域名下的一个下载链接，右键选中复制下来，然后粘贴进浏览器下载，下载下来是一个trojan-cil压缩包，解压点开文件夹下usr->src->trojan-cil->config.json，记下remote_addr, remote_addr, password三项。

到这时候，用任意一个浏览器输入你刚才注册的域名，应该就可以看到一个这样的网站（如果你到这看不到网页，就别往下做了，有两个原因，第一可能你买域名的时候解析地址填错了，第二，也是最大的可能性，这个ip的443端口已经被墙了，这时候就得去vultr重建一个vps了）。理解为它就是我们翻墙的掩护就好。


![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664602-1fc0ca51-bd99-435e-b478-e2804249a2ed.png)

之后回到我们的putty界面，输入下面的代码安装BBR加速，安了会让科学上网速度提升很多。

```
cd /usr/src && wget -N --no-check-certificate "https://raw.githubusercontent.com/luyiming1016/ladderbackup/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```

之后显示BBR启动成功，这样我们服务端架设的步骤就完全完成了。

这时候注意最好在命令行输入service v2ray start，确保v2ray起来了，因为有时会发生系统重启v2ray进程起不来，会发生伪装网站可以进但配好不好用的状况

# 客户端使用
## window使用Trojan梯子
客户端下载地址：
https://rachel.heartango.com/vtwowt.zip

windows下现在体验最好的还是这个带Trojan版本的v2ray客户端。

- 双击打开trojan文件夹下的 v2rayN.exe 文件
- 如客户端运行Trojan报错，请尝试下载以下软件，安装完毕再运行Trojan
- [isual C++ 2015 (x64、x86均安装)](https://www.microsoft.com/zh-CN/download/details.aspx?id=48145)
- [Windows.NET Framework 4.6.2](https://support.microsoft.com/zh-cn/help/3151800/the-net-framework-4-6-2-offline-installer-for-windows)
- 桌面右下角会出现1个小图标，再次双击，打开 Trojan 设置面板
- 点击「服务器」-「Add [Trojan] server」来添加Trojan节点
- 打开v2rayN.exe,右下角出现如下小图标：

![Trojan梯子](https://user-images.githubusercontent.com/84239400/146664605-966ee6cb-c8a7-480d-9b99-4eb223873bd8.png)


双击左键点开，选择服务器，添加Trojan服务器。将之前在putty中记下的参数(地址，端口，密码)输入这里，然后点击确定。

之后就配置成功了，建议在配好的服务器上单击右键选择“批量导出分享URL至粘贴板”，然后在记事本中保存，之后会用在配置手机客户端里。

之后点右上角×关闭主界面，在右下角小图标单击右键。在服务器一栏勾选上已经配好的服务器，点击启用Http代理，代理模式选pac模式。之后就可以开心的科学上网了。提醒一下记得不用的时候，按顺序先把启用http代理勾选取消，之后退出客户端，最后关电脑。如果有没有按顺序操作，再次开机发现上不了网了，请在这里的小电脑点右键，打开“网络和Internet设置”→代理→手动设置代理，将使用代理服务器一栏关闭。

##  ios使用Trojan梯子
新版本的Shadowrocket（简称小火箭）也支持Trojan的配置，虽然小火箭也要钱，不能在大陆App store下载，但是网上共享账号很多，大家可以多搜一搜，关键词“Shadowrocket/小火箭 ios 共享账号”。我这里提供两组账号，大家试一试，不保证好用，因为这种多人共享的账号很容易被苹果封了，账号时效性很强，不好用大家就自己找找了。

app store账号：hadadreammm@gmail.com
密码：As778899

注意下完小火箭后一定马上把账号退了，换回自己的账号。

之后把刚才在电脑端导出的链接复制到手机里，在手机上直接复制，然后打开小火箭，小火箭就会自动识别到已经复制好的链接，将服务器添加进来，之后把最上面的链接打开就好了。（软件会要求使用手机vpn，请允许）

若导出链接在小火箭里不好用，就在小火箭手动添加Trojan节点，输入地址，端口，密码，

## Android使用Trojan梯子
https://rachel.heartango.com/igniter-0.1.0-pre-alpha10.apk
上面的安不了的话用下面这个，

https://rachel.heartango.com/igniter-0.1.0-pre-alpha9.apk
这个进去直接输入节点地址，端口，密码三项信息就可以了。
