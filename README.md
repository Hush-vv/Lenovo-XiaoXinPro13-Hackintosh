# Lenovo XiaoXinPro13 hackintosh


Lenovo XiaoXinPro13 Hackintosh

## 电脑配置
|规格 | 详细信息|
|:-: | :-:|
|电脑型号|联想小新pro13 笔记本电脑|
|操作系统|macOS Catalina 10.15.x |
|处理器|英特尔 酷睿 i7-10710U|
|内存|16GB板载无法更换|
|硬盘|原装 三星981A 512GB 更换为 西数SN750 1TB |
|显卡|Intel HD Graphics CFL CRB|（UHD620）|
|显示器|13.3 英寸 IPS 2560x1600 华星光电|
|声卡| Realtek ALC257|
|网卡| 原装Intel AX201NGW更换为 DW1820A|

      
## 镜像下载
  
   - [[**黑果小兵的部落阁**] :【黑果小兵】原版镜像](https://blog.daliansky.net/categories/下载/镜像/)

## EFI下载

   - [OpenCore](https://github.com/Hush-vv/Lenovo-XiaoXinPro13-Hackintosh/archive/master.zip)
   
   - Clover[请移驾daliansky](https://github.com/daliansky/XiaoXinPro-13-hackintosh)

# 使用说明

## 注意

- 强烈建议不要使用`OpenCore Configurator`来修改`config.plist` `OpenCore Configurator`更新缓慢与`OpenCore`版本不匹配，推荐使用`ProperTree`   
- 小新由于安装过程中触摸板可能无法驱动，使用U盘安装macOS会占用仅仅一个USB接口,建议安装之前先买个usb拓展,用于插入鼠标,来进行安装步骤选项设定。
- 安装或更新系统完成后请使用`终端`输入`sudo kextcache -i /`清理缓存并重启，触控板才能正常使用

## BISO设置

- ### BIOS 版本:  `CLCN32WW`

   -  `Fn+F2`进入`BIOS`,
   -  先查看 `Information`：`Secure Boot` 是否为 `Disabled`;
   -  如果 `Secure Boot` 是 `Enabled`，选择左边到 `Security`： 设置 `Secure Boot` 为 `Disabled`;
   -  `Fn+F10` 保存设置

## 配置config【重要】

- ### 已修改BIOS`DVMT`机器可删除以下内容

  - `Kernel` \ `Patch` \ `iten0`
  - `Kernel` \ `Patch` \ `iten1`
  - `PciRoot(0x0)/Pci(0x2,0x0)`\ `framebuffer-fbmem` = `00009000`
  - `PciRoot(0x0)/Pci(0x2,0x0)`\ `framebuffer-stolenmem` = `00003001`
  
- ### 已解锁BIOS`CFG LOCK`机器可删除以下内容
  
    - `Kernel` \ `Quirks` \ `AppleCpuPmCfgLock`=`NO`
    - `Kernel` \ `Quirks` \ `AppleXcpmCfgLock`=`YES`
    - `Kernel` \ `Quirks` \ `AppleXcpmForceBoost`=`NO`
    - `UEFI` \ `Quirks` \ `IgnoreInvalidFlexRatio`=`YES`
    
 - ### 使用`1820A`网卡的驱动蓝牙和WI-FI将这些`YES`即可
 
    - `Kernel` \ `Add` \ `18`\ `Enabled`=`YES`
    - `Kernel` \ `Add` \ `19`\ `Enabled`=`YES`
    - `Kernel` \ `Add` \ `20`\ `Enabled`=`YES`
    - `Kernel` \ `Add` \ `21`\ `Enabled`=`YES`
 
- ### 部分`i5`机型可删除以下内容

  - `Kernel` \ `Patch` \ `iten0`
  - `Kernel` \ `Patch` \ `iten1`
  - `Kernel`\ `Emulate`\ `Cpuid1Data`
  - `Kernel`\ `Emulate`\ `Cpuid1Mask`  

## 安装失败注意

 - ### 强烈建议解锁BIOS`CFG LOCK` `DVMT`以避免安装时卡住。解锁方法请参考群文件`小新PRO13修改DVMT说明`
 
 - ### 安装系统时请在BIOS中禁用无线网卡，安装成功后在打开。避免因网卡问题导致安装失败
    - 一些网卡需要屏蔽针脚，方法请自行百度
    
- ### `CPU多线程(BIOS Hyper)`的`开` 与`关` 和 `config`的`AppleXcpmExtraMsrs`设置不一致时可能导致`-v`引导失败，可尝试

    - BIOS中打开超线程并将`config`的`AppleXcpmExtraMsrs`设置为`YES`
    - BIOS中关闭超线程并将`config`的`AppleXcpmExtraMsrs`设置为`NO`
   
- ### 安装`macOS Catalina10.15.4`过程中可能无法驱动核显，导致引导失败重启回引导页面，临时解决方法
  
  - [`DeviceProperties` \ `Add` \ `PciRoot(0x0)/Pci(0x2,0x0)`\ `AAPL,ig-platform-id`=`12345678`](https://github.com/daliansky/XiaoXinPro-13-hackintosh/issues/16)安装成功后恢复即可

## 关闭触摸板快捷键
- 
    组合键: FN+F6

## 唤醒方法
 -
    电源键

## 已知问题
 -
    内置MIC不工作
 -
   使用耳机时，睡眠唤醒后声音输出不正常。目前解决办法是进入`声音偏好设置`切换一下麦克风即可
 -
    耳机孔不支持线控
    
    
## 感谢
-
    本EFI所使用的`ACPI`均来自 @宪武 大佬
    
-   daliansky黑果小兵

-   感谢PS@Donald提供的解锁`DVMT` `CFG lock`工具

-
    感谢群友QQ876310253提供的`解锁dvmt及cfglock.docx`教程
    
-
    感谢群友Dreamn提供的[`SleepWithoutBluetoothAndWifi`](https://github.com/dreamncn/SleepWithoutBluetoothAndWifi)工具
        
-    
    @Bat.bat [自动化 OpenCore 编译，每 8 小时刷新一次](https://github.com/williambj1/OpenCore-Factory/releases)
    
    ......

## QQ群
- 
    [小新pro黑苹果 946132482](https://jq.qq.com/?_wv=1027&k=5XoGay4)（已满）
    
-   
     [小新pro13insyde bios研究交流 635160015](https://jq.qq.com/?_wv=1027&k=5R7Zcci)
        

## 更新日志  
  
  - [Changelog](https://github.com/Hush-vv/xiaoxing-pro13/blob/master/%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97.md)
