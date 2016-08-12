##MyBatis

###Mac下配置MySQL
* 首先下载dmg文件，安装，千万要记住原始的root密码；
* alias mysql=/usr/local/mysql/bin/mysql
* alias mysqladmin=/usr/local/mysql/bin/mysqladmin
* 改变root密码的方法：mysqladmin -u root -p'原始密码' password '新密码'；虽然这种方法并不是最安全的


###Java连接Mysql
* driver使用maven的话会改变：com.mysql.cj.jdbc.Driver
* url也要改变，将ssl连接设置为false：jdbc:mysql://localhost:3306/your-database?useSSL=false
* 存在web所在时区与数据库时区不一致的原因，即timezone错误

###Intellij idea Java目录是不会编译xml文件的
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
