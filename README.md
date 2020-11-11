# Lenovo XiaoXinPro13 2109&2020 hackintosh


Lenovo XiaoXinPro13 Hackintosh

## 电脑配置
|规格 | 详细信息|
|:-: | :-:|
|电脑型号| 联想小新pro13 2019笔记本电脑 |
|操作系统| macOS Big Sur 11.0.1（20B28）|
|处理器| 英特尔 酷睿 i7-10710U |
|内存| 16GB板载无法更换 |
|硬盘|原装 ~~三星981A 512GB~~ 更换为 三星970 evo 1TB |
|显卡| Intel HD Graphics CFL CRB（UHD620）|
|显示器| 13.3 英寸 IPS 2560x1600 华星光电 |
|声卡| Realtek ALC257 |
|网卡| 原装~~Intel AX201NGW~~ 更换为 BCM94360CS2 |

## 使用说明【请仔细阅读】

### 注意

- 强烈建议不要使用`OpenCore Configurator`来修改`config.plist` `OpenCore Configurator`更新缓慢与`OpenCore`版本不匹配，推荐使用`ProperTree`   
  - Win下修改`config.plist`请下载群文件`ProperTree中文版-WIN`来修改`config.plist`
- 小新由于安装过程中触摸板可能无法驱动，使用U盘安装macOS会占用仅仅一个USB接口,建议安装之前先买个usb拓展,用于插入鼠标,来进行安装步骤选项设定。
- 安装或更新系统完成后请使用`终端`输入`sudo kextcache -i /`清理缓存并重启，触控板才能正常使用

### BISO设置 【重要】

- 需要更新`BIOS`【重要】
  - [`BIOS`下载](https://pan.baidu.com/s/1bNwPFp6RHZvGNAaPx_IcJA) 密码: dpoe

- 解锁 `DVMT` 、 `CFG` 【或参考@Donald 《修改DVMT Pre-Allocated数值方法》】
  - `DVMT` =`64M`;位置:`Advanced` ->` System Agent` -> `Graphics Configura` -> `DVMT Pre- Allocated` 【重要】
  - `CFG` =`disable`;位置:`Advanced` -> `Power Performanc` -> `CPU Power Manage` -> `CPU Lock Configura`【重要】
  
- `Security `【重要】
  - `Intel Platform Trust Technology `= `Disable`
  - `Intel SGX Control` = `Disable` 【建议】
  - `Secure Boot` =`Disable`

### 关闭触摸板快捷键

- 组合键: FN+F6

### 唤醒方法

- 电源键

### 不正常工作

- ~~睡眠~~ (小新PRO13不能真正睡眠，可以仿真睡眠。唤醒比较困难，`OC` 下唤醒方法是：`电源键`唤醒)
- 声卡MIC(`暂时解决方法`：启动台-声音-输入：手动切换到“`外接可用麦克风设备`”)
<details>
<summary>关于 小新PRO13(2019/2020/13S Intel版本) 没有S3睡眠延展</summary>
<p>D0 就是正常工作状态，S0 是 D0 的电源管理，S0睡眠应该是不存在的，说 S0 睡眠，本质就是 D0 状态下进入了空闲，所以有了空闲状态下的电源管理，这个机器没有 S3睡眠，没有设计相关硬件</p>
<p>但因 ACPI 有了 S3才导致苹果试图进入睡眠，但因缺少必须的硬件最终失败，对于 Windows 不妨碍</p>更详细的说明移步<a href="https://github.com/daliansky/OC-little/tree/master/01-%E5%85%B3%E4%BA%8EAOAC" target="_blank">OC-little</a>
<p>实测选择省电的SSD可有效延长待机时间。如：三星970EVO+BCM94360CS2并使用SleepWithoutBluetoothAndWifi盒盖一小时耗电仅需0.86%，而西数SN750+BCM94360CS2并使用SleepWithoutBluetoothAndWif则需要3%每小时</p>   
</details>

### 哪些可以工作更好
- 开启 [HIDPI](https://github.com/xzhih/one-key-hidpi) 来提升系统UI质量, `可能会出现花屏现象`

### 镜像下载
  
- [[**黑果小兵的部落阁**] :【黑果小兵】原版镜像](https://blog.daliansky.net/categories/下载/镜像/)

### EFI下载

- [OpenCore 正式版](https://github.com/Hush-vv/Lenovo-XiaoXinPro13-Hackintosh/releases)

- [OpenCore 开发版](https://github.com/Hush-vv/Lenovo-XiaoXinPro13-Hackintosh/archive/master.zip)
   
- Clover[请移驾daliansky](https://github.com/daliansky/XiaoXinPro-13-hackintosh)
        
### 感谢
- 本EFI所使用的`ACPI`均来自 @宪武 大佬
- daliansky黑果小兵
- 感谢PS@Donald提供的解锁`DVMT` `CFG lock`工具
- 感谢群友QQ876310253提供的`解锁dvmt及cfglock.docx`教程    
- 感谢群友Dreamn提供的[`SleepWithoutBluetoothAndWifi`](https://github.com/dreamncn/SleepWithoutBluetoothAndWifi)工具        
- @Bat.bat [自动化 OpenCore 编译，每 8 小时刷新一次](https://github.com/williambj1/OpenCore-Factory/releases)
    
    ......

### QQ群
- 小新pro黑苹果 946132482
    
- 小新pro13insyde bios研究交流 635160015
        

### 更新日志  
  
- [Changelog](https://github.com/Hush-vv/Lenovo-XiaoXinPro13-Hackintosh/blob/master/%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97.md)
