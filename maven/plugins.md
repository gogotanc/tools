## Maven 日常插件使用

使用 Maven 的过程中，常用的插件。

### Apache Maven Compiler Plugin

Maven 自带的编译时默认使用的 source 和 target 版本是 1.5，如果项目中使用了 Java 的一些新版本中的特性，编译的时候是会出错的，所以需要配置编译插件。

pom.xml 文件内容如下：

```
<project>
  ...
  <build>
    <pluginManagement>
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
    </pluginManagement>
  </build>
  ...
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

