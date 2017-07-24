
# Maven 使用说明

`maven` 是 `java` 中优秀的包管理工具。有着各种插件，使用很方便。

### maven 国内镜像

国内的网连接 `maven` 的中央仓库速度很慢，这里安利一发国内的镜像。

```xml
<mirror>
  <id>alimaven</id>
  <name>aliyun maven</name>
  <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
  <mirrorOf>central</mirrorOf>        
</mirror>
```

直接在 `settings.xml` 文件中 `mirrors` 标签下面添加上面的内容即可。

### 新建一个 Java Web 项目

直接运行下面命令

```shell
$ mvn archetype:generate
```

需要稍等下，然后会让你选择和填写相关项目信息，如 `groupId`、`DartifactId` 和版本号之类的,主要是 `archetypeAritifactId` 要选择 `webapp`。

### 跳过测试的命令

使用如下命令进行打包，可以跳过测试阶段。

```shell
$ mvn package -Dmaven.test.skip=true
```

离线打包的时候，有些测试是需要网络连接，于是不能通过，这时就可以使用这个命令。

### 解决构建项目骨架速度奇慢的问题

maven 骨架生成项目速度慢的令人发指，都在 Generating project in Batch mode 等待，Idea 状态显示栏还在不行 running，并没有卡死。查看 debug 信息发现，是 maven 获取 archetype-catalog.xml 导致。

```
-DarchetypeCatalog=internal
```

加上-DarchetypeCatalog=internal 运行参数，archetype-catalog.xml本地获取。

对于intellij idea可以在 Runner 加上该参数。

