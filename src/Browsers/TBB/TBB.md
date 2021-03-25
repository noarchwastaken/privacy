# Tor 浏览器 (Tor Browser)

---

<img src="images/logo.svg" height=96> [*来源*](https://gitweb.torproject.org/tor-browser.git/tree/browser/branding/official/firefox.svg?h=tor-browser-78.5.0esr-10.5-1)

Tor 浏览器 - *私密浏览，自由探索。*  
一个匿名、加密、抗追踪、反监视，最重要的是 - 零审查的浏览器。基于 [Firefox](https://www.mozilla.org/en-US/firefox/new/) 构建。

开发者：[Tor Project](https://www.torproject.org/zh-CN/about/people/)  
[官方网站](https://www.torproject.org/zh-CN/) | 源代码 ([cgit](https://gitweb.torproject.org/tor-browser.git/) / [自托管 GitLab](https://gitlab.torproject.org/tpo/applications/tor-browser)) | [许可协议（主要为 MPL 2.0）](https://www.mozilla.org/en-US/MPL/2.0/) | [用户手册](https://tb-manual.torproject.org/zh-CN/)

---

## Tor 浏览器是什么，它和普通浏览器有什么区别？

> 部分引用 [Tor 浏览器用户手册](https://tb-manual.torproject.org/zh-CN/about/)

Tor 浏览器是经过修改的 [Firefox](https://www.mozilla.org/zh-CN/firefox/new/)， 通过 Tor 网络来保护你的隐私和匿名性。使用 Tor 网络带来了两个主要好处：

- 你的网络运营商 (ISP) 或任何本地监控者（例如路由器家长控制）无法监控你使用 Tor 浏览器进行的网络活动，包括网站名称和地址。

- **除非你明确标识自己**（例如登录帐号，署名等），你访问的网站和服务的运营商，或任何监视他们的人不会知道你的真实身份。

此外，Tor 浏览器还抗指纹。“浏览器指纹”指网站通过收集你的电脑配置和硬件特殊的属性来识别你的行为。普通浏览器中的 JavaScript API 会向网站[泄露大量身份信息](https://browserleaks.com/)，而 Tor 浏览器通过禁用或欺骗这些请求来保护你的身份。

最后，默认情况下，Tor 浏览器不保留任何浏览历史。Cookies 和网站数据只在单一会话内有效，关闭 Tor 浏览器或点击“新身份”时清除。

简单来说：Tor 浏览器是一个永远处于“无痕模式”的浏览器，但它除了抵抗例如父母的浏览历史检查之外，还能应对路由器监控、运营商审查，以及网站身份识别等更高级的审查手段。

### Tor 如何工作

`privacy.noarch` 在 [Tor 使用教程]()中已经解释了 Tor 如何工作。不过 *armFusion*会在这回顾一下：

Tor 是由一个虚拟通道 (tunnel) 组成的网络，用于增强你在互联网上的隐私和安全性。

Tor 会将你的流量通过随机选择的三个服务器加密并转发；其加密和路线选择方式类似于将三层 VPN 像洋葱一般卷在一起。这也是 Tor (The Onion Router， 洋葱路由器) 名字的由来。线路中的最后一个节点，即“出口节点”，剥下这个加密“洋葱”的最后一层皮，将流量转发到公网。

![](images/how-tor-works.webp) [*来源*](https://tb-manual.torproject.org/about/)

上图展示了一个用户如何经过 Tor 网络访问互联网。中间的绿色计算机表示 Tor 网络中的节点，三把钥匙则是 *armFusion* 前面提到的“洋葱”的三层皮，这个洋葱从客户端出发，一个节点只能剥掉一层皮（解开一层加密），直到最后的出口节点将数据传输到明网服务器。

### Tor 在中国的现状

因为[防火长城](https://zh.wikipedia.org/wiki/防火长城)的审查，*armFusion* 很抱歉， 你无法在中国“直接”连接到 Tor 网络。因为 Tor 网络的节点是[公开的](https://metrics.torproject.org/rs.html)，防火墙可以对它们进行批量封锁。同时，Tor 的“直接连接”也没有经过混淆处理，并且已经被防火长城检测。

为此，Tor Project 发布了[网桥](https://tb-manual.torproject.org/zh-CN/bridges/)：它们是“未公开”，需要单独请求的 Tor 节点。需要单独请求的特性使得防火墙无法一次性对它们进行全部封锁。目前大部分 Tor 网桥还采用了[传输插件](https://2019.www.torproject.org/docs/pluggable-transports.html.en)，或者叫[混淆](https://en.wikipedia.org/wiki/Obfuscation_(software))。混淆使得防火墙难以鉴别 Tor 流量，并因此难以封锁这些流量。

在中国，目前只有 Tor Project 提供的，使用 [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) 混淆的网桥可以工作。这种混淆方式将网桥部署到大型云服务上，例如 Microsoft Azure 或 Amazon CloudFront， 并将你的 Tor 流量伪装成，根据网桥部署的位置，向微软或亚马逊的连接。

然而，中国对网桥的需求巨大，但这些网桥都是由志愿者运行的、非营利性的代理。因此，meek 网桥供不应求，导致它们速度十分缓慢。“十分缓慢”指数分钟的线路建立，以及 < 10 KB/s 的传输速度 (亲测如此)。

综上所述，*armFusion* 在下面的教程里将会搭配现有的“翻墙”方式使用 Tor。 取决于你使用的前置翻墙代理，通过这种方式连接 Tor 一般可以达到 Tor 的常见速度 (~200KB/s) 甚至更快。

## 如何使用 Tor Browser

### 使用前置代理配置 Tor

首先，请确认你所用的代理工具的本地代理端口。这一般是一个 `SOCKS5` 端口；比如 macOS 下 ClashX 默认使用的端口为 7891。 确保其已经打开并能正常浏览（被屏蔽的）网站。

打开 Tor 浏览器，地址栏输入 `about:preferences` 进入设置 （或者用你平时进入 Firefox 设置的方式），在侧栏中选择 Tor （或者在地址栏输入 `about:preferences#tor`）。

上文已经说明不用网桥的原因，所以请取消勾选 “使用网桥” 复选框。划到下面的 “高级设置”， 勾选 “我使用代理连接到网络”， 代理种类选择 `SOCKS 5`， 地址填入 127.0.0.1，端口填入你上面所看到的本地代理端口。如果你设置了密码认证， 可以在下面填入用户名密码信息， 否则请留空。

最后请回到主页， 随便登录一个网站...... 如果加载成功， 说明你已经成功使用前置代理配置了 Tor！这是 *armFusion*的测试结果：

![osu1](images/osu1.webp)

如果你感兴趣的话，还可以点击地址栏左侧的锁图标，查看你的流量经过的 Tor 节点：

![osu2](images/osu2.webp)

## 安全性等级

安全性等级是 Tor Browser 中的一个实用功能；你可以用它方便的关闭可能会泄漏你的隐私的两大网站特性：媒体资源（图片等）和 JavaScript。

> <i class="fa fa-exclamation-triangle" aria-hidden="true"></i> 有许多网站依赖这两项特性（尤其是 JavaScript）工作；大多数现代网站（比如 Twitter 和 Reddit）都在其页面上使用 JavaScript 实现了一些高级特性，所以**使用此设置可能会导致这些网站无法正常显示** - 请自行权衡。

你可以在设置 - 安全性和隐私 （`about:preferences#privacy`）找到这个设置。它应该长这样：

![seclevel](images/seclevel.webp)

三个选项从上到下分别为：

> - 标准 - 保留所有网站特性。
>
> - 更安全 - 禁用如下的网站特性（可能会导致某些网站崩溃）：
>
>   - 禁用**非 HTTPS 来源**的 JavaScript（只允许 HTTPS 加密传输的 JavaScript 脚本运行），同时禁用一部分脚本功能（如 [WebAssembly](https://zh.wikipedia.org/wiki/WebAssembly) 和 [JIT](https://zh.wikipedia.org/wiki/%E5%8D%B3%E6%99%82%E7%B7%A8%E8%AD%AF)（有沙盒逃逸风险，是造成 2021 年初 Firefox 沙盒逃逸漏洞的主要原因））
>   - 禁用一些字体和数学符号
>   - 禁用 HTML5 媒体和 WebGL 的自动播放。
>
> - 最安全 - 这一模式默认只允许静态或纯文本网页必须的基本特性。在 “更安全” 设置的基础上：
>
>   - 全局禁用 JavaScript
>
>   - 禁用一些图片和图标
> 	

## 广告过滤插件