## 效果展示

注意：本项目暂不支持flutter2.0，如果您用的是flutter2.0版本，请先降低版本。

您可以 [下载](https://cloud.tencent.com/document/product/647/17021) 安装我们的 Demo 体验语音沙龙的能力，包括语音聊天、上下麦、低延时语音互动等 TRTC 在语音聊天场景下的相关能力。

主播麦位操作：

[](https://tccweb-1258344699.cos.ap-nanjing.myqcloud.com/sdk/trtc/chatsalon/pjckq-4zdgj.gif)

观众麦位操作：

[](https://tccweb-1258344699.cos.ap-nanjing.myqcloud.com/sdk/trtc/chatsalon/new.gif)

如需快速接入语音沙龙功能，您可以直接基于我们提供的 Demo 进行修改适配，也可以使用我们提供的 TRTCChatSalon 组件并实现自定义 UI 界面。

[](id:DemoUI)
## 复用 Demo 的 UI 界面

[](id:ui.step1)
### 步骤1：创建新的应用
1. 登录实时音视频控制台，选择【开发辅助】>【[快速跑通Demo](https://console.cloud.tencent.com/trtc/quickstart)】。
2. 输入应用名称，例如  `TestChatSalon`  ，单击【创建】。

>!本功能同时使用了腾讯云 [实时音视频 TRTC](https://cloud.tencent.com/document/product/647/16788) 和 [即时通信 IM](https://cloud.tencent.com/document/product/269) 两个基础 PaaS 服务，开通实时音视频后会同步开通即时通信 IM 服务。 即时通信 IM 属于增值服务，详细计费规则请参见 [即时通信 IM 价格说明](https://cloud.tencent.com/document/product/269/11673)。



[](id:ui.step2)
### 步骤2：下载 SDK 和 Demo 源码
1. 根据实际业务需求下载 SDK 及配套的 Demo 源码。
2. 下载完成后，单击【已下载，下一步】。
![](https://main.qcloudimg.com/raw/3b115019ddfd0866108ed1add30810d8.png)

[](id:ui.step3)
### 步骤3：配置 Demo 工程文件
1. 进入修改配置页，根据您下载的源码包，选择相应的开发环境。
2. 找到并打开 `/lib/debug/GenerateTestUserSig.dart` 文件。
3. 设置 `GenerateTestUserSig.dart` 文件中的相关参数：
<ul style="margin:0"><li/>SDKAPPID：默认为PLACEHOLDER，请设置为实际的 SDKAppID。
<li/>SECRETKEY：默认为PLACEHOLDER，请设置为实际的密钥信息。</ul>
<img src="https://main.qcloudimg.com/raw/31b265429e66a899acccb875a8c17ad6.png">
4. 粘贴完成后，单击【已复制粘贴，下一步】即创建成功。
5. 编译完成后，单击【回到控制台概览】即可。


>!本文提到的生成 UserSig 的方案是在客户端代码中配置 SECRETKEY，该方法中 SECRETKEY 很容易被反编译逆向破解，一旦您的密钥泄露，攻击者就可以盗用您的腾讯云流量，因此**该方法仅适合本地跑通 Demo 和功能调试**。
>正确的 UserSig 签发方式是将 UserSig 的计算代码集成到您的服务端，并提供面向 App 的接口，在需要 UserSig 时由您的 App 向业务服务器发起请求获取动态 UserSig。更多详情请参见 [服务端生成 UserSig](https://cloud.tencent.com/document/product/647/17275#Server)。

[](id:ui.step4)
### 步骤4：编译运行
> 安卓需要在真机下运行，不支持模拟器调试

执行 `flutter pub get`

Android端

1. 执行 `flutter run`。
2. 使用 Android Studio（3.5及以上的版本）打开源码工程，单击【运行】即可。

iOS端
1. 使用 XCode（11.0及以上的版本）打开源码目录下的 `/ios工程`。
2. 编译并运行 Demo 工程即可。

[](id:ui.step5)
### 步骤5：修改 Demo 源代码
源码中的 trtcchatsalondemo 文件夹包含两个子文件夹 ui 和 model，ui 文件夹中均为界面代码，如下表格列出了各个文件或文件夹及其所对应的 UI 界面，以便于您进行二次调整：

| 文件或文件夹 | 功能描述 |
|-------|--------|
| base | UI 使用的基础类。 |
| list | 列表页和创建房间页。 |
| room | 主房间页面，包括主播和观众两种界面。 |
| widget | 通用控件。 |

[](id:model)
## 实现自定义 UI 界面

[源码](https://github.com/c1avie/TRTCChatSalon) 中的 trtcchatsalondemo 文件夹包含两个子文件夹 ui 和 model，model 文件夹中包含可重用的开源组件 TRTCChatSalon，您可以在 `TRTCChatSalon.dart` 文件中看到该组件提供的接口函数，并使用对应接口实现自定义 UI 界面。
![](https://main.qcloudimg.com/raw/fcf694c8550664623414604d14ffcd94.png)

[](id:model.step1)


实现自定义 UI 界面详情参考[文档](https://tcloud-doc.isd.com/document/product/647/53582)

场景sdk参考[文档](https://tcloud-doc.isd.com/document/product/647/53583)