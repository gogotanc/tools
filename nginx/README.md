## Nginx 使用说明

Nginx 是一个高性能的 HTTP 服务器和反向代理服务器，也是一个 IMAP、POP3、SMTP 代理服务器。

### 特点

- 高并发：Nginx 支持 50000 个并发连接数的响应；
- 占用内存少：10000 个非活动 HTTP 保持连接占用大约 2.5M 内存；
- 安装简单，配置文件简洁。

### 模块划分

主要有以下几个模块：

- Core : 核心模块
- Events : 事件模块
- HTTP : HTTP模块
- Mail : 邮件模块

## 参考文章

[Nginx 为什么比 Apache 高效：原理篇](http://www.mamicode.com/info-detail-1156329.html)
