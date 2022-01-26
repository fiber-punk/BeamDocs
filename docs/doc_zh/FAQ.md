#### 1.运行BeamNexus提示"MSVCP140.dll not found" "VCRUNTIME140.dll not found####

有一些Windows系统会提示上述错误，如果出现，请参考如下链接:

https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170

下载最新的C++ Redistributable 安装包。

- [ARM64](https://aka.ms/vs/17/release/vc_redist.arm64.exe)
- [X86](https://aka.ms/vs/17/release/vc_redist.x86.exe)
- [X64](https://aka.ms/vs/17/release/vc_redist.x64.exe)

#### 2. 我的BeamNode无法连接wifi,是什么原因?

可能的原因:

- SD卡配网失败,BeamNexus没有使用管理员权限运行，导致写SD卡失败
- BeamNode只支持2.4G网络
- 距离路由器太远，wifi信号太弱

#### 3. BeamNode支持哪些机型?

这个取决于您的打印机的主板的USB转串口实现的方式。 目前BeamNode支持的串口转USB方式包含如下:
- CH340/CH341
- FT232
- CP2102
- STM32 CDC USB Device

需要注意的是。 BeamNode目前只测试了Marlin固件，Pursa的固件还没有测试过。
此外，需要确定您打印机的USB串口波特率是多少，需要在上位机上设置对应的波特率值。

#### 4. BeamNode可以接哪些传感器?

BeamNode提供了2个GPIO口，一个I2C和一个串口，目前官方支持的传感器只有断料传感器。 
后续会增加声音，陀螺仪等各种传感器。 您可以关注我们的github源码，获取更多信息。

#### 5. 为什么我的局域网搜不到我的Beam设备?

请确定您的PC处在的网络是否和Beam设备在同一个局域网内。 如果不是同一个局域网，需要您手动指定Beam设备的IP。 相关说明参考QuickStart中连接网络的说明。

此外，如果您的电脑使用了VPN，也可能会影响BeamNexus搜索设备

#### 6. 为什么BeamNexus无法发送邮件?

有两个原因:
- 请检查谷歌邮箱账号是否开启了未认证设备登录许可,参考QuickStart中的说明
- 使用VPN也可能导致BeamNexus无法发送邮件
- 您的防火墙设置了BeamNexus无法发送邮件。

#### 7. BeamNuxus的本地推理功能导致crash?
如果您选择了Openvino来进行本地推理，但是您的PC电脑不是Intel的，且早于6代处理器，那么就会出现异常。此时，建议您使用纯CPU来指令来进行推理。




