#This section will include some Java Knowledge

###Eclipse配置指南
* 打开Window的Preferences，将General-Appearance的主题改成暗色主题
* 修改General-Colors and Fonts-Basic-text Font的字体和大小
* Java-Editor-Content Assist，将代码提示改为@abcdefghijklmnopqrstuvwxyz.
* 常用快捷键：
    * sysout：System.out.println()
    * Ctrl + D：删除行
    * Alt + Shift + R: Rename


###Tomcat配置
* 下载zip文件，这样可以免安装，直接解压就可以使用了
* 进行换进变量的配置：TOMCAT_HOME：tomcat bin所在位置
* CLASSPATH添加%TOMCAT_HOME%\BIN

##反射
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
