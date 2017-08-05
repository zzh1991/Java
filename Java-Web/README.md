Web 开发学习路线
=======

### 建立网站的准备材料
* 域名：推荐在GoDaddy上购买，国内需要去备案，十分麻烦
* GitHub 设置域名
  * 设置A记录，即将域名指向主机IP地址；MX记录为邮件服务器；CNAME：即别名，完成域名映射到其他网址上去
* 空间：存放网页和其他资源
  * 用FTP传输网页文件
  * 网站数据库

### SSH远程登入
* ssh (-p 端口号(默认为22)) username@host(ip地址) 
```
ssh user@ip
# input password

ssh -i key user@ip
```
* 采用了公钥加密，口令登入
  * 远程主机发送公钥
  * 登入密码加密
  * 私钥解密登入密码
* 公钥登入
  * 本地生成自己的公钥和密钥
  * 将公钥传送给远程主机
  * 本机用私钥加密传送回去远程发来的字符串
  * 远程使用事先储存的公钥解密

### 版本控制工具
* git
    * GitHub
* svn：TortoiseSVN

### Java开源库
* 文件处理：apache commons io
* JSON 对象转换：Jackson
* Strman-java：字符串处理
* Dex：数据可视化
* ND4j：科学计算

### 改变java版本
* Intellij Idea 中 project structure 可以修改 project language level 版本，另外 module 的 language level 也要修改
* setting 中的 compiler 也要修改成当前的java版本号
* try catch shortcut： Ctrl-Alt-T, 6


## Java Spark framework
* 创建一个 maven 工程，并添加依赖关系 sparkjava，slf4j
* URL 中的参数可以使用：name 或者 *splate 数组代替
* port（4567），默认的端口号为 4567，内置的 web server 为 jetty
* Websocket：一种协议，在TCP连接上提供全双工的通信，只适用嵌入的 jetty 容器

[视频链接] (https://www.youtube.com/watch?v=sBzRwzY7G-k)
