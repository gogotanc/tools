## Maven 日常插件使用

使用 Maven 的过程中，常用的插件。

### Apache Maven Compiler Plugin

Maven 自带的编译时默认使用的 source 和 target 版本是 1.5，如果项目中使用了 Java 的一些新版本中的特性，编译的时候是会出错的，所以需要配置编译插件。

pom.xml 文件内容如下：

```
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.7.0</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
          <encoding>UTF-8</encoding>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

配置完成后，会自动绑定编译阶段，使用的 source 和 target 版本就是配置的版本了。

编译源码：

```shell
$ mvn compile
```

编译测试源码：

```shell
$ mvn test-compile
```
参考文章：

[Apache Maven Compiler Plugin](https://maven.apache.org/plugins/maven-compiler-plugin/)

### Exec Maven Plugin 运行插件

在编写普通的 Java 程序的时候，手动 java 来运行很麻烦，于是用到这个插件来简化运行。

pom.xml 文件配置如下：

```propertites
<plugin>
  <groupId>org.codehaus.mojo</groupId>
  <artifactId>exec-maven-plugin</artifactId>
  <version>1.2.1</version>
  <executions>
    <execution>
      <id>run-server</id>
      <goals>
        <goal>java</goal>
      </goals>
    </execution>
    <configuration>
      <mainClass>org.test.App</mainClass>
      <arguments>
        <argument>arg1</argument>
      </arguments>
      <systemProperties>
        <systemProperty>
          <key>property</key>
          <value>value</value>
        </systemProperty>
      </systemProperties>
    </configuration>
  </executions>
</pulgin>
```

或者使用在命令中添加 MainClass 和参数信息：

```shell
$ mvn exec:java -Dexec.mainClass="org.test.App" -Dexec.args="arg1 arg2"
```

参考文章：

[Usage](https://gist.github.com/zbigniewTomczak/4241451)
[Exec Maven Plugin](http://www.mojohaus.org/exec-maven-plugin/)
