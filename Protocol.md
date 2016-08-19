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
