Protocal
======

###protocol serialize
* 紧凑模式：raw data，除了数据本身外，没有一点额外冗余信息
* 可扩展：添加协议version信息
* 更好的可扩展性：为每一个字段添加一个额外信息——tag
* 长度可变：使用三元组编码，简称TLV编码；Tag，Length，Content
* 自解释性：TT[L]V（tag，type，length，value）
* jce协议增加特性：
  * 压缩数据类型长度
  * require/optional（建议避免使用require，optional字段可以指定默认值）
  * 0<=tag<=255，占用4比特大小
  * out表示输出参数

###jce结构
* module
* 常量定义
* 枚举定义
* struct定义
* Req请求
* Resp响应

##网络协议分析
* 基于Fiddler的HTTP/HTTPS协议分
  * Fiddler2 是一个使用本地 127.0.0.1:8888 的 HTTP 代理，任何能够设置 HTTP 代理为 127.0.0.1:8888 的浏览器和应用程序都可以使用 Fiddler。
* 基于Wireshark的TCP/HTTP协议深入分析
  * 使用WinPCAP作为接口，直接与网卡进行数据报文交换
  * 在显示筛选编辑框中输入“tcp”或者“udp”，回车
  * 使用Wireshark分析ARP协议：在显示筛选编辑框中输入“arp”，回车
  * 使用Wireshark分析ICMP协议：在显示筛选编辑框中输入“icmpv6”，回车
  * 使用Wireshark分析IP协议：在显示筛选编辑框中输入“ip”，回车
* windows下好用的终端模拟器：cmder，下载地址：[http://cmder.net]
