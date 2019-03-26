#Sony Xperia XZ1 G8341 解锁+恢复DRM+刷入Recovery +刷入Boot.img + Magisk安装

##硬件准备
1. 一根优质数据线（可以非原装）
2. 一台可以全局FQ的Windows PC
3. 已经退出google账号或恢复出厂设置的该机型机子

##软件准备
1. google的ADB驱动即`android_winusb.inf`（Sony的官方的ADB驱动无法安装）
2. google的[ADB工具](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
3. Xperifix 最新版本（收费软件不给链接了，度盘搜索是可以找到分享的）
4. Recovery推荐[recovery9cryptfs15-1omni8-1.img](https://androidfilehost.com/?fid=11410963190603845086)by [oF2pks](https://forum.xda-developers.com/xperia-xz1/development/recovery-twrp-3-2-1-t3727602/page12)
5. [Boot.img](https://mega.nz/#F!plw2kCaJ!GAX167ZVKSnZm9zbHsJ-jw)根据自己机型选择 by [janjan]{https://forum.xda-developers.com/xperia-xz1/development/kernel-sony-xz1-23-january-2018-t3739586}
6. [Magisk Manager](https://magiskmanager.com/)

#步骤
##步骤1：申请解锁码
在拨号界面输入 *#*#7378423#*#* 打开菜单;  
选择 Service info > Configuration，查看 Rooting status 状态;  
当 Bootloader unlock allowed 为 Yes 表示可解锁，No 表示不可解锁;  
确认为 Yes 就可以继续往下！否则请关闭本教程。  
打开：系统 > 关于手机 > 连续点击版本号进入 开发者模式;  
打开：系统 > 开发者选项 > 打开 OEM解锁；（若提示 请连接到互联网或与您的运营商联系，请给手机设置锁屏密码或图案或FQ，稍等并重新打开尝试开启。）  
以下步骤建议全程开启FQ模式;  
打开索尼解锁码[申请页面](https://developer.sonymobile.com/unlockbootloader/);  
填写IMEI号码，拨号界面输入 *#06# 弹出IMEI，填写第一个即可，同意条款和风险，提交;  
记住解锁码（重要！）  
##步骤2：给电脑安装ADB驱动
1. 下载并安装Android Studio
2. 在Android Studio里面安装AndroidSDK
3. 将手机关机，等待10秒左右，按住音量加不放，同时插入数据线，等待手机“●”蓝色指示灯亮起；
此时已经进入Fastboot模式；（屏幕不会显示任何东西，黑屏，正确。）
接下来手动安装驱动，打开电脑设备管理器；（按 WIN+R > 输入 devmgmt.msc > 运行。）
找到 感叹号设备 Android，右键更新驱动程序；
4. “浏览我的计算机以查找驱动程序文件”>“让我从计算机上的可用驱动程序列表中选取”`C:\Users\用户\AppData\Local\Android\Sdk\extras\google\usb_driver`
5. 下一步，完成  

##步骤3：解锁Bootloader
###按 WIN+R > 输入 CMD > 运行，依次输入以下命令：
```
Z: 回车（Z为ADB工具所在磁盘符，自行更改为自己的盘符）
CD 你的adb.exe路径 （例：CD :C:\Users\用户\Downloads\SonyXZ1\platform-tools) 回车（CD 后面改为你的路径）
fastboot devices
fastboot oem unlock 0x<insert your unlock code> //刚刚获得的解锁码
```
##步骤4：步骤4：修复DRM+Root
1. 和刚刚一下操作，手机进入Fastbot模式
2. 以管理员身份打开Xperifix v3.2
3. 选择recovery9cryptfs15-1omni8-1.img和magisk.zip
4. 点击 FIX my device ，软件会自动刷入TWRP进入Recovery并刷入DRM内核和Root管理Magisk，
全程无需手动操作，也不要操作，然后等待重启，成功！！！是不是很简单？！
赶快开机测试相机和X-Reality吧！！！干杯！！！  

##步骤5：检查是否成功（！重要）
1. 手机关机，音量-键 和 电源 一起按住，当手机振动的时候松开电源按键，音量-键一直按住，如果成功进入了TWRP Recovery，那么就刷入成功了，跳到3. ，如果没有成功，那么继续看2.
2. 么得办法，我并不会刷入TWRP Recovey，只是记录我自己的这次刷机……
3. 打开手机，安装Magisk Manager，查看Magisk v18是否成功安装，成功就结束了呀，如果没有，继续看步骤6

##步骤6：刷入boot.img
0. 将boot.img放到platform-tools文件夹
1. 像之前一样进入fastboot，并CD到adb.exe所在位置
2. - adb reboot bootloader
3. - fastboot devices
4. - fastboot devices
5. - fastboot flash boot boot.img
6. 关机，进入TWRP Recovery，刷入Magisk.zip
7. 全部完成  
  
  
参考自：作者Z的[索尼 Sony Xperia XZ Premium G8141/G8142 – 解锁BootLoader + 恢复DRM + Root 详细教程](http://www.hwangleungfai.com/索尼-sony-xperia-xz-premium-g8141g8142-解锁bootloader-恢复drm-root-详细教程/)



