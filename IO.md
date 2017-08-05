IO
======

## File操作常见错误
* windows下的文件分隔符：是/而不是\，（或者使用\\）
* String以.号分割split时，必须使用"\\."，而不能只使用"."，那样得到的数组长度为0
* String以(左括号分割split时，必须使用"\\("，而不能只使用"("，那样得到的数组长度为0

## 文件过滤
```Java
File file = new File("path + file name");
  String[] FileList = file.list(new FilenameFilter() {
      // 文件过滤
      @Override
      public boolean accept(File dir, String name) {
          // 只返回txt后缀的文件
          return name.endsWith(".txt");
      }
```

## 字符流的缓冲区
* 字符流的缓冲区，提高了对数据的读写效率
* 需要流对象，如FileReader，FileWriter
* 写入完成，如想马上看到效果，需手动刷新，调用flush()函数

## 转换流
* InputStreamReader：读取字节流转换成字符流
* OutputStreamWriter：写入字节流转换成写入字符流

## 装饰类
* 装饰类通常会通过*构造方法*接收被装饰的对象，并基于被装饰的对象的功能提供更强的功能
* 装饰与继承的区别：
    * 装饰者模式比继承要灵活，避免了继承体系的臃肿，而且降低了类与类之间的关系
    * 装饰类因为增强已有对象，具备功能和已有的功能相同，只不过提供了更强的功能，所以装饰类和被装饰类通常属于一个体系中的

## Properties
* hashtable的子类，常用于配置文件
* 具备map集合的特点，里面的键值对都是字符串

### Java8 directly read the specific lines
```Java
String line32 = Files.readAllLines(Paths.get("file.txt")).get(32) // small file
// large file
try (Stream<String> lines = Files.lines(Paths.get("file.txt"))) {
    line32 = lines.skip(31).findFirst().get();
}
```
