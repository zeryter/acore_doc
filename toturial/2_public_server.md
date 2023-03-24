# 开外网步骤

## 服务端

### 1 连接 MySQL
使用任意 MySQL 客户端连接到 MySQL 服务器，例如 HeidiSQL。
连接信息如下：
* IP: 127.0.0.1
* 端口: 63306
* 用户: root
* 密码: password

### 2 修改 realmlist 表里的服务器IP
1. 打开 `acore_auth` 数据库
2. 找到 `realmlist` 表，修改 `address` 字段的值为外网IP（如果是局域网联机，使用局域网IP也是可以的）

IP 地址根据需要可以填以下值：
* LAN IP (192.168.x.x) - 如果您在运行 WoW 的不同计算机上安装 AzerothCore，但所有涉及的计算机都在同一网络（路由器）上，请使用该计算机的局域网 IP。
* 127.0.0.1 - 也称为“本地主机”。 如果您在运行 WoW 的同一台计算机上安装了 AzerothCore，并且只有您连接到它，请在此处和您的配置中保留此设置。
* 公网IP - 需要租用服务器，或者使用云服务器（例如：阿里云、腾讯云、AWS、GCP等）
* 域名 - 填域名的好处是，如果服务器IP地址变了，只需要修改域名的解析记录即可，而不用改客户端。如果使用域名，需要在 `realmlist` 表里填写域名，而不是IP地址。


### 3 开放端口
服务器需要开放以下端口
* 认证服务器：3724
* 游戏服务器：8085

官方文档：https://www.azerothcore.org/wiki/networking

## 客户端
修改 `Data/zh-TW/realmlist.wtf` 文件，把IP改为外网IP。