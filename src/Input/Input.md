# 自由打字，打字自由 - 输入法隐私

---

作为中文用户，你的线上生活应该离不开输入法。

输入法，掌握着所有你输入的文本。

一个侵犯隐私，或是恶意的输入法所带来的危害，远不亚于符号文字输入中的键盘记录器 (Keylogger), 并且它可以隐藏为人畜无害的工具潜入你的线上生活中。

## “云输入”的巨大隐私问题

如果你用过商业的输入法（搜狗输入法、百度输入法...），你应该对“云输入”这个词不陌生。

云输入是众多商业输入法所提供的功能，它通过“云端”的帮助为你提供更精确的候选词和联想结果。

然而，要让*云端*为你工作，首先你得为云端工作：将你要输入的内容上传到云端。“云输入”的数据库就是这么构建的 - 收集用户输入的内容，并且将它推荐给其它在相同上下文中的用户。

简而言之：*你在把你输入的内容分享给别人，只不过它被分成了一个个独立的词。同时你也在使用其他人的输入内容。*

### 你向输入法云端上传的信息

> 你向云端上传了什么信息？云端在收到你的信息后做了什么？如果对手向输入法云端请求你的信息，会发生什么？

如果你是一个“普通用户”，你不出意料地没有读过商业输入法们的隐私政策。下面是一些搜狗输入法[隐私政策](https://shouji.sogou.com/wap/htmls/privacy_policy.html)的节选，以回答上面的问题。

#### 你向“云输入”上传的信息，包括但不限于：

> 您在使用本软件时，根据您在软件安装及使用中授予的具体权限，搜狗公司会收集您的**设备品牌、设备型号、屏幕分辨率、设备识别码、系统版本、应用识别码、IP地址。**
>
> 在您使用快捷翻译功能时，本软件需要获取您输入的**待翻译的文本信息**...
>
> 在您使用智能回复功能时，本软件会读取您在当前聊天场景下**前文内容**...
>
> 在您使用云输入功能时，本软件会读取您当前输入的**字符串**，并通过技术分析字符串为您提供云联想词...
>
> 为了向您提供地理位置词库功能，**当您输入时搜狗公司可能会使用GPS、WiFi或其他技术方式收集和处理有关您实际所在位置的信息**...

根据对“云输入”功能的描述，搜狗完全可以通过你上传的输入字符串**重建你的输入内容**。

根据搜狗当前 (2020-10) 的隐私政策，搜狗输入法**仅会匿名化日志信息**。因此可以认定，上述非日志的输入信息是非匿名的，并且与你的设备识别码 (e.g. IMEI) 和登录的帐号（如果有）绑定。

#### 除了让大数据为你服务，你也在为大数据服务：

> **在符合相关法律法规的前提下，搜狗公司可能将通过本软件所收集的信息，用于搜狗公司的其他产品和服务，或帮助搜狗公司设计新产品和服务，或在不透露您个人信息的前提下对用户数据库进行分析并予以商业化的利用。例如搜狗公司可能将您在使用我们某一功能或服务时收集的信息，在另一功能或服务中向您提供特定内容，包括但不限于展示广告、基于特征标签进行间接人群画像并提供个性化服务。**

*如果你没为这个产品付费，那么你多半就是那个产品。* 商业输入法会使用你的输入向你展示针对性的广告。

#### 向第三方披露你的信息前不需要经过你同意的状况：

> （1）与国家安全、国防安全有关的；
>
> （2）与公共安全、公共卫生、重大公共利益有关的；
>
> （3）与犯罪侦查、起诉、审判和判决执行等有关的；
>
> （4）出于维护个人信息主体或其他个人的生命、财产等重大合法权益但又很难得到本人同意的；
>
> （5）所收集的个人信息是个人信息主体自行向社会公众公开的；
>
> （6）从合法公开披露的信息中收集的您的个人信息的，如合法的新闻报道、政府信息公开等渠道；
>
> （7）根据您的要求签订和履行合同所必需的；
>
> （8）用于维护所提供的产品或服务的安全稳定运行所必需的，例如发现、处置产品或服务的故障；
>
> （9）为合法的新闻报道所必需的；
>
> （10）学术研究机构基于公共利益开展统计或学术研究所必要，且对外提供学术研究或描述的结果时，对结果中所包含的个人信息进行去标识化处理的；
>
> （11）法律法规及监管政策规定的其他情形。

**因此，如果你的对手是上面任意一个，你的计划和安全将受到威胁。**

## 向云输入说不

看似便利的功能潜藏巨大的危害；不过你可以从现在开始止损。

- 首先，最基础的，你需要停止使用云输入，来让输入法不再上传你的输入信息；

- 其次，如果可以，你还要禁止输入法联网，这样即使它收集了信息也无法 "call home".

- 最后，如果你的盟友给了你更好用的工具，为什么要用对手的呢？

本章节，*noarch* 将教你如何禁用云输入以及其它依赖云端的功能，禁止输入法联网，并且 - **硬核** - 改用开源自由的输入方案。

---

创建：2020-10-27, *noarch*  
最后修改：2020-10-27, *noarch*