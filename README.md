﻿# This section will include some Java Knowledge

### Eclipse配置指南
* 打开Window的Preferences，将General-Appearance的主题改成暗色主题
* 修改General-Colors and Fonts-Basic-text Font的字体和大小
* Java-Editor-Content Assist，将代码提示改为@abcdefghijklmnopqrstuvwxyz.
* 常用快捷键：
    * sysout：System.out.println()
    * Ctrl + D：删除行
    * Alt + Shift + R: Rename


### Tomcat配置
* 下载zip文件，这样可以免安装，直接解压就可以使用了
* 进行环境变量的配置：TOMCAT_HOME：tomcat bin所在位置
* CLASSPATH添加%TOMCAT_HOME%\BIN

## 反射
* 反射机制是在运行状态中
* 动态获取类或对象的属性和方法，需提前获取这个类的Class对象
* 获取class文件对象
      * 对象的getClass（）方法
      *  类的静态属性：类名.class
      *   Class类的静态方法：Class.forName(String 类名)

| Class        | 描述           |
| -------------            |:-------------:          |
|java.lang.Class	| 描述编译后的class文件的对象 |
|java.lang.reflect.Constructor	| 用于描述构造方法 |
|java.lang.reflect.Field	| 描述字段（成员变量） |
|java.lang.reflect.Method	| 描述成员方法 |


## JVM
* Java虚拟机是一个可以执行Java字节码的虚拟机进程

<br>    Java中static方法不能被覆盖，因为方法覆盖是基于*运行时动态绑定*的，而static方法是编译时静态绑定的

> 同步方法和同步代码块的区别
>>同步方法默认用this或者当前类class对象作为锁；
>> 同步代码块可以选择以什么来加锁，比同步方法要更细颗粒度，我们可以选择只同步会发生同步问题的部分代码而不是整个方法；

## ClassLoader
* 将Class加载到JVM中
* 审查每个类应该由谁加载
* Class字节码重新解析成JVM统一要求的对象格式
* ClassLoader是一个抽象类，有defineClass，findClass，loadClass和resolveClass方法
* 要想实现自己的ClassLoader，一般继承URLClassLoader这个子类
* ClassLoader采用上级委托接待机制

### 字符格式化
* System.out.println("%d %f", x, y);
* System.out.printf("%d %f", x, y);
* java.util.Formatter;
* String.format("%d %f", x, y);

### 正则表达式

|符号|	说明|	符号|	说明|	符号|	说明|
| ------------- |:-------------: | ------------- |:-------------: | ------------- |:-------------: |
|^	|一行的起始|	\W	|非字母数字|	\w	|字母数字|
|$	|一行的末尾|	\D	|非数字|	\d	|数字|
|+	|>=1	|?	|0或1次	|*	|任意次|
|.	|非换行任意字符|	[^x]	|非X字符的任意字符|	\S	|任意非空白符字符|

## Java内存存储
* 栈(Stack) ：存放基本类型的变量数据和对象的引用，但对象本身不存放在栈中，而是存放在堆（new 出来的对象）或者常量池中（字符串常量对象存放在常量池中）
* 堆(heap)：存放所有new出来的对象和数组。
* 常量池(constant pool)：在堆中分配出来的一块存储区域，存放储显式的String常量和基本类型常量(float、int等)。另外，可以存储不经常改变的东西(public static final)。常量池中的数据可以共享。
* 静态存储：存放静态成员（static定义的）。

<br>针对接口编程是一种重要的程序思维方式，这种方式不仅可以复用代码，还可以降低耦合，提高灵活性，是分解复杂问题的一种重要工具
<br>

## Java 8 Lambda表达式
### 基本语法
- Lambda 的基本结构为 (arguments) -> body
- Stream对象
  - 指的是一组支持串行并行聚合操作的元素，可以理解为集合或者迭代器的增强版。
  - 聚合操作有平均值、最大值、最小值、总和、排序、过滤等。
  - 常见的获取 Stream 的方式
     - 从集合中获取：Collection.stream()、Collection.parallelStream()
     - 静态工厂：Arrays.stream(array)、Stream.of(T …)、IntStream.range()
  - 常用方法：
     - forEach（e -> method）方法：Collection提供了forEach方法，供我们逐个操作单个对象
     - 排序：Collections.sort(array, (o1, o2) -> o1(.getA()) - o2(.getA()))、object collection.stream().sorted((o1, o2) -> o1(.getA()) - o2(.getA())).forEach()
     - 最大、最小值：max（(o1, o2) -> o1(.getA()) - o2(.getA())）、min（）方法
     - filter（）方法：filter（o -> o.getA() > threshold(equals...) + (&&, ||, !)）
     - limit(int)方法截取有限的元素
     - reduce 的函数操作为二元操作符，一个为前面操作的结果，一个为当前元素，reduce 会逐个对 Stream 中的元素执行指定的操作，并返回最终的结果
     - get（）方法获取对象：返回Optional 类，Optional类主要目的是防止产生空指针异常
     - map 方法的作用是依次对 Stream 中的元素进行指定的函数操作，并将按顺序将函数操作的返回值组合到一个新的 Stream 中
     - 重新组织对象结构：map(e -> e.getA()).collect(Collectors.joining(","));
     - 统计信息：返回类型IntSummaryStatistics, DoubleSummaryStatistics, LongSummaryStatistics 包含了 Stream 中的汇总数据；具体使用mapToInt（看返回类型）(Employee(class or object)::getAge(method)).summaryStatistics()

### 六大设计原则
* 依赖倒置原则：高层模块不应该依赖底层模块
* 开闭原则：对扩展开放，对修改关闭
* 单一职责原则：一个类的职责只有一个
* （里式）替换原则：子类必须能够替换父类
* 接口隔离原则：暴露给用户的接口小而完备
* 迪米特法则：一个对象应该对其他对象保持最少了解

## 23种设计模式
### 创建型模式
* 工厂模式：return一个new出来的对象
* 抽象工厂模式：return一堆new出来的对象
* 原型模式：通过copy自己来创建对象
* 单例模式：一个类只有一个实例
* 生成器模式：负责对象的分步创建，由外部实现

### 结构型模式、行为模式
* 策略模式：定义一系列的算法，只要有if/else的地方其实都可以使用策略模式
* 适配器模式：将一个类的接口转换成客户希望的另一个接口；有类适配器和对象适配器
* 模板方法：定义一个操作中的算法的骨架，而将一些步骤延迟到子类中
* 装饰器：动态给对象添加一些额外的职责
* 观察者：定义对象间的一种一对多的依赖关系，修改时通知
