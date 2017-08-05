Android环境搭建
======

### Windows环境下jdk配置：
* JAVA_HOME：jdk安装所在路径
* PATH：添加;%JAVA_HOME%\bin
* CLASSPATH：.;%JAVA_HOME%\lib\tools.jar

### ADB配置：
* android：新建，sdk/platform-tools和tools所在路径
* PATH：添加%android%
* 使用手册：http://adbshell.com
* 常用命令：
    * 查看设备：adb （-d -e -s） devices
    * 安装软件：adb （-s serial number）install 软件所在路径；adb shell pm install (option) 路径
    * 查看所有安装软件：adb shell pm list packages
    * 卸载软件：adb uninstall （option） 软件名；
    * pc数据copy到手机：adb push pc路径 手机路径；反向：adb pull 手机路径 （pc路径）
    * 获取手机序列号：adb get-serialno
    * adb-server关闭与开启：adb kill-server；adb start-server
    * 进入手机系统：adb shell
    * 查看手机软件安装路径：adb shell pm path 软件名
    * 屏幕录制：adb shell screenrecord 路径+文件名；截屏screencap
    * 手机重启及关机：adb reboot；adb shutdown
    * Logcat：adb logcat，adb shell dumpsys， adb shell dumpstate；注：打印东西太多，不好查看，需要设置详细的filter
    * 网络有关：adb shell netstat， adb shell ping（可选参数较多），adb shell ip
