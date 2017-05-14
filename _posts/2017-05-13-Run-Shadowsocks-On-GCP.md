---
layout: post
title: Run Shadowsocks Server on Google Cloud Platform
description: "在谷歌云平台的 VM 实例上搭建 shadowsocks 服务."
date:   2017-05-13 22:06:31
tags: ["Shadowsocks", "Google Cloud Platform"]
categories: ["Network"]
comments: true
---



## 创建 VM 实例

一个 f1-micro 微型的实例跑 Shadowsocks 就足够了，系统选个自己熟悉的 Linux，防火墙要允许 HTTP 和 HTTPS 流量，其他保留默认就好。另外，美国区的 f1-micro 实例是永久免费的。

## 安装 Shadowsocks 并启动 ssserver

实例启动后"在浏览器窗口中打开"，安装 shadowsocks：

```shell
sudo apt-get install python-pip
sudo pip install shadowsocks
```

shadowsocks 安装成功后创建配置文件 `/etc/shadowsocks.json`，内容如下：

```json
{
    "server":"0.0.0.0",
    "server_port":8388,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"barfoo!",
    "timeout":300,
    "method":"aes-256-cfb"
}
```

各配置项的解释可以去看 [Wiki](https://github.com/shadowsocks/shadowsocks/wiki/Configuration-via-Config-File)，密码记得改了。接下来就可以启动 shadowsocks server 了：

```shell
sudo ssserver -c /etc/shadowsocks.json -d start # 启动
sudo ssserver -c /etc/shadowsocks.json -d stop  # 关闭
```
## 添加防火墙规则

刚才新建的 VM 实例需要添加一条防火墙规则，把 ss server 的端口开放。在 '网络-防火墙规则'页面，创建防火墙规则，规则参考下图：

![ss 防火墙规则](/assets/img/blog/ScreenShot20170513184917.png)

## 静态IP

VM 实例的 IP 地址推荐设置成静态 IP，这样每次实例重启后 ss 客户端的配置不需要随着更改。

## 开机自启动

先创建一个 ss server 的系统服务。新建文件 `/etc/systemd/system/shadowsocks-server.service`，内容参考下面的 gist，ss 的配置文件路径根据自己的情况修改：

<script src="https://gist.github.com/guyskk/a9665bc6b2a89b73fae34678b1f6dc6b.js"></script>

最后，

```shell
# 启动 shadowsocks server
sudo systemctl start shadowsocks-server

# 开机自动启动
systemctl enable shadowsocks-server
```



