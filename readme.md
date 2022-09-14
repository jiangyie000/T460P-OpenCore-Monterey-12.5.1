# T460P OpenCore Monterey 12.5.1

* 基于[T460p-OpenCore](https://github.com/Danny-Z/T460p-OpenCore)安装，版本为macos bigsur 12.5.1，自用，几乎完美。（指纹，随航，HDMI外接显示器内置屏幕黑屏）

## 相关资料		

最佳底包：[T460p-OpenCore](https://github.com/Danny-Z/T460p-OpenCore)

最佳参考：[GitHub - CLAY-BIOS/Lenovo-ThinkPad-T450s-Hackintosh-OpenCore: 99%接近于白苹果的完美黑苹果。](https://github.com/CLAY-BIOS/Lenovo-ThinkPad-T450s-Hackintosh-OpenCore)

最佳合集：[GitHub - daliansky/OC-little](https://github.com/daliansky/OC-little)

最佳问题解决：[关于笔记本开启hidpi后，睡眠唤醒半屏、雪花点闪屏的解决办法](https://bbs.pcbeta.com/viewthread-1832969-1-1.html)



- [@Sniki](https://github.com/Sniki?tab=repositories)
- [@benbender](https://github.com/benbender/x1c6-hackintosh/blob/experimental/EFI/OC/dsl/SSDT-BATX.dsl) 新一代电池补丁。
- [@zhen-zen](https://github.com/zhen-zen) for YogaSMC。
- [@daliansky](https://github.com/daliansky/OC-little) 各种ACPI热补丁样本。
- [@xzhih](https://github.com/xzhih) 一键开启Hi-DPI。
- [@cholonam](https://github.com/cholonam/Sinetek-rtsx) [读卡器修复](https://github.com/cholonam/Sinetek-rtsx/pull/18)
- [@MSzturc](https://github.com/MSzturc/ThinkpadAssistant) ThinkPad助手。
- [@zxystd](https://github.com/OpenIntelWireless/itlwm) Intel Wi-Fi Drivers for macOS。
- [@0xFireWolf](https://github.com/0xFireWolf/RealtekCardReader) 读卡器驱动。
- 

## 工作情况

| *项目*        | *工作与否* | *备注*                                                       |
| ------------- | ---------- | ------------------------------------------------------------ |
| CPU变频       | √          | 14档, i7-6700HQ, 0x191b0000，显卡HD530                       |
| SMBios        | √          | MBP13,3                                                      |
| 🔊声卡         | √          | ALC-293, alcid=28                                            |
| 显卡          | √          | Intel HD530 @1080p                                           |
| HDMI          | √          | 屏蔽独显后无法使用，不屏蔽独显睡眠又无法唤醒，***目前暂无解决办法*** |
| miniDP        | √          | 屏蔽独显后无法使用，不屏蔽独显睡眠又无法唤醒，***目前暂无解决办法*** |
| 有线网卡      | √          |                                                              |
| WiFi          | √          | Inter无线网卡，AirportItlwm.kext驱动                         |
| 蓝牙          | √          | Inter蓝牙驱动，IntelBluetoothFirmware.kext、IntelBluetoothInjector.kext、IntelBTPatcher.kext |
| 📹摄像头       | √          |                                                              |
| USB-3.0       | √          | 速度： 最大 5 Gb/秒                                          |
| 🔋电池         | √          |                                                              |
| 亮度快捷键    | √          | F5,F6(Fn)，采用[OC-little](https://github.com/daliansky/OC-little)的亮度补丁，注意改名问题 |
| 声音快捷键    | √          | F2,F3                                                        |
| Fn其余快捷键  | √          | 采用[YogaSMC]([zhen-zen/YogaSMC: ACPI driver for OEM hardware. (github.com)](https://github.com/zhen-zen/YogaSMC))补丁<br />使用方法：[关于YogaSMC 的使用](https://github.com/daliansky/XiaoXinPro-13-hackintosh/issues/139) |
| 触摸板        | √          |                                                              |
| HIDPI         | √          | 1920*1080，开启超过900的hidpi会花屏，采用缓冲帧补丁解决。 <br />https://bbs.pcbeta.com/viewthread-1832969-1-1.html |
| 睡眠💤唤醒     | √          | 🔌电源键，睡眠快捷键：Fn + 4，启用停用睡眠                    |
| 盒盖睡眠💤唤醒 | √          |                                                              |





## 存在问题

* 指纹不可用。
* 随航Sidecar暂不可用
* 扩展坞未尝试过，有需要的可以自行测验
* 屏蔽独显与外接HDMI无法共存，不屏蔽独显睡眠又无法唤醒，暂时无法解决。



## 安装步骤

* *下载bigsur系统，EFI文件，准备balenaEtcher，DiskGenius工具*
* 下载bigsur，[黑苹果镜像 macOS 11.6 Big Sur 正式版(20G165)](https://heipg.cn/macos/macos-11-6-big-sur-20g165-oc-073-clover-r5139-wepe.html)

* 下载balenaEtcher，准备一块16G+的U盘（最好是32G以上，否则可能写不进去），插入后写入bigsur镜像

  <img src="https://www.jianguoyun.com/c/dl-file/20229419229.png?dt=rhomrh&sd=dhzay&kv=amlhbmd5aWUwMDBAMTYzLmNvbQ&vr=1&ud=jOujUiymAMV9RUN_eZgPcyXzcZUcCbpFaYixd4bwEfQ" alt="image-20220904190222390" style="zoom:50%;" />

* 下载本仓库中的EFI文件，准备替换
* 用DiskGenius将U盘里的OC分区挂载并拷贝到电脑上备份
* 将上一步EFI/OC/Kexts文件夹与config.list文件替换到U盘中
* 完成后的U盘插入新电脑，选择install macos bigsur，执行安装（这一步可能出现各种问题，在网上找答案）
* 完成安装后，进入系统，执行其余修复



## 问题解决

  1. **Inter无线网卡联网**：下载AirportItlwm.kext驱动，拷贝到Kexts文件夹，添加进OC

  2. **蓝牙补丁**：IntelBluetoothFirmware.kext、IntelBluetoothInjector.kext、IntelBTPatcher.kext

  3. **睡眠无法唤醒（实际唤醒了，但不能亮屏）**：屏蔽独显，两种方法：[OC-little](https://github.com/daliansky/OC-little)，下面介绍配置法

     ①：OC引导用OC Configuration打开（Windows可用OCAT）

     - `DeviceProperties\Add\PciRoot(0x0)/Pci(0x2,0x0)` 添加

       ```
       disable-external-gpu  01000000
       ```

     - 添加引导参数

       ```
       boot-args             -wegnoegpu 
       ```

   

​          ②：启用SSDT-DGPU.aml，这种屏蔽独显的同时可调节亮度（系统调节，不能使用快捷键）



4. **睡眠唤醒后1/4屏、花屏问题**：开启分辨率较高的hidpi后（一般是超过900），睡眠会出现1/4屏问题，再睡眠一次会出现雪花花屏问题。 

​      ①：将hidpi开启到1440*810，这算是1080P屏幕比较好的状态

​      ②：[关于笔记本开启hidpi后，睡眠唤醒半屏、雪花点闪屏的解决办法 ](https://bbs.pcbeta.com/viewthread-1832969-1-1.html)，这种办法能开启1080P



5. **亮度补丁**

​		补丁：https://github.com/daliansky/OC-little， 05/05-2
​		操作：https://bbs.pcbeta.com/viewthread-1840044-1-1.html



6. **Fn快捷键**

​		ThinkPad解决方法：YogaSMC补丁，使用方法：https://github.com/daliansky/XiaoXinPro-13-hackintosh/issues/139

- 注：ThinkPad用ThinkPad那个补丁，实现功能：
- Fn功能键开启与关闭 ( 键盘上第一行的功能键几乎能工作 )。
- 键盘灯启动与关闭
- 性能模式切换
- CapsLk 锁



其他解决办法（SSDT，键盘映射补丁修补）

​        原理：https://www.mfpud.com/topics/1070/ 转载自 https://blog.skk.moe/categories/%E9%BB%91%E8%8B%B9%E6%9E%9C/

​        操作：ThinkPad全线键盘的fn快捷键是通用的，因此找一个其他版本的ThinkPad做好的SSDT-KBD.asl文件修补即可。 

​        同时在系统偏好设置中设置对应功能的快捷键（不设置对应功能的快捷键，fn可用，但无法操作系统）



7. **屏蔽独显后无法外接显示器**

暂时还未实践，解决方法：https://www.it610.com/article/1279831208980660224.htm



# 版本升级

### 20220914

- 升级oc版本至0.8.4
- 升级各种驱动版本
