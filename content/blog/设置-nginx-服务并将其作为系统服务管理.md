---
title: 设置 Nginx 服务并将其作为系统服务管理
date: 2024-12-08T17:01:17.517Z
---

您提到的命令用于设置 Nginx 服务并将其作为系统服务管理。如果您是通过源码安装的 Nginx，可以使用这些步骤。但如果您是通过 Docker 安装 Nginx，这些步骤大部分不适用，因为 Docker 容器会独立运行服务，不需要使用 `systemd` 管理。以下是两种情况的操作说明：

---

### **如果是源码安装 Nginx：**

1. **放行端口 80**  
   运行以下命令：
   ```bash
   firewall-cmd --zone=public --add-port=80/tcp --permanent
   firewall-cmd --reload
   ```

2. **创建服务脚本**  
   编辑服务脚本文件：
   ```bash
   vi /usr/lib/systemd/system/nginx.service
   ```

   将以下内容复制粘贴到文件中：
   ```text
   [Unit]
   Description=nginx - web server
   After=network.target remote-fs.target nss-lookup.target

   [Service]
   Type=forking
   PIDFile=/usr/local/nginx/logs/nginx.pid
   ExecStartPre=/usr/local/nginx/sbin/nginx -t -c /usr/local/nginx/conf/nginx.conf
   ExecStart=/usr/local/nginx/sbin/nginx -c /usr/local/nginx/conf/nginx.conf
   ExecReload=/usr/local/nginx/sbin/nginx -s reload
   ExecStop=/usr/local/nginx/sbin/nginx -s stop
   ExecQuit=/usr/local/nginx/sbin/nginx -s quit
   PrivateTmp=true

   [Install]
   WantedBy=multi-user.target
   ```

3. **重新加载服务配置**  
   ```bash
   systemctl daemon-reload
   ```

4. **启动 Nginx 服务**  
   ```bash
   systemctl start nginx.service
   ```

5. **设置开机启动**  
   ```bash
   systemctl enable nginx.service
   ```

---

### **如果是 Docker 安装 Nginx：**

Docker 运行的 Nginx 不需要创建 `nginx.service` 脚本，因为 Docker 已经管理了容器的生命周期。

1. **运行 Nginx 容器**  
   使用以下命令启动并暴露端口：
   ```bash
   docker run -d -p 80:80 --name nginx nginx
   ```

2. **确保服务器的 80 端口已放行**  
   使用防火墙命令：
   ```bash
   firewall-cmd --zone=public --add-port=80/tcp --permanent
   firewall-cmd --reload
   ```

3. **验证 Nginx 是否运行**  
   使用以下命令查看容器状态：
   ```bash
   docker ps
   ```

4. **设置 Nginx 容器开机启动**  
   确保容器在服务器重启时自动启动：
   ```bash
   docker update --restart=always nginx
   ```

---

如果您不确定应该使用哪种方式，请告诉我您的具体安装方法，我可以提供更有针对性的帮助！