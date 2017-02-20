##MyBatis

###Mac下配置MySQL
* 首先下载dmg文件，安装，千万要记住原始的root密码；
* alias mysql=/usr/local/mysql/bin/mysql
* alias mysqladmin=/usr/local/mysql/bin/mysqladmin
* 改变root密码的方法：mysqladmin -u root -p'原始密码' password '新密码'；虽然这种方法并不是最安全的


###Java连接Mysql
* driver使用maven的话会改变：com.mysql.cj.jdbc.Driver
* url也要改变，将ssl连接设置为false：jdbc:mysql://localhost:3306/your-database?useSSL=false
* 存在web所在时区与数据库时区不一致的原因，即timezone错误：serverTimezone=UTC
* url=jdbc:mysql://localhost:3306/your-database?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=UTC

###Intellij idea Java目录是不会编译xml文件的
Mybatis XML 配置失效<br>
解决方法：在pom下增加如下：<br>
```Xml
<build>
    <resources>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.xml</include>
        </includes>
      </resource>
    </resources>
</build>
```

###配置logj
* xml配置文件
```Xml
log4j.rootLogger=info,appender1,appender2
log4j.appender.appender1=org.apache.log4j.ConsoleAppender
log4j.appender.appender2=org.apache.log4j.FileAppender
log4j.appender.appender2.File=D:/logFile.txt
log4j.appender.appender1.layout=org.apache.log4j.TTCCLayout
log4j.appender.appender2.layout=org.apache.log4j.TTCCLayout
```
* Java程序中添加：PropertyConfigurator.configure("src/log4j.properties");

###Junit配置
* cltrl+Shift+T快捷键
