# Caps Writer

### 💡 简介

一款电脑端语音输入工具，后台运行脚本后，按下按下 `Caps Lock`（也就是大写锁定键）超过 0.3 秒后，开始语音识别，松开按键之后，自动输入识别结果。

目前使用了阿里云的一句话识别 api。（有兴趣的可以自行改成百度、腾讯、讯飞、谷歌的 api ）

因为使用了阿里云的 api，所以需要用户自己到阿里云申请，再填到 `token.ini` 中才能正常使用。

对于聊天时候进行快捷输入、写代码时快速加入中文注释非常的方便。

### 📝 背景


我真是气抖冷，为什么直到 0202 年，仍然没有开发者做过一个好用的语音输入工具？


有人建议用搜狗输入法、讯飞输入法的语音输入，但这几个方面是真让人受不了：


* 广告太多，拒绝安装
* 我主力五笔，不使用搜狗输入法、讯飞输入法，顶多临时用下微软拼音
* 就以搜狗输入法为例，它的语音输入快捷键只能是`Ctrl + Shift + A/B/C……`，有以下槽点：
  * 这个快捷键会和许多软件的快捷键冲突，且不好记
  * 打字时，按这样三个快捷键，手指很别扭，不爽
  * 它的逻辑是按下快捷键后，启用语音输入，你一停顿一下，要说下一名，语音输入却结束了，不能让用户决定什么时候结束语音输入。


为了在电脑上语音输入，我之前是用的 Quicker 的手机端进行语音识别，输入到电脑上，需要两个设备，非常麻烦。今天终于做好我心目中最好用的电脑端语音输入工具了！


### 📽️ 视频演示

作者为这个工具录制了使用视频演示、申请 api 的教程视频

请到 HacPai 帖子中进行查看：[Caps Wirter 发布：按住大写锁定键，进行语音识别输入](https://hacpai.com/article/1594371212477) 

或者到 Bilibili 查看：[ Caps Writer（电脑端语音输入工具）使用教程 ](https://www.bilibili.com/video/BV1qK4y1s7Fb/)

## 🔮 开箱即用

小白用户，只需要在 [Release](https://github.com/HaujetZhao/CapsWriter/releases) 界面下载打包好的 exe 文件，运行，会在同级目录生成一个 `token.ini` 文件，在 `token.ini` 中填入你阿里云拥有 **管理智能语音交互（NLS）** 权限的 **RAM访问控制** 用户的 **Accesskey Id**、**Accesskey Secret** 和智能语音交互语音识别项目的 **appkey** ，就可以正常使用了。

详细申请、填写 API 的步骤请到 [Caps Wirter 发布：按住大写锁定键，进行语音识别输入](https://hacpai.com/article/1594371212477)  或到 [ Caps Writer（电脑端语音输入工具）使用教程 ](https://www.bilibili.com/video/BV1qK4y1s7Fb/) 查看视频教程

### 🛠 开发使用

本工具是一个python脚本，上面小白下载的 Release 其实是用 pyinstaller 导出的 exe 文件，如果你想在源码基础上使用，就需要安装以下模块：

- keyboard
- pyaudio
- configparser
- aliyunsdkcore
- alibabacloud-nls-python-sdk

其中：

- pyaudio 在 windows 上不是太好安装，可以先到 [这个链接](https://www.lfd.uci.edu/~gohlke/pythonlibs) 下载 pyaudio 对应版本的 whl 文件，再用 pip 安装
- alibabacloud-nls-python-sdk 不是通过 python 安装，而是通过 [阿里云官方文档的方法](https://help.aliyun.com/document_detail/120693.html) 进行安装。

另外，需要在 `token.ini` 中填入阿里云拥有 **管理智能语音交互（NLS）** 权限的 **RAM访问控制** 用户的 **accessID**、**accessKey** 和智能语音交互语音识别项目的 **appkey** 。

本文件夹内有一个 `安装指南` 文件夹，在里面可以找到详细的安装指南，还包括了提前下载的 alibabacloud-nls-python-sdk 和 pyaudio 的 whl 文件。

用 python 运行 `run.py` 后，按下 `Caps Lock`（也就是大写锁定键）超过 0.3 秒后，就会开始用阿里云的 api 进行语音识别，松开按键后，会将识别结果自动输入。

### 后话

因为作者就是本着凑合能用就可以了的心态做这个工具的，所以图形界面什么的也没做，整个工具单纯就一个脚本，功能也就一个，按住大写锁定键开始语音识别，松开后输入结果。目前作者本人已经很满意。

欢迎有想法有能力的人将这个工具加以改进，比如加入讯飞、腾讯、百度的语音识别api，长按0.3秒后开始识别时加一个提示等等等等。

目前已知改进的方向：

- 使用 VoiceRecognition 中的 google_recognize 进行识别，使用的是谷歌的免费语音识别 api，优势是不用用户个人申请 api 了，但是在中国大陆不太好使用。在海外的话会非常好用。
- 使用 Baidu AI 语音识别 api，每个账户有 200 万次的免费额度。
- 使用 Tencent AI 语音识别 api，每个账户有 5000 次的免费额度。
- 使用讯飞的语音识别 api，每个账户有 1 年的免费使用时间。

欢迎有兴趣的贡献者对项目进行翻译（国际化），添加 Google、Bing 的 api，让海外用户也可以使用这个便捷的语音输入工具！