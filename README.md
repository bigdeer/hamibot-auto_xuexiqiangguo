# hamibot-auto_xuexiqiangguo
基于Hamibot的安卓端学习强国自动化脚本

# 免责声明
**本脚本为免费使用，本脚本只供个人学习使用，不得盈利传播，不得用于违法用途，否则造成的一切后果自负！**
# v1.0 版本声明
目前版本**无法**完成挑战答题、四人赛、双人对战、订阅、发表观点模块，其他模块均可自动化完成（当然不包括强国运动！），因为本人是在校学生无法把全部精力放在这，因此如果有想合作的小伙伴请在[GitHub联系我](https://github.com/dundunnp/hamibot-auto_xuexiqiangguo)，一起完成更新项目
***
# 使用说明
1. 打开无障碍服务权限、程序保持后台运行
2. 手机屏保设置时长大于2分钟
3. 手机打开勿扰模式，防止突然的信息弹窗导致脚本的失败
4. 如果要完成答题，请在执行脚本后，点击手机弹窗出来的打开截图权限
4. 在应用中尽量不要有其他弹窗，比如打开应用，提示你发现新版本的弹窗

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/b095b81f07d19bd4b347052e5b9ace0.png" alt="b095b81f07d19bd4b347052e5b9ace0" style="zoom:50%;" />

填写你对应的省份，用于打开本地频道可以积一分（一分也是分!注意不要多加一个省字），比如我这里是江西，然后随意选择一个本地频道（比如我选择的是江西卫视）

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/HwMirror_zmj2eavi85.png" alt="HwMirror_zmj2eavi85" style="zoom:50%;" />

而后填写跳转页面加载的时间(以秒s为单位)，默认为1s(支持小数点形式)，根据手机性能与网络情况自行而定，时间越长出bug的可能越小，但同时耗费的时间越长。
我的手机是华为mate20 pro用的是1s，大家可以参考一下，不建议小于1s，太快不符合正常人类点击频率，容易被系统侦测出（当然我也设置了随机时间性，你的任何等待时间都是你设定的基础值加一个随机时间）

目前脚本支持两种模式：
1. 仅完成阅读文章与看视频部分，不完成答题
2. 除没实现部分外，全部完成

但是第二种模式需要通过华为API实现OCR功能，从而完成答题，注意这里通过华为API的收费标准如下，可以看到每个月有一千次免费使用，是完全够用的，相当于免费

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_QmQEm4XND4.png" alt="msedge_QmQEm4XND4" style="zoom:50%;" />

因此如果只想实现模式一的用户后面的选项不需要填写，到这里脚本就可以正常运行了！

**但如果想实现答题功能你还需要完成以下步骤：**

登录[华为云官网](https://www.huaweicloud.com/)，点击注册（如果已经有账号可以直接登录）

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_LAXxJYLH9v.png" alt="msedge_LAXxJYLH9v" style="zoom: 33%;" />

注册成功后，登录

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_MF3EQpHYfl.png" alt="msedge_MF3EQpHYfl" style="zoom: 33%;" />

点击账户中心，并点击实名认证中的个人认证

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_i0WswextDv.png" alt="msedge_i0WswextDv" style="zoom: 33%;" />

完成认证后，大家可以在基本信息中改一个自己的账号名（我这里改为了dundunnp，注意只能改一次账号名，大家也可以选择不改），而后还需创建一个用户，点击统一身份认证

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_KaElfaa67l.png" alt="msedge_KaElfaa67l" style="zoom:33%;" />

虽然可以看到已经有一个企业管理员用户，**但华为账号不支持获取帐号Token，需要我们自己创建一个IAM用户**，授予该用户必要的权限，获取IAM用户Token，因此，点击右上角的创建用户

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_DF8MDpI9Ck.png" alt="msedge_DF8MDpI9Ck" style="zoom:33%;" />

填写用户名与密码，请记住，后面需要用到，点击下一步

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_uNigytTpFa.png" alt="msedge_uNigytTpFa" style="zoom:33%;" />

点击admin，使其用户加入用户组，点击创建用户

搜索框中[搜索ocr](https://www.huaweicloud.com/s/JW9jciU)，在第一条中点击立即使用

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_HNfceTw9ey.png" alt="msedge_HNfceTw9ey" style="zoom:33%;" />

将页面滚动到最下方

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_uUOIuwfWH1.png" alt="msedge_uUOIuwfWH1" style="zoom:33%;" />

翻到第二页，找到网络图片识别，点击开通服务，并确认

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_lLg8QqR7m8.png" alt="msedge_lLg8QqR7m8" style="zoom:33%;" />

点击左侧的调用指南其下的API调用

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_ccv7yxXG7h.png" alt="msedge_ccv7yxXG7h" style="zoom:33%;" />

在这个界面中，下面的配置参数查询下面的构造请求模块中有，Endpoint和project_id两项，将这两项填入配置中

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_iHvmohHfBh.png" alt="msedge_iHvmohHfBh" style="zoom:33%;" />

再将第二个模块的domainname和projectname填入配置中，**注意，这里千万不要将这里显示的dundunnp填入username中，domainname是企业管理员的账号名也就是dundunnp，而username和password填入的是刚刚创建的用户的信息，也就是dundun和XXXXX(你们设置的密码)。**

这里是我的配置文件的例子：

<img src="http://r32wozj47.hn-bkt.clouddn.com/img/msedge_4qInvihBwb.png" alt="msedge_4qInvihBwb" style="zoom:50%;" />

恭喜你，到这里就算是完成了！

***
待编写：
1. 填空题如果文本框有分开的情况还未解决
2. 视频题待编写
3. 挑战答题、四人赛、二人赛待编写
3. 专项答题和每周答题不能重复答题，因此如果做了就不用再做