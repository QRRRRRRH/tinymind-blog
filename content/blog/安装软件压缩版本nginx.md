---
title: 安装软件压缩版本nginx
date: 2024-12-09T11:02:47.861Z
---

https://developer.aliyun.com/article/1395437

![image.png](https://github.com/QRRRRRRH/tinymind-blog/blob/main/assets/images/2024-12-08/1733691194136.png?raw=true)
pwd 到目录root里面

安装 Nginx
安装依赖项
在开始安装Nginx之前，首先需要安装一些依赖项，以确保Nginx编译和运行正常。打开终端并执行以下命令：
yum install -y wget gcc-c++ pcre-devel zlib-devel openssl-devel
这将安装必要的工具和库，以支持Nginx的编译和运行。
下载Nginx
从Nginx官网下载最新的稳定版本。您可以在https://nginx.org/en/download.html上找到最新版本的下载链接。
# 例如，下载Nginx 1.24.0版本
wget https://nginx.org/download/nginx-1.24.0.tar.gz
解压Nginx
解压下载的Nginx源代码包：
tar -zxvf nginx-1.24.0.tar.gz
编译和安装
进入解压后的Nginx目录并进行编译和安装：
# 切换到 Nginx 解压目录
cd nginx-1.24.0
# 编译前的配置和依赖检查
./configure
# 编译安装
make && make install
Nginx安装完成后，默认自动创建 /usr/local/nginx 目录，并创建必要的文件和目录，包括配置文件、日志文件、HTML文件等。
防火墙设置
如果您的系统启用了防火墙，需要关闭防火墙
# 查看防火墙状态
systemctl status firewalld
# 关闭防火墙
systemctl stop firewalld
# 开机禁用防火墙
systemctl disable firewalld
启动Nginx
进入Nginx的安装目录：
cd /usr/local/nginx/sbin
然后，启动Nginx服务器：
./nginx
您现在可以通过浏览器访问您的服务器的IP地址或域名来验证Nginx是否正常工作。
配置 Nginx 为系统服务
将 Nginx 制作成系统服务让你无需手动到 Nginx 安装目录下执行命令来启动它，而是系统会在开机时自动启动 Nginx，让启动过程更加方便和自动化。
配置 Nginx 服务文件
在 /etc/systemd/system/ 目录下创建一个新的服务文件，例如 nginx.service：
vi /etc/systemd/system/nginx.service
在打开的文件中，添加以下内容：
[Unit]
Description=Nginx HTTP Server
After=network.target
[Service]
Type=forking
ExecStart=/usr/local/nginx/sbin/nginx
ExecReload=/usr/local/nginx/sbin/nginx -s reload
ExecStop=/usr/local/nginx/sbin/nginx -s stop
PrivateTmp=true
[Install]
WantedBy=multi-user.target
执行以下命令重新加载 systemd 配置文件：
systemctl daemon-reload
启动 Nginx 服务
执行以下命令启动 Nginx 服务：
systemctl start nginx
现在，Nginx 将作为系统服务在后台运行。
设置开机自启动
如果你希望 Nginx 在系统启动时自动启动，可以执行以下命令设置开机自启动：
systemctl enable nginx
这样，Nginx 将在系统启动时自动启动。
检查 Nginx 状态
systemctl status nginx
停止 Nginx 服务
systemctl stop nginx
重启 Nginx 服务
systemctl restart nginx
卸载 Nginx
如果需要卸载Nginx，您可以执行以下步骤：
停止 Nginx 服务：
执行以下命令停止 Nginx 服务：
systemctl stop nginx
如果你使用的是非系统服务方式启动Nginx，可以使用以下命令停止Nginx：
/usr/local/nginx/sbin/nginx -s stop
确定Nginx的安装位置：
执行以下命令查找Nginx的安装位置：
whereis nginx
该命令将返回Nginx可执行文件的路径，例如 /usr/local/nginx。
删除Nginx安装目录：
执行以下命令删除Nginx的安装目录：
rm -rf /usr/local/nginx
查找并删除相关文件：
执行以下命令查找可能与Nginx相关的文件：
find / -name nginx
这将搜索文件系统中所有包含 “nginx” 的文件名，并且你可以根据需要删除这些文件。
完成以上步骤后，Nginx将被完全卸载。
结语
Nginx是一个强大而多才多艺的Web服务器，它不仅提供卓越的性能，还具备灵活的配置选项。通过本文的指南，您已经成功地掌握了Nginx的基本安装和配置，并且了解了如何将其设置为系统服务。这将为您的Web应用程序提供稳定性和高性能，同时为您提供了丰富的自定义选项，以满足各种需求。希望这份指南对您在Nginx的世界中踏上成功的旅程提供了帮助。看解压包中的安装说明，或者考虑从源代码进行编译。
